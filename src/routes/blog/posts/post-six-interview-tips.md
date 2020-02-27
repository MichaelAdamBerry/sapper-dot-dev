---
title: Front End Interview Tips
date: 2020-02-26T10:26:00.996Z
---

Essential Knowledge 

<!-- more -->

If you have experience interviewing for Front End Engineering roles, then chances are you also have experience fielding questions best answered by Back End Engineering candidates. 

Much has been written recently over the growing divide in the Front End Engineering field. Chris Coyier explores in [this article on CSS tricks](https://css-tricks.com/the-great-divide/)

> "Two "front-end web developers" can be standing right next to each other and have little, if any, skill sets in common. That's downright bizarre to me for a job title so specific and ubiquitous. I'm sure that's already the case with a job title like designer, but front-end web developer is a niche within a niche already." - [The Great Divide](https://css-tricks.com/the-great-divide/) | [Chris Coyier](https://twitter.com/chriscoyier)

So what does this divide mean for Front End candidates? In short, it means we need to be prepared to get a wide variety of questions (read  literally anything). A recent interview I had for a Front End Interview included questions about CSS selector hierarchy which was followed by SQL queries  that join two tables of data. Ya know, all your classic Front End stuff...

While the above example is extreme, it demonstrates the rising expectation that Front End Engineers have a working knowledge across the stack. And with the rise of low-code and no-code platforms, it's probably a good idea invest some time learning how things work under the hood anyways. 

A great resource to help you round out your backend knowledge is [Full Stack for Font End Engineers](https://frontendmasters.com/courses/fullstack-v2/) a  Front End Masters workshop taught by [Jem Young](https://www.notion.so/adamsdevstuff/8-Essential-Interview-Questions-for-Front-End-Engineers-5d8e552abd7246aa94977917168562fd), Software Engineer at Netflix . Or if you prefer a more academic vibe and already know a little Python, Harvard offers a free course on EDX called [Web Applications with Python and Javascript](https://www.edx.org/course/cs50s-web-programming-with-python-and-javascript). You'll gain experience building full stack  applications with Flask, Django and Postgresql while incorporating your JavaScript and CSS skills into projects as well.

Despite the range of questions you may encounter, a strong understanding of JavaScript and the DOM are essential and will almost certainly be a feature of a phone screening or first interview. Below are a few examples of the kinds of knowledge you need to have  before heading into an interview.  *[Source: Interviewing for Front End Engineers on Front End Masters](https://www.notion.so/adamsdevstuff/8-Essential-Interview-Questions-for-Front-End-Engineers-5d8e552abd7246aa94977917168562fd)*

### JavaScript Questions

- **What's the difference between let, var, and const?**

    *Answer* : Once const variables are declared to point to a certain value, they cannot be re-assigned to point to a different value. If the value is an array or an object, the value can is technically still mutable as you can still add items and properties to the initial value. Pointers of let variables can be re-assigned to point to new values but they are always scoped to closure it is defined within. Variables declared with var are hoisted, and let and const are not; meaning if you were try to access the value var x before it has been defined, the value would be undefined, and would throw a reference error with a const or let.  

- **Describe prototypal inheritance?**

    *Answer* Other than the immutable primitive types (string, number, boolean, null, undefined), everything in JavaScript is an object (classes, functions, arrays). Prototypal Inheritance means that everything has a baseline object prototype. When new objects are defined as being an instance or extending from other objects, this means they inherit their parent and ancestor properties by default, unless explicitly overridden.

- **Explain what "this" is in JavaScript**

    *Answer*: The this keyword is a way to reference everything that is accessible in the current scope that is not locally defined. A more in depth answer will speak to the different use cases which include: implicit binding, explicit binding, constructor functions, and window bindings. Check [my previous post](https://adamberrydotdev.now.sh/blog/post-two-whats-this) for more in depth info and examples.

- **Explain the .apply() and .call() methods**

    *Answer:*  Essentially call and apply are both ways to **change the scope** of a function. The call method takes a series of arguments and the apply method takes an array of arguments.

### Browsers, Events, The DOM

- **What data structure is the DOM**

    *Answer:* A Tree!

- **What is stack, and what is a queue?**

    A*nswer:* Stacks and Queues are two types of data structures with different protocols on how data enters and exits. Stacks. like a stack of books on a table, operate by **LIFO** which stands for **last in last out**. Queues operate by **FIFO** which, as you probably guessed, stands for **first in first out.** Bonus points for mentioning to the execution loop as functions are pushed to the call stack and the event queue which fires events when the call stack is empty.

- **What is event delegation?**

    *Answer:* Event listeners can be expensive when it comes to performance, so it's better to set one event listener on a parent element and take advantage of the fact that **events bubble up the DOM** tree from child to parent.

- **What is a worker and why are they used?**

    *Answer:* A worker is something you use in a browser to offload computationally expensive work so that the UI can continue load while the worker takes care of the longer/harder work. Javascript is **single threaded** so we need to use workers.

These really just scratch the surface at what you may encounter, but I think they are representative of the *kinds*  of knowledge and depth of understanding you will be expected to know. 

[This is a comprehensive repository](https://github.com/h5bp/Front-end-Developer-Interview-Questions) of interview questions that's well organized by topic. Spend some time everyday on a new topic and keep track of your progress. I recommend using a flash card system like [Anki](https://apps.ankiweb.net/)  to help learn these concepts efficiently.  

With the right mindset, interviewing can be a rewarding experience and an opportunity to identify and correct gaps in knowledge. Just remember: **no one was born knowing any of this stuff.** Work hard. Keep your head up. You're gonna do great.
