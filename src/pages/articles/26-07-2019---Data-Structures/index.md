---
title: Intro to Data Structures 🌳
date: "2019-07-26"
layout: post
draft: false
path: "/posts/Data-Structures/"
category: "Software"
tags:
  - "Software" 
description: "The building blocks for everything we use"
---
This is part 2 of a 3 part introductory series into the Big 0, Data Structures and Algorithms. This article will introduce what data structures are, why you should understand them and to discuss the most common data structures. I'll be introducing the following:

- Arrays
- Linked Lists
- Stacks/Queues
- Hash Tables
- Trees

But before we get into those...

## What is a data structure? 🤔

Wikipedia defines a data structures as:

> a data organization, management, and storage format that enables efficient access and modification.More precisely, a data structure is a collection of data values, the relationships among them, and the functions or operations that can be applied to the data.

I prefer defining a data structure as:

> a way of storing and organising data to most efficiently apply actions on.

...I have a habit of oversimplifying, but hey, take your pick! 🤷‍♀️

## Why are data structures important?

Understanding and implementing data structures at the deepest level is vital. It is the difference between designing an app that delivers returns your search results within a blink of an eye compared to one which takes several minutes to complete. Data structures are the foundations, the building blocks of every piece of software. 

The depth of your data structures knowledge depends on your situation and circumstance e.g. programming in C compared to JavaScript. 

But IMO whether you actually code data structures at the lowest level or not, I would argue that having a good understanding of what data structures are and why they are important is necessary.


## Do I need to know data structures if I'm a Web Developer?

Short answer: yes.

With higher level programming languages, yes a lot of the complexity of data structures has been abstracted away - it is built into the fabric of the languages themselves. But understanding about data structures is still really important. 

In my very short time as a JavaScript developer, I've already realised that I've neglected the importance of data structures. Even though you might not be creating them yourself from scratch, you will still be making use of objects, arrays, linked lists, stacks/queues etc. on a regular basis. Sometimes intentionally, sometimes without realising. Even just understanding how these data structures in JavaScript work and how they behave "under the hood" can be very useful.

## The data structures you should know...

There are many types of data structures you *could* learn about, but these are the ones that I think you *should* know. These are the ones that are most regularly used in all software development, regardless of languages or circumstances:

- Arrays
- Linked Lists
- Stacks/Queues
- Hash Tables
- Heaps
- Trees
- Graphs

*Note: the terms 'data' and 'value' are used interchangeably throughout.*

### Arrays

An array is a collection of items stored at contiguous memory locations. In JS, they are very flexible as they can contain multiple values of different types. Each value is stored in a memory location which has an assigned index. This index can be used to retrieve that value.

For example:

```javascript
var arr = [2, "Tom", 4, true]

console.log(arr[0]); // logs 2
```

A visual representation would be as so:

![Array](./array.png)
<span><center>From [here](https://www.geeksforgeeks.org/array-data-structure/)</center></span>

But I prefer this:

![Drawers](./drawers.jpeg)

<span><center>From [here]()</center></span>

Arrays are fast at accessing a particular value and slow for adding, searching for, or removing values (depending on their location in the array). We'll look into this more further on in the article.

*Note: I find analogies and linking abstract data structures (or computer science theory in general) to real world objects really helpful at remembering things as I'm learning. If you'd like to understand more about how are brains learn best, and what you can do to optimise it, check out this [book](https://www.amazon.co.uk/Mind-Numbers-Science-Flunked-Algebra-ebook/dp/B00G3L19ZU).*

### Linked lists

A linked list is similar to an array in terms of the ability to store different types of data in each place in memory. But it is fundamentally different in terms of how it is designed.

As the name suggests, a linked list is a connected set of what are called nodes which link one value to another. There are two types of linked lists: 

(1) **Singly** linked list

(2) **Doubly** linked list

A singly linked list is one which points a node to the next node, but not the previous one. Whereas a doubly linked list has nodes which point both to its successor and its predecessor. Each has a *head*, *tail* and *length* property using *pointers* to "point" to the next node in the chain (or previous), with the last node in the list pointing to *null*.

I like to think of linked list as so:

**Singly linked list**

![conga](./conga.jpg)

<span><center>From [here](https://dspace.sunyconnect.suny.edu/handle/1951/52105)</center></span>

**Doubly linked list**

![holding hands](./holding-hands.jpg)

<span><center>From [here](https://www.gsq.org.au/home/people-holding-hands-blue-sky-small-version2/)</center></span>
#### Arrays vs. Linked Lists

At this point you may be thinking: 

*Aren't arrays and linked lists basically the same? Why use linked lists > arrays?* 🤔

Whilst they share several similarities, there are some fundamental differences between the two. And these differences are the reason why you would choose one data structure over the other for a particular use case.

I find the best way to understand the differences between arrays and linked lists is to start by comparing their Big 0 run times: 

| Operations| Arrays| Linked Lists|
| :-------: |:-----:| :----------:|
| Access    | 0(1)  |     0(n)    |
| Search    | 0(n)  |     0(n)    |
| Insertion | 0(n)  |     0(1)    |
| Deletion  | 0(n)  |     0(1)    |

The above table shows that arrays are very quick for accessing a value within, but slow at the other functions (depending on input size (i.e. n)). 

Whereas linked lists are very quick for inserting and deleting a value, but slow at accessing and searching for a specific value. 

### Stacks / Queues

Stacks and queues are both linear data structures which follow a particular order of how data can be used.

#### Stacks

For example, a stack is, well, a stack! It is a data structure where each inserted value is added to the existing stack of values. And when you want to return a value, you receive the top value on the stack. A perfect analogy for this is a stack of books.

![Books](./books.jpg)

<span><center>From [here](https://unsplash.com/photos/IOzk8YKDhYg)</center></span>

A stack is what is referred to as a LIFO data structure:

**L**ast **I**n, **F**irst **O**ut

And it has three methods to manipulate the values:

- *push* - add value to stack
- *pop* - remove last value from stack
- *peek* - view last value, but do not remove from stack

#### Queues

Again, the name is a bit of a giveaway! 

A queue is similar to a stack, being a linear data structure; however, it's fundamental difference is how data is added and removed.

A stack is a LIFO data structure. A queue, on the otherhand, is a FIFO data structure:


**F**irst **I**n, **F**irst **O**ut

Think of a queue of people waiting to be served. To the cashier, it doesn't matter how many people are in the queue: they will always serve the next in line (the first person).

![Queue](./queue.jpg)

<span><center>From [here](https://sorrydadenglandisweird.wordpress.com/2009/12/08/post-office-queues/)</span></center>

Same as with a queue, you could have 10 values, 100 values, or 1 million values in the data structure; the first value will always be "served" first. The way that a queue data structure "serves" the first value, or adds a value, is with the two following methods:

- *enqueue* - adds value to queue
- *dequeue* - removes value from queue

### Hash tables

A hash table is a data structure which uses key:value pairs to store data. It uses what is called a hashing function to associate the key (or property name) to the value. 

Hash tables are baked into most programming languages by default. For example, in JavaScript they are an object, in Python a dictionary, and in Java a hash map. Under the hood, they are kind of take the good bits of arrays and linked lists and combine them together. Which makes them very powerful at both searching and inserting data.

![Hash Table](./hash-table.png)

<span><center>From [here](https://en.wikipedia.org/wiki/Hash_table)</center></span>

### Trees

A tree is a hierarchical data consisting of a set of connected nodes. The most common type of tree is called a Binary Search Tree (BST).

A tree starts with a *root* element. From there, the root can have two children. Well, technically it can have one child, but for it to be a BST it must have two. These children are referred to as *nodes* and within each *node* data can be stored. *Nodes* are then connected to other *nodes* through *edges*.

So similar to a tree, you have a root (except this root is upside down!), you have branches (edges), and leaves (nodes). 

![Tree](./tree.jpg)

<span><center>From [here](https://www.thoughtco.com/id-trees-using-leaf-shape-venation-1343511)</center></span>

*Note: technically in a BST a "leaf" is a node with no children nodes - but that ruins my analogy!* 😅

Trees are mainly used for searching. They can search for data extremely fast as, when implemented with a binary search algorithm, they act logarithmically. 

*Note: I'll be explaining logarithmic algorithms in my next post*

## Big 0 of Data Structures

As I've mentioned, certain data structures are very efficient at specific functions and inefficient at others. The table below summarises the average Big 0's of the data structures we have discussed:

| Operations| Arrays| Linked Lists| Stacks/Queues| Hash Tables | Binary Search Tree |
| :-------: |:-----:| :----------:| :-----------:|:------------:| :-------:|
| Access    | 0(1)  |     0(n)    | 0(n)     |  N/A         | 0(log n) |
| Search    | 0(n)  |     0(n)    | 0(n)     |    0(1)       | 0(log n) |
| Insertion | 0(n)  |     0(1)    | 0(1)     |  0(1)        | 0(log n) |
| Deletion  | 0(n)  |     0(1)    | 0(1)      |  0(1)      | 0(log n)
 
## To sum up 👏...

Gaining a deep understanding of data structures is vital for becoming a competent Software Engineer. It will help you design programs from the bottom up with a focus on organisning your data in an effective manner. It will help prepare you for challenging interviews. It will even help develop a mindset for thinking about how you can optimise your code. 

I have written this post as a high-level introduction for some of the most important data structures you should know. I have purposely missed out a lot of details that you should understand e.g. how to create these data structures in the programming language of your choice. 

With keeping this post as an "introduction", I have missed out a few data structures which I would recommend researching e.g. heaps, graphs and more complex trees.