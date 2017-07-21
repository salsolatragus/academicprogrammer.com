---
title: About Assumptions
categories:
  - Meta

---

Some weeks ago, I attended [a talk about IntelliJ IDEA][ideatalk]. It was an interactive talk, to the most part, where attendees would ask questions about the IDE and then the speaker, [Yann Cébron](https://twitter.com/yanncebron), would share the thoughts of IDEA developers and himself on the matter. At the same time, he would live demo what he was talking about. I like this format a lot, as a way to get to know new tools or to get to know tools better. 

At some point during the talk we discussed IDEA's "semantic" expansion of the editor selection. An awesome feature I wouldn't wanna live without. Here, Yann stopped and proclaimed that we would now venture behind the scenes, to get an exclusive insight on how IDEA works it's magic. That caught my attention. We were to be initiated into the arcane arts!

Then Yann told us that the selection is based on a mysterious thing called *the AST*...[^magic]

"Well... thanks Captain Obvious," I thought. "Why bother to stop and make a fuzz around such an obvious thing?!"

Truly, why?

I paused.

The most likely explanation was that, in Yann's experience, this was *not* as obvious to everybody in the room as it appeared to me.

Why was it obvious to me, anyway?

I realized that, since my Computer Science 101 courses, I've been taught about how parsers, interpreters, and compilers work. You just can't get through this without abstract syntax trees (ASTs), which is why they became a fundamental part of my understanding of programming languages and of how I think about code. Thinking about it, I have to admit that, though I believe that it's beneficial for programmers to know about underlying concepts of programming languages, objectively, there's probably no need to know about ASTs in order to program...

I had assumed that everybody else's view on things was the same as mine. We all do this frequently, because it is by the assumption of shared knowledge that we are able to communicate. When I talk to another developer, I assume she knows what code and syntax are, what a compiler does (from a user's perspective), and what an IDE is. After all, where would we end if we had to clarify all these terms before each and every conversation?

When I judged Yann's explanation of IDEA's "semantic" expansion of the editor selection, I did this based on my perspective and assumed that everybody else looked at it the same way. Under this assumption, the explanation seemed trivial and boring. Does this assumption hold? I don't know. And since I don't know, it's probably safer to assume it doesn't hold and verify it, instead of passing judgement as if it would hold.

Implicit assumptions may cause much confusion and miscommunication. Conversely, sometimes, it's making them explicit what helps others the most when we try to explain something, be it in a talk, a lecture, a discussion, or in a scientific publication. For example, by asking our audience whether they are familiar with ASTs or by referring to supplementary material for those who may not be to read up on. 

And also, for our own sake, it is important to, every now and then, consciously reflect on our assumptions and decide, for each single one, whether we can actually take them for granted. For example, understanding that ASTs are not necessarily common knowledge made me realize that things building on ASTs, such as the automated refactorings offered by modern IDEs (and how and why they sometimes fails) are probably not obvious either and, therefore, may be interesting topics for lectures, talks, or blog posts. 

Challenge your assumptions.

Thank you, Yann, for this great event and for opening my eyes.

  [ideatalk]: http://www.jug-da.de/2017/05/IntelliJ-Tricks/
  [^magic]: I'm exaggerating a little, for the sake of dramaturgy and delivering my message ;)
