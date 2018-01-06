---
title: Docker for Cross-platform Research Prototypes
categories:
  - Reproducibility
  - Docker

---

Something I like about my job in academia, is the freedom with respect to what I work with. When I first started, I chose and configured my own laptop. When I develop a [research prototype][prototypes], I use whatever programming languages, libraries, frameworks, or IDE I deem appropriate. This opens up a gigantic playground.

As a result, already in my current 4-person office, we have machines running OSX, Windows, and Debian and write our prototypes in at least seven different programming languages (Java, Scala, Python, PHP, Bash, Batch, and C#). This heterogeneity poses a serious challenge to collaboration, e.g., when additional people join projects. Take the following example:

When I started developing [MUBench][mubench], a benchmarking platform, I quickly found myself with a quite complex setup. For example, in MUBench you run a benchmark experiment with something like the following command:

    $> ./mubench.py run ex1 DemoDetector

This starts a Python application that retrieves the source code of benchmarking Java projects, which requires git and Subversion, and compiles them, which requires Apache Ant, Apache Maven, Gradle, and an Oracle JDK 8. Then it invokes the `DemoDetector`, a Java program, on these benchmarking projects and sends the results to a PHP web application for display, which requires a server and a database. And this is only the tip of the iceberg.

It soon showed that it was a hassle for even my closest collaborators to set up MUBench on their respective machines. In fact, it was already challenging for me to maintain a list of all the dependencies and determine a range of compatible versions for each of them. It became clear that, if I wanted others to use my platform, I desperately needed a more user-friendly setup.

It was around this time that [Ben][benhermann] started a discussion about how [Docker][docker] might help us to more easily produce paper artifacts. I quickly realized that Docker also presented a solution to the portability problem I was facing.

## Docker in a Nutshell

Think of using Docker as of using very resource-efficient virtual machines. In the Docker universe, such a VM is called a *container*. Docker is available for OSX, Windows, and Linux. It makes use of the respective OSs native virtualization capabilities, to be as efficient as possible. In my experience, containers start up in at most a few seconds and do not incur a significant runtime or memory penalty.

The environment of a Docker container is defined by an *image*. To run a command (e.g., an application) in a specific environment, we instantiate a container from a respective image. The container essentially consists of a reference to the image and a writeable [layer][docker-layers] on top of it that captures the effect of the command we run. You may think of a layer like a change set in a version-control system. This has two important effects:

1. The container is very lightweight in terms of disk space, because it contains only the difference to the image and not the entire environment.
2. The image underlying the container remains unchanged by what happens inside the container, which makes it simple and efficient to instantiate further containers with the exact same environment.

In fact, Docker images are themselves composed from one or multiple layers. Each layer of an image captures the effect of a command applied to the state described by the layers below it. This allows Docker to efficiently reuse (parts of) images and to derive arbitrarily many complex images from the same base image, similar to branching in git version control.

A major difference between Docker containers and virtual machines is that containers are intended to serve for the execution of a single (though arbitrarily complex) command. Once the command terminates, so does the container. To execute another command, we instantiate a fresh container, to avoid stacking layers upon layers upon layers. Basically, this means that containers provide stateless environments. If you need to share state between multiple Docker containers, you may mount [volumes][docker-volumes] into them and read/write data from/to them.

## A Cross-platform, Ready-to-use Environment

Primarily, I wanted Docker to provide a platform-independent, ready-to-use runtime environment for running MUBench experiments. To achieve this, I created a Docker image that satisfies all the requirements of MUBench. This allows me to create containers from this image, mount the base directory of the MUBench project from my host filesystem into them, and run the same experiment commands as before, only within the container environment. The example command from above now looks like this:

    $> docker run --rm \
        --mount source=/mubench/checkout/,target=/mubench \
        svamann/mubench \
        ./mubench.py run ex1 DemoDetector

It tells Docker to run the MUBench Python application in a fresh container created from the docker image `svamann/mubench` with the mentioned mount and to delete this container immediately after termination (`--rm`). With a simple shell script (and a respective batch script for Windows) to handle the creation of the container, I reduced this somewhat lengthy command to again look almost the same as originally:

    $> ./mubench.sh run ex1 DemoDetector

As you can see, the use of Docker is almost completely transparent to users of MUBench. I published my Docker image on [DockerHub][dockerhub], such that Docker automatically downloads it on first use. Hence, the previously difficult setup of MUBench---regardless of the user's OS---now consists of only a single step: installing Docker.

In addition to the obvious benefit for other users of the benchmark, introducing Docker also had immediate benefits for myself. For example, I can update my host system without fear of breaking anything that MUBench depends on and I need not bother to maintain a list of MUBench's requirements. Also, when I had to move my experiment environment to another machine, literally all I needed to do was install Docker on the new machine and copy over the data from previous experiments. Within half an hour, I was back up and running.

## A CI Environment

Apart from a platform-independent environment for the use and development of MUBench, introducing Docker to the project had another benefit, which I did not anticipate.

I had long since used [Shippable][shippable] for the CI of MUBench. But since Shippable (and all other current CI service) provides no CI environment with Java, Python, and PHP preinstalled, I had problems with my multi-language project. My quick-fix solution was to use a Python environment and to install the other prerequisites of MUBench in the preparation step of *every build*. A quite inefficient thing to do.

While I had wondered about the lack of multi-language CI environments, things became clear when I realized that Shippable (and many other CI services) build on Docker. There is simply no need to provide more complex environments out-of-the-box, since you can [use any Docker image from DockerHub as your environment][shippable-custom-image]. Hence, I derived my own CI image from my environment image (by additionally installing some test dependencies) and configured Shippable to use it for MUBench. E viola. My project-tailored, ready-to-use multi-language CI environment was born.

  [benhermann]: http://www.thewhitespace.de/
  [docker]: http://docker.com
  [dockerhub]: https://hub.docker.com/
  [docker-layers]: https://medium.com/@jessgreb01/digging-into-docker-layers-c22f948ed612
  [docker-volumes]: https://docs.docker.com/engine/admin/volumes/volumes/
  [mubench]: https://github.com/stg-tud/MUBench
  [prototypes]: {{ site.baseurl }}{% post_url 2017-03-10-academics-code-only-prototypes %}
  [shippable]: https://app.shippable.com
  [shippable-custom-image]: http://docs.shippable.com/ci/custom-docker-image/
