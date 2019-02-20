---
layout: post
title:      "Solving the DNA coding challenge💻"
date:       2019-02-20 17:21:58 -0500
permalink:  solving_the_dna_coding_challenge
---


As part of my life now as a job seeker, I spend some time practicing challenges that will help me to improve my problem-solving skills.  I use different sites to practice: Codewars,  Hackerrank, Codility, Leetcode, and freeCodeCamp!  These early morning I decided to do some of the challenges under the JS section of freeCodeCamp!! One of the funnest ones was to solve a DNA coding challenge!

Here is the challenge:

> The DNA strand is missing the pairing element. Take each character, get its pair, and return the results as a 2d array.

> Base pairs are a pair of AT and CG. Match the missing element to the provided character.
> 
> Return the provided character as the first element in each array.
> 
> For example, for the input GCG, return [["G", "C"], ["C","G"],["G", "C"]]
> 
> The character and its pair are paired up in an array, and all the arrays are grouped into one encapsulating array.
> 

After some digging I ended up with this info:

 *G* element  will return  **[”G”, “C”]**

 *C* element  will return  **[“C”, “G”]**

 *A* element  will return  **[“A”, "T"]**  
 
 *T* element will return  **[“T”, “A”]**



The fun part begins now!! I always try to pseudo-code, it helps me to understand the problem and to organized my thoughts!

 Pseudo-code:
   1. Create an empty array to store the pairs!
   2. A switch case would be useful to check for every element and push into the new array
   3. Loop through the elements to pair the strand(using the switch case)!
   
	```
function pairElement(str) {

      let strand = [];

      
      const check = function(char) {
        switch (char) {
          case 'A':
            strand.push(['A', 'T']);
            break;
        
          
          case 'G':
            strand.push(['G', 'C']);
            break;
						
					case 'C':
            strand.push(['C', 'G']);
            break;
						
						case 'T':
            strand.push(['T', 'A']);
            break;
        }
      };

      
      for (let i = 0; i < str.length; i++) {
        check(str[i]);
      }

      return strand;
}
```

Time to test!! ✨✨🎊😎

<iframe height="400px" width="100%" src="https://repl.it/@cmlugoce/DeterminedDelectableCoordinates?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>

Awesome!! It works!! 


