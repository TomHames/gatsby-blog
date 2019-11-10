---
title: Intro to Algorithms 💻
date: "2019-08-22"
layout: post
draft: false
path: "/posts/algorithms/"
category: "Software"
tags:
  - "Software" 
description: "Searching and sorting algorithms with JavaScript examples"
---

This is the final part of a mini series into Big 0, Data Structures and Algorithms. In this article we will be focussing on the last piece of the puzzle, algorithms. I'll also be providing examples of all algorithms in JavaScript.

## What are algorithms? 🤔

Wikipedia defines an algorithm as:

> a process or set of rules to be followed in calculations or other problem-solving operations, especially by a computer.

This is an algorithm. 👇

``` js
const factorial = (num) => {
    if (num === 0) {
        return 1;
    } else {
        return num * factorial(num-1);
    }
}
```
In layman's terms, it's a set of repeatable, step-by-step instructions to carry out a specified task. In this instance, to calculate a factorial.

## Why are algorithms important? 🤷‍♀️

A "good" or a "bad" algorithm can cause your program to either be insanely fast or to take several minutes to run.

What makes an algorithm "good" or "bad" is its *time complexity*. Basically, how fast or slow it is at performing a given task.

In computing, there are a set of common tasks which cover the majority of all tasks:

1. Inserting
2. Updating
3. Searching
4. Sorting
5. Deleting

In this article, we will be covering common **searching** and **sorting** algorithms.

## Searching algorithms 🕵️‍♂️

Searching algorithms are used to check for and/or retrieve a specified value in a data structure.

There are two types of search algorithms:

1. Linear Search
2. Binary Search

### Linear Search

A linear search is referred to as a sequential search (I like to refer to it a brute force search 💪). It is what you ordinarily think of as a basic way to searching for something.

For example, consider how you would find a name in a list which contains names in random order. 

You would start at the beginning of the list and read down the list one by one until you find the name you were looking for. This *is* linear search.

As you can imagine, for a list of 10 names this is not a problem. For a list of 100 names it becomes slow. For a list of 10000 names, well, you may as well go home. 😔

So if we consider the time complexity of linear search it would be **0(n)**. The time it takes to complete is proportionate to the size of the input *(n)*.

The code for a simple linear search of an array in JavaScript is below. 

``` js
const linearSearch = (arr, value) => {
    for (let i = 0; i < arr.length; i++) {
        if (arr[i] === value) {
            return i;
        }
    }
    return null;
}
```

### Binary Search

Binary search is the saviour to linear search. It makes searching for something extremely fast. However, there is a caveat: the list *must* be sorted.

It works by taking the middle value of a sorted list and working out whether the value is more than or less than the selected value.

For example, consider the list of names are now in sorted order. You have names from A-Y. You are searching for a name beginning with K.

Binary Search works by selecting the middle value (M). Then it asks:

1. Is this the value? 
2. If yes, return it. 
3. If no, is it more than? Or less than?

In this instance K is less than M, so all the values greater than M are disregarded and the process is repeated until the value is found.

The beauty in binary search lies in that each time you run through the algorithm, the input size is halved. This is what makes binary search so efficient. This type of behavior is called logarithmic and is defined in big 0 as **0(log n)**.

The code for using binary search in JavaScript is below.

``` js
const binarySearch = (arr, value) => {
    let start = 0;
    let end = arr.length - 1;
    let middle = Math.floor((start + end) / 2);

    while (arr[middle] !== value && start < end) {
        if (arr[middle] > value) {
            end = middle - 1;
        } else {
            start = middle + 1;    
        }
        middle = Math.floor((start + end) / 2);   
     }
    return arr[middle] === value ? middle : -1;
}
```

## Sorting algorithms 📶

Unlike searching algorithms, there are *many* sorting algorithms, way too many to cover in this article.

So I have kept it brief and focussed on a select few, the most common ones. I have also ranked them in ascending order of worst to best in terms of their time complexities.

### Selection Sort

Selection sort works by repeatedly selecting the smallest element and placing it at the beginning of the array until all elements are sorted.

It involves creating two arrays:

1. A sub-array which is already sorted
2. A sub-array which with remaining elements to be sorted

With each iteration through the algorithm, the smallest element of the unsorted sub-array is selected and moved to the sorted sub-array.

The following pseudo-code explains this method:

``` js
const arr = [10, 5, 12, 8, 2]

// find min element of arr and place at front
// repeat
arr = [2, 10, 5, 12, 8]
arr = [2, 5, 10, 12, 8]
arr = [2, 5, 8, 10, 12]
```

The actual code for selection sort in JavaScript is as below.

``` js
const selectionSort = (arr) => {
    for (let i = 0; i < arr.length; i++) {
        var lowest = i; // stores index of smallest element
        for (let j = i+1; j < arr.length; j++) {
            if (arr[j] < arr[lowest]) {
                lowest = j; // updates index of smallest element
            }
        }
        // swaps smallest element
        var temp = arr[i];
        arr[i] = arr[lowest];
        arr[lowest] = temp;
    }
    return arr;
}
```
Selection sort is a simple way of sorting a given array. However, it comes at a cost in terms of time.

Two nested for loops are required to execute selection sort, and as a result the time complexity is **0(n²)**. This runtime is referred to as quadratic.

### Bubble Sort

Bubble sort is the simplest of the sorting algorithms. It works by comparing adjacent elements and swapping them if they are in the wrong order.

It gets its name from the fact that during the process of sorting the larger elements "bubble" up towards the end of the array.

Let's take the array we used above and demonstrate how we would sort it with bubble sort.

```js
const arr = [10, 5, 12, 8, 2]

// iterate through array
// compare adjacent pairs
// swap if wrong order
// repeat
arr = [5, 10, 8, 2, 12]
arr = [5, 8, 2, 10, 12]
arr = [5, 2, 8, 10, 12]
arr = [2, 5, 8, 10, 12]
```
And below is an example of how bubble sort could be implemented in JavaScript.

```js
const bubbleSort = (arr) => {
  let noSwaps;
  for(let i = arr.length; i > 0; i--){
    noSwaps = true;
    for(let j = 0; j < i - 1; j++){
      if(arr[j] > arr[j+1]){
        let temp = arr[j];
        arr[j] = arr[j+1];
        arr[j+1] = temp;
        noSwaps = false;         
      }
    }
    if(noSwaps) break;
  }
  return arr;
}
```
Again, similar to selection sort, nested loops are required to complete this type of sort. As a result, bubble sort is a quadratic algorithm **0(n²)**.

### Insertion Sort

Insertion is the last of the simple sorting algorithms. It works by comparing a element and inserting it in its correct position in the array. This way the array is built up one element at a time until sorted.

``` js
const arr = [10, 5, 12, 8, 2]

// iterate over array
// select element and place in correct position
arr = [5, 10, 12, 8, 2]
arr = [5, 8, 10, 12, 2]
arr = [2, 5, 8, 10, 12]
```

As you can see, the array has been built up from start to finish. With each iteration you select the element, traverse backwards through the array, compare the element with existing elements, and place in the correct position.

Consider it like how you would sort a deck of cards in your hand. 

![Hand of Cards](./hand-of-cards.jpeg)
<span><center>From [here](https://unsplash.com/photos/GZ9aJw1DMBA)</center></span>

You would sort from left to right by looking through the hand and picking out the cards one by one and placing them in their correct position.

This is represented programmatically in the below code. 

```js
const insertionSort = (arr) => {
    let currentVal;
    for(let i = 1; i < arr.length; i++){
        currentVal = arr[i];
        for(let j = i - 1; j >= 0 && arr[j] > currentVal; j--) {
            arr[j+1] = arr[j]
        }
        arr[j+1] = currentVal;
    }
    return arr;
}

insertionSort([2,1,9,76,4])
```

Again, two nested loops are required for this algorithm. One to loop over the array itself, and the second to loop backwards and compare the current element to the other elements.

Insertion sort works well for lists which are almost sorted. But for larger lists, again, its runtime grows large as its time complexity is **0(n²)**.

Now onto the actual *decent* algorithms...

![GIF](https://media.giphy.com/media/IcGkqdUmYLFGE/giphy.gif)

### Quick Sort

Quick sort is an advanced algorithm compared to the ones we've covered. It is a divide and conquer algorithm.

It works by picking a element as a pivot point. It uses this pivot point to partition the array. If the elements are less than or equal to the pivot, they go to the left. If the elements are greater than the pivot, they go to the right. 

This process is repeated until all elements are separated.

The algorithm then works backwards to return a sorted array. It takes the elements and repeats the instructions in reverse order (kind of 🙃).

All the elements to that were smaller than the pivot go before the pivot. All the elements that were greater than the pivot go after the pivot.

This process is repeated until the array is combined into a single sorted list. Voila! 👏

It's much easier to understand how quick sort works visually, and this video does a fantastic job of understanding how quick sort works.

[![Quick Sort](./quick-sort.jpg)](https://www.youtube.com/watch?v=XE4VP_8Y0BU)

And below is how quick sort could be implemented in JavaScript.

``` js

const pivot = (arr, start = 0, end = arr.length - 1) => {
  const swap = (arr, idx1, idx2) => {
    [arr[idx1], arr[idx2]] = [arr[idx2], arr[idx1]];
  };

  // assumes pivot is first element
  let pivot = arr[start];
  let swapIdx = start;

  for (let i = start + 1; i <= end; i++) {
    if (pivot > arr[i]) {
      swapIdx++;
      swap(arr, swapIdx, i);
    }
  }

  // Swap the pivot from the start the swapPoint
  swap(arr, start, swapIdx);
  return swapIdx;
}


const quickSort = (arr, left = 0, right = arr.length -1) => {
    if(left < right){
        let pivotIndex = pivot(arr, left, right) //3
        //left
        quickSort(arr,left,pivotIndex-1);
        //right
        quickSort(arr,pivotIndex+1,right);
      }
     return arr;
} 
```
A last thing to note is quick sorts runtime. It is a very quick (pun intended 😏) sorting algorithm. It usually runs at **0(n x log n)**. However, in a worst case scenario it could run at **0(n²)**.

The difference is the pivot point. It all depends on what pivot point is selected. If the pivot point is the smallest/largest element in the array, many more iterations through the algorithm take place compared to if the pivot point is a median of all the elements.

In this article I'm not going to go in detail about this. But I would recommend checking out the following [article](https://www.khanacademy.org/computing/computer-science/algorithms/quick-sort/a/analysis-of-quicksort) to provide some deeper understanding of this.

### Merge Sort
Now finally, onto the last algorithm we will cover. I've saved the best til' list, the crème de la crème of sorting algorithms: merge sort. 😚

Like quick sort, merge sort is a divide and conquer algorithm. It works by taking the array and splitting it down into single elements. It then merges the sub-arrays, sub-sub-arrays, sub-sub-sub-arrays... until a single sorted array is returned.

It does this by:

- comparing adjacent pairs of elements
- swap if necessary
- merge sub-array together
- then repeat process by comparing sub-arrays to each other

This is my explanation in pseudo-code:

``` js
// separate list into sub-array until only one element in sub-array
// compare sub-array
// if left element > right element, swap
// if left element <= right element, do not swap
// merge sub-array by placing left element on top of right elements
// repeat from Step 2.
// stop when only one array remains

```
And this is how merge sort could be coded in JavaScript.

``` js
const merge = (arr1, arr2) => {
    let results = [];
    let i = 0;
    let j = 0;
    while(i < arr1.length && j < arr2.length){
        if(arr2[j] > arr1[i]){
            results.push(arr1[i]);
            i++;
        } else {
            results.push(arr2[j])
            j++;
        }
    }
    while(i < arr1.length) {
        results.push(arr1[i])
        i++;
    }
    while(j < arr2.length) {
        results.push(arr2[j])
        j++;
    }
    return results;
}

// recursive merge sort
const mergeSort = (arr) => {
    if(arr.length <= 1) return arr;
    let mid = Math.floor(arr.length/2);
    let left = mergeSort(arr.slice(0,mid));
    let right = mergeSort(arr.slice(mid));
    return merge(left, sright);
}
```
Again, it's difficult to explain an advanced algorithm like this in words and code. It's much easier to understand it visually. 

For this I would recommend VisualGo. It's an interactive tool which you can use to understand algorithms and data structures. I've found it super helpful for understanding more complicated algorithms like quick and merge sort.

[![Sorting Algorithms](./visualgo.png)](https://visualgo.net/bn/sorting)

Finally, what makes merge sort the crème de la crème of sorting algorithms is its efficiency. Regardless of the size of the input, it will always complete sort in **0(n x log n)**.

## To sum up 👏...

And there we have it. A whistle stop tour of algorithms.

I would highly recommend having a go at coding these algorithms yourself or have a play about with the code snippets I've included.

Also, check out Colt Steele's JavaScript Algorithms and Data Structures Masterclass. That is what I primarily used to learn about these algorithms and is the place which provided most of these code snippets.

And finally, have a look into the following resources which I used to help provide me with the content for this article:

[Geek for Geeks](https://www.geeksforgeeks.org/)

[Getting Sorted & Big 0 Notation](https://www.youtube.com/watch?v=kgBjXUE_Nwc)

[Cracking the Coding Interview](http://www.crackingthecodinginterview.com/)
