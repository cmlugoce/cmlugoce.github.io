---
layout: post
title:      "The Big O Notation...🤔😵"
date:       2019-02-06 12:39:55 -0500
permalink:  the_big_o_notation
---


![](https://images.unsplash.com/photo-1532411644617-ea8077306595?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60)


Preparing for tech interviews is both scary and excited!! While researching for most common interview questions I stumbled with this one *How would you explain the Big O notation ?* I was a bit confused (the emojis in the title explain my reaction haha). After some research and practice I can understand the concept a little better. 

## Big O Notation

Big O notation is the language we use for talking about how long an algorithm takes to run. It's how we compare the efficiency of different approaches to a problem.

With big O notation we express the runtime in terms of how quickly it grows relative to the input, as the input gets arbitrarily large.

To understand it better, we can break it down in the following:

**how quickly the runtime grows**—It's hard to know the exact runtime of an algorithm. It depends on the speed of the processor, what else the computer is running, etc. So instead of talking about the runtime directly, we use big O notation to talk about how quickly the runtime grows.

**relative to the input**—If we were measuring our runtime directly, we could express our speed in seconds and minutes. Since we are measuring how quickly our runtime grows, we need to express our speed in terms of something else. With Big O Notation, we use the size of the input, which we call **n**. So we can say things like the runtime grows “on the order of the size of the input” **(O(n))** or “on the order of the square of the size of the input” **(O(n²))**.

**as the input gets larger** — Our algorithm may have steps that seem expensive when **n** is small but are eclipsed eventually by other steps as n gets larger. For Big O Notation analysis, we care more about what grows fastest as the input grows, because everything else is quickly eclipsed as **n** gets very large.


## Examples

```
function printFirstItem(items) {
  console.log(items[0]);
}
```

This function runs in O(1) time (or "constant time") relative to its input. The input array could be 1 item or 1,000 items, but this function would still just require one "step."
```
  function printAllItems(items) {
  items.forEach(item => {
    console.log(item);
  });
}
```

This function runs in O(n) time (or “linear time”), where n is the number of items in the array. This means that if the array has 10 items, I have to print 10 times. If it has 1,000 items, I have to print 1,000 times.

```
function printAllPossibleOrderedPairs(items) {
  items.forEach(firstItem => {
    items.forEach(secondItem => {
      console.log(firstItem, secondItem);
    });
  });
}
```

In this example I am nesting two loops. If the array has n items, the outer loop runs n times and the inner loop runs n times for each iteration of the outer loop, giving us n²​​ total prints. Thus this function runs in O(n²) time (or “quadratic time”). If the array has 10 items, I have to print 100 times. If it has 1,000 items, I have to print 1,000,000 times.


### N could be the actual input, or the size of the input

```
function sayHiNTimes(n) {
  for (let i = 0; i < n; i++) {
    console.log('hi');
  }
}

function printAllItems(items) {
  items.forEach(item => {
    console.log(item);
  });
}
```


Both of the previous functions have O(n) runtime, even though one takes an integer as its input and the other takes an array. Sometimes n is an actual number that’s an input to the function, and other times n is the number of items in an input array (or an input map, or an input object, etc.). This means that N could be the actual input, or the size of the input.

### Worst Case Scenario:

When it comes to the Big O Notation, we are usually talking about the worst case scenario. At times the worst case runtime is significantly worse than the best case runtime.

```
function contains(haystack, needle) {

  // Does the haystack contain the needle?
  for (let i = 0; i < haystack.length; i++) {
    if (haystack[i] === needle) {
      return true;
    }
  }

  return false;
}


```

In this example, I might have 100 items in the haystack, but the first item might be the needle, in which case I would return in just 1 iteration of the loop. I can say this is O(n) runtime and the worst case scenario would be implied. But to be more specific I could say this is worst case O(n) and best case O(1) runtime.

###  Space Complexity:

Sometimes we want to optimize for using less memory instead of (or in addition to) using less time. Talking about memory cost (or "space complexity") is very similar to talking about time cost. We simply look at the total size (relative to the size of the input) of any new variables we're allocating.

This function takes O(1) space (I am not allocating any new variables):

```
function sayHiNTimes(n) {
  for (let i = 0; i < n; i++) {
    console.log('hi');
  }
}
```

This function takes O(n) space:

```
  function arrayOfHiNTimes(n) {
  const hiArray = [];
  for (let i = 0; i < n; i++) {
    hiArray[i] = 'hi';
  }
  return hiArray;
}
```

Most of the time when we talk about space complexity, we’re talking about additional space, so we don’t include space taken up by the inputs. For example, this function takes constant space even though the input has n items:
```
function getLargestItem(items) {
  let largest = -Number.MAX_VALUE;
  items.forEach(item => {
    if (item > largest) {
      largest = item;
    }
  });
  return largest;
}
```

Overall,  Big O notation helps you to understand efficiency of your code. When  working with huge data sets, you will have a good sense of where major slowdowns are likely to cause trouble, and where do you have to put  more attention to get the largest improvements in your project. 

### Reference

[Big O notation](https://www.interviewcake.com/article/javascript/big-o-notation-time-and-space-complexity?)
