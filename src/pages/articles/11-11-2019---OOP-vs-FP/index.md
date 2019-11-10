---
title: OOP vs. FP 🥊
date: "2019-11-11"
layout: post
draft: false
path: "/posts/oop-vs-fp/"
category: "Software"
tags:
  - "Software" 
description: "Comparing two popular types of programming"
---

Recently whenever I heard the phrase "multi-paradigm programming language" I would sit there silently, nod and pull a confused face.  

It's not something I had come across whilst teaching myself how to code. I just thought there was one way to program...

But since I've started to expand my learning, I've come to realise that it's important to know why we program in a certain way and why we use a certain type of programming.

Two types of programming paradigms I've been looking into are Object Oriented Programming (OOP) and Functional Programming (FP). They are the most popular and commonly used programming paradigms today. We're going to cover the key aspects of each, and compare them throughout to understand their similarities and differences.

Let's begin with OOP.

## What is OOP?

Wikipedia defines Object Oriented Programming as:

> a programming paradigm based on the concept of "objects", which can contain data, in the form of fields (often known as attributes or properties), and code, in the form of procedures (often known as methods).

## Principles of OOP

To be considered an OO, there are 4 principles the programming language must demonstrate:

1. **Encapsulation**
2. **Abstraction**
3. **Inheritance**
4. **Polymorphism**

![The rules](https://media.giphy.com/media/3o7aTkjnoAzNaxPes8/giphy.gif)
<span><center>From [GIPHY](https://giphy.com/gifs/tiffany-rules-3o7aTkjnoAzNaxPes8)</center></span>

### Encapsulation

Encapsulation is a fundamental principle of OOP. It refers to bundling all the data and methods for a specific object into that object; essentially, making it self-contained. This is often referred to as a class in most OOP languages. The object’s data is encapsulated which prevents other objects from accessing it directly.

### Abstraction

Consider abstraction as an extension of encapsulation. Similar to encapsulation, abstraction “hides” certain details from a user, exposing only the relevant details which are needed.

### Inheritance

Inheritance is the mechanism in which one class acquires the property of another class. Think of it like a physical trait passed from a parent to a child, like a parents's brown eyes passed to their child.

This is a powerful feature of OOP as we can reuse the data and methods of an existing class.

### Polymorphism

Polymorphism...

![WTF](https://media.giphy.com/media/aZ3LDBs1ExsE8/giphy.gif)
<span><center>From [GIPHY](https://giphy.com/gifs/optical-illusions-asap-science-aZ3LDBs1ExsE8/links)</center></span>

Strange word, but it makes sense if you break the word down:

```
Poly = many
Morphism = takes different forms
```

In terms of programming, this is the ability to present the same interface for different forms (or data types). For example, consider a parent class called LogIn with a method in that class called handleClick. With polymorphism, any child classes of the parent class LogIn may use the handleClick method in different ways, like using it to manipulate numbers or using it to concatenate strings.

## What is FP?

Wikipedia defines Functional Programming as:

> a programming paradigm — a style of building the structure and elements of computer programs— that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

Some of the key phases here are **mathematical functions** and avoids **changing state and mutable data**.   

## Principles of FP

The principles of FP aren't as clear cut as those in OOP. But there are certain interconnected traits a language must have if it is be defined as functional:

- Immutability
- No side effects
- No shared state
- Pure functions

## Immutability

Immutability is a key concept of FP. It refers to the inability to change state directly after it is created.

For example, imagine you have created an object with some data in it. With OOP, you can mutate that data - you can change its *state*. However, with FP you cannot directly change the data in that object. That object's data is *immutable*.

## No side effects

In FP side effects are avoided. A side effect is when there are any observable changes to state other than the function's return value.

For example, this function has no side effects as its output is contained to its return value only.

``` js
function add (x, y) {
  return x + y;
}
```
Whereas this function has a side effect as it does more than just return a value. It has an action which something external to itself (in this case logging to the console).

``` js
function log (x, y) {
  console.log(x + y);
}
```
## No shared state

In FP, there are no global variables. Instead, each function only receives its values through parameters.

## Pure functions

The above examples are examples of a pure function and an impure function, respectively.

A pure function is one which:

- same inputs return same outputs
- no side effects

The first example, the function 'add', is a pure function as passing in the same input will always result in the same output.

Even though this is also true for the second function, the function 'log' is an impure function as it causes side effects outside of the scope of that function.

Pure functions are the foundation to FP.

## OOP vs. FP

So now that we have summarised each paradigm and looked at some of their key features, let's compare them.

This isn't a "lets see which one is better", because at the end of the day each paradigm serves its own purpose. And, as you'll see, it is possible that you could use either one to perform the same thing.

For example, consider filtering a list.

In OOP, you could do this:

```js
const list = [1,2,3,4,5,6,7,7,8,9,9,10];
const filteredList = [];

for (let i = 0; i < list.length; i++) {
  if (list[i] > 5)
    filteredList.push(list[i]);
}
```

In FP, you could do this:

```js
const list = [1,2,3,4,5,6,7,7,8,9,9,10];
const filteredList = list.filter(num => num > 5);
```

Both examples produce the same result, but just in different ways.

With OOP, the steps are explicitly defined one by one, in the order they are expected to be called. This is called imperative programming. The word imperative refers to commands. So it's likened to having a set of commands for the computer to run.

With FP, things are done differently. In terms of how you write your code, it's like the opposite of imperative programming. Instead of defining the steps one by one in the order they are computed, you describe the result without saying how you want to explicitly want to achieve it.

In the above example, the ES6 `filter()` method is used to achieve the result of filtering through the list. This is functional programming as the code to do this returns the same output given the same output and produces no side effects (i.e. mutates `list` array). Note: `filter()` produces a new array, in this instance `filteredList`.

## Advantages vs. Disadvantages

One thing I love about programming is that rarely is there a time when there is just one answer to anything - it is a matter of judgement, experience and circumstance. This certainly applies to programming paradigms.

When it comes to OOP and FP, there are pros and cons to both. Some of them include:

OOP
---
✅ Reusable code through inheritance <br />
✅ Easy to maintain through modularity <br />
✅ Flexibility through polymorphism <br />

❌ Slower performance due to relative larger memory space required

FP
---
✅ Reduces bugs <br />
✅ Code more readable <br />
✅ Code more predictable <br />

❌ Steep learning curve <br />
❌ Lack readability <br />

## Why choose one paradigm over another?

Well it depends on what you're trying to solve. 

FP excels in use cases where many operations are performed on fixed data. For example, in an app which you are using deep learning to determine patterns. Or maybe a CLI app which reads some input and produces some output which are consistent in their nature.

OOP on the other hand is more suited to applications that you can interact with like a GUI or API. These kind of apps often rely on mutable state and can grow to be very large and complex which is something OOP can manage well.

## Popular OOP and FP languages

There are a number of OOP and FP languages: 

### OOP:

  - Java
  - C++
  - Ruby
  - Objective-C

### FP:

  - Lisp
  - Haskell
  - Erlang
  - Clojure

And there are several languages which are capable of both and are therefore referred to as multi-paradigm; JavaScript and Python are examples of such.

## To summarise...

Currently OOP is the most popular and well adopted programming paradigm, but it isn't without its flaws. FP shows promise, and there appears to be a growing view that it might be more widely adopted in the future. At the end of the day though, there is never any "perfect" anything, and this certainly applies to programming paradigms. 