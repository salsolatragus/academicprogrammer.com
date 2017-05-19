---
title: Legacy Code Retreat
categories:
  - Teaching
  - Quality

---

Where does legacy code come from? What is legacy code, anyway? Why should we care about it? Can we make it go away? How? Can we prevent it from coming back, or even from ever showing up in the first place?

Let's start with a fact: Legacy code isn't written. When we write code, we know why we write it and how it works. All is nice and well. Only when this knowledge fades---because our memory is unreliable, developers leave, and nobody cared for sufficient documentation and tests---code may become a legacy.

Legacy code is code that is of importance to us, i.e., it is profitable. If this weren't the case, we could simply throw it away. If we can't, then we rely on the code. And code that we rely on needs to be changed (maintained/extended) every now and then.

Legacy code is code that solves a non-trivial problem. Otherwise, we could figure it out easily or simply throw it away and write it anew. It is also difficult to change, because we don't know how it works and which constraints it satisfies. With every change we risk breaking the code itself or something that depends on it.

This locks us in between the need to change the code and the fear of breaking things through these changes. Being locked in means pressure. Pressure creates fear. 

**Legacy code is profitable code that we are afraid to change.**

It doesn't matter who wrote the legacy code (we all do it!) nor when (only yesterday this was all green-field code!). What matters is that it is there now and that we need to deal with it. We need to clean up the mess and do so in a way that preserves both our sanity and our jobs.

In a typical programmer's day job, there's no time to learn how to do this. We're all behind schedule anyways and the cost of struggling with legacy code is crushing us. We need a way to learn how to do this safely, correctly, and eventually, even quickly.

How about we withdraw from our day job for a day to do some deliberate practice on this matter?

**How about a Legacy Code Retreat?**

The idea of a legacy code retreat is simple: We find us a group of programmers, take a diabolic-but-fun codebase (available in 26 programming languages), and I teach you various design rescue and improvement techniques, as well as a couple of tricks to get the beast under test. The main goal is for you to practice these techniques in a low-stakes environment, before you don them to battle your own personal nightmare.

---

The idea of a Legacy Code Retreat is not new. As far as I know, [Joe Rainsberger coined the term and first derived the concept][jbrains-original] from that of a regular Code Retreat. Others, such as [Adrain Bolboaca][bolboaca] and [myself][myself] have done it since.

  [jbrains-original]: http://www.jbrains.ca/legacy-code-retreat/
  [bolboaca]: http://blog.adrianbolboaca.ro/2014/04/legacy-coderetreat/
  [myself]: http://www.jug-da.de/2015/03/Legacy-Code-Retreat/
