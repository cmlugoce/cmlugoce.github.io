---
layout: post
title:      "Coffee and Code: JS Algorithm Challenges During My Coffee Break ☕💻"
date:       2019-02-27 16:42:01 -0500
permalink:  coffee_and_code_js_algorithm_challenges_during_my_coffee_break
---




Hi everyone! Last week I discussed one of the solutions for the FCC's DNA challenge! This week, I will discuss a very simple algorithm code challenge from FCC, *[Find the longest word on a string](https://learn.freecodecamp.org/javascript-algorithms-and-data-structures/basic-algorithm-scripting/find-the-longest-word-in-a-string/)* . 

**The Challenge**

> Return the length of the longest word in the provided sentence.

>Your response should be a number.

```
function findLongestWord(str) {
  return str.length;
}
findLongestWord("The quick brown fox jumped over the lazy dog");
```

 **Test Case**
 
` findLongestWordLength("The quick brown fox jumped over the lazy dog")` should return a number.

`findLongestWordLength("The quick brown fox jumped over the lazy dog")` should return 6.

**Organize your ideas before coding**

This step is very important(at least for me!)! Read the instructions and the test cases  a few times! It helps you to get the general idea, and then pseudocode!

After reading the challenge and the test cases, I had an idea of what I wanted to do.
  
1. Convert the string into an array and save it in a variable
2. Create a variable that will save the longest word length; initialize it to 0
3. `For loop` to find the longest word!!
4. READY to code and test with repl.it!!

**The Solution**

There are several ways to solve this challenge! But I will provide the one that makes more sense to my brain, and easier to remember!

```
function findLongestWord(str) {
let arr= str.split(' ') // split by space not by character 
 let longest = 0  //save the longest word length in this variable

 for(let i = 0; i < arr.length; i++){  //iterate over the array
 if (arr[i].length > longest){  //if the length of the word(arr[i].length) is longer than the variable, let that be the new length
   longest = arr[i].length;
 }
 }
 return longest   //return the variable otherwise it will return 'undefined'
}
```


That's it!! An easy way to start practicing algorithms and JavaScript ✨🎉😊


