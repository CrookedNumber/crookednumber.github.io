---
layout: post
title:  The “Early Bail” is an Anti-Pattern
date:   2012-07-24
---

So what _is_ the early bail? It is a way to leverage how return works to shorten a function and -- ostensibly -- improve performance. It look like this:

~~~
function foo() {
  if (!$condition) {
    return;
  }
  // do stuff
}
~~~

We’ve all seen it before. Call it the short-circuit or, as a co-worker calls it, the “shallow depth conditional.” But I’m going to call it what I think it is: an anti-pattern.

Reason #1: It Doesn’t Use the Simplest Evaluation
-------------------------------------------------

The above example is actually shorthand for:
~~~
function foo() {
    if (!$condition) {
    return;
  }
  else {
    // do stuff
  }
}
~~~

And that's just wrong, right? According to Code Complete 2 -- and everyone in the world -- you should use the simplest possible conditional possible. `if not TRUE` makes me think, if only for a second. So we really should do the inverse.

~~~
function foo() {
  if ($condition) {
    // do stuff;
  }
  else {
    return;
  }
}
~~~

And of course that's just longhand for:

~~~
function foo() {
  if ($condition) {
    // do stuff;
  }
}
~~~

Reason #2: You Lose Visual Cues
-------------------------------

Let’s look at the early bail again.
~~~
function foo() {
  if (!$condition) {
    return;
  }
  // do stuff
  // do lots more stuff
  // several lines later
  // ...
  // lots lines later
}
~~~

The first level of indentation tells us that we are inside a function. Since a condition has been met, the `DO STUFF` code should be at a second level of indentation -- but it’s not. There is no visual clue to remind us that `$condition == TRUE`.

But let's take a look at the above code re-written correctly.

~~~
function foo() {
  if ($condition) {
    // do stuff
    // do lots more stuff
    // several lines later
    // ...
    // lots lines later
  }
}
~~~

Even if there are 100's of lines of code within that code block (there probably shouldn’t be), you'll always know immediately that some condition has been met (or you are in a loop).

The case is closed but the comments are open.