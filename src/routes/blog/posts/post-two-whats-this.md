---
title: WTF Is This?
date: 2019-10-13T12:51:00.000Z
---

The What, Why, and When of the 'this' keyword in JavaScript

<!-- more -->

![Jack from Nightmare Before Christmas Exasperated By 'This'](https://res.cloudinary.com/dscjol9s7/image/upload/v1578264420/hqdefault_qlv5co.jpg)

In honor of the Halloween / Christmas cross-over juggernaut, exploring WTF the this keyword is in Javascript

## why this is a thing?

Before we look at specific examples of the "this" keyword in action, perhaps the better question to ask is "why this?"

If this concept can make even seasoned javascript developers pause then what value are we gaining by having a this keyword at all?

Javascript is a functionally scoped. Meaning that each function has it's own scope or execution context. Variables defined inside a function do not exist outside of their execution context.

## Functional Scope

```javascript
function allWords() {
  const word = "anthropology";

  function getWords() {
    const arr = ["amber", "arson", "ache"];
    return arr;
  }

  try {
    //arr is not in scope
    console.log(arr);
  } catch (e) {
    console.log("this is an error my dude. arr doesnt exist out here");
  }
  const words = getWords();

  return words.push(word);
}

allWords();

// console logs  an error message
// returns ["amber", "arson", "ache", "anthropology"]
```

## First Use Case of 'this': Implicit Binding

Implicit Binding is the most intuitive example and will usually be what "this" is referencing.

In the code below we...

```javascript
//Implicit binding
let doggo_A, doggo_B;

doggo_A = {
  name: "Bones",
  age: 2,
  color: "white",

  favQuote:
    "i may have gotten bigger. but my desire to be held. has remained constant",
  barkQuote: function() {
    console.log(this.favQuote);
  }
};

doggo_B = {
  name: "Red",
  age: 3,
  color: "Red",

  favQuote:
    "sometimes. i will go outside. only to realize. it is inside that i desired all along",
  barkQuote: function() {
    console.log(this.favQuote);
  }
};

doggo_B.barkQuote();
/* output --> "sometimes. i will go outside. only to 
    realize. it is inside that i desired all along " */

doggo_A.barkQuote();
/* output --> "i may have gotten bigger. but my desire 
    to be held. has remained constant" */

function getDoggoQuote(doggo) {
  doggo.barkQuote();
}
//Below each getDoggoQuote() will return different values when passed different objects

getDoggoQuote(doggo_A);
/* output --> "i may have gotten bigger. but my desire 
    to be held. has remained constant" */

getDoggoQuote(doggo_B);
/* output --> "i may have gotten bigger. but my desire 
    to be held. has remained constant" */
```

Let's take this a step further. What if we wanted to indicate that these dogs are siblings? Me might add a sibling property. And because our properties
are implicitly bound to the appropriate execution context
we will be able to access the expected value when we invoke the barkQuote
function from the sibling property.

```javascript
doggo_B.sibling = doggo_A;

doggo_A.sibling = doggo_B;

doggo_B.sibling.barkQuote();

/* output --> the value of from the sibling object 
        "i may have gotten bigger. but my desire 
         to be held. has remained constant"
    */
```

Because this is the most common use of "this", it is often suggested that if you are ever unsure of what a "this" is doing when trying to grok a repo, the first place you should look is what is immediately left of the "." before "this." In the example above it is the sibling property, so when we see doggo_B.sibling.barkQuote we can know that this === doggo_B.sibling or doggo_A.

## Second Use Case of 'this': Explicit Binding

Explicit binding is used with the javascript methods .call() .bind()

The .call() method allows you to take a function which references it's 'this' object in its definition and set what the this is referring to when the function is invoked.

```javascript
/* Explicit binding to set the execution context with .call() */
const barkName = function() {
  console.log(this.name);
};

barkName.call(doggo_A);
```

.apply() is similar to .call() except that it takes an array of values.

```javascript
// The .apply() method allows us to pass in an array
const barkNames = function(dogA, dogB) {
  console.log(
    "my name is ",
    this.name + " and these are my dogs " + dogA,
    dogB
  );
};
const dogs = ["red", "bones"];

barkNames.apply("adam", dogs);
//output ---> my name is adam and these are my dogs red and bones
```

.bind() is acts the same way as .call() except that it does not execute the function immediately but returns a new function within the execution context.
This can be particularly useful when we want to reuse a function later within a known context.

```javascript
//The .bind() method returns a new function with the this bound to the function
const barkName = function() {
  console.log(this.name);
};

const RedBarks = barkName.bind(doggo_A);
```

## Third Use Case of 'this': With the 'new' keyword

The 'new' keyword allows us to create an instance of a user-defined object. This will allow us to write objects with properties that can be defined when an instance our objects are invoked.

Take the following example where we make a new template of a Doggo object

```javascript
//The this keyword in a constructor function
function Doggo(name, age, color, quote) {
  this.name = name;
  this.age = age;
  this.color = color;
  this.quote = quote;
}
const Sparky = new Doggo("Sparky", "spotted", "i just bark");
console.log(Sparky.quote);
//output --> 'i just bark'
```

## Fourth Use Case of 'this': The Window Binding

As we covered earlier, javascript is functionally scoped and at the outer level of this scope is the Global Execution Context.

You can use the Window object and reference the window in the global execution scope.

```javascript
// Global Execution Context
const PetTurtle = {
    name: "squares",
    age: 22
}

function GetTurtlesAge{
    console.log(this.age)
}

getTurtlesAge()
// age is undefined

window.TurtlesAge = 13;
console.log(this.turtlesAge)
// --> 13
```

It generally considered bad practice to populate the Window object with variables and will result in an error if using Strict Mode.
