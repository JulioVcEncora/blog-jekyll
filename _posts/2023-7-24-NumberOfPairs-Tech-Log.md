---
layout: post
title: Maximum Number Of String Pairs Tech Log
---
  In this technical log we can find the solution and algorithm to LeetCode problem called Find Maximum Number of String Pairs. This solution uses an algorithm that has a time complexity of O (n * m), which can be greatly improved and is written in Typescript. With the solution provided we can solve all tests given by LeetCode platform.

## Context
  This algorithm is the solution to the following LeetCode problem: <https://leetcode.com/problems/find-maximum-number-of-string-pairs/>

  The given problem states that we are going to receive as a parameter an array of strings of n length. We must find all the corresponding pairs inside this array and return the pair quantity.  As a requirement we must possess the knowledge to traverse an array and a string. 

  This problem states that we can count word[I] as a pair of word[j] if either one of them is completely equal to the other or if they’re equal on their reversed form. This is an extremely important thing to note, since Typescript (JavaScript) already possesses a predefined array function called reverse.

## Solution

  The first thing we must do is get the inner strings inside an array, and what better way to do this than using the classic for loop. By the line of code shown below we can easily access them. 

 `for (word of wordsArr) {}`

  Now we also need a variable that stores the pairs count which will later be our result, and another variable which will work as our HashMap so that we can see if we have already stored one string. 

`pairs = 0;`

`Hashmap = {};`

  The inner logic inside the for loop is that every time we have a matching string, we are going to increment our pairs count, so how can we get this running, we must reverse our current string in the loop and verify if we already have this string on our hashmap. 

`ReversedWord = word.reverse(); `

`If(hashmap[reversedWord] || hashmap[word]) pairs++;`

  In case we don’t have either the current word or the reversed word on our hashmap, we must store our reversed word. 

```
  else { 
  
    hashmap[reversedWord] = 1; 
  
  }
```

  After we have finished running our for loop, we can successfully return our pairs variable with the correct answer. So, our complete algorithm will have the following structure.

```
    function maximumNumberOfStringPairs(words: string[]): number {
      let pairs = 0;
  
      const memo: {[key: string]: number} | {} = {};
  
      for(let word of words) {
          const sortedWord = word.split('').reverse().join('');
          if(memo[sortedWord] || memo[word]) pairs++;
          else {
              memo[sortedWord] = 1;
          }
      }
      return pairs;
    }
```

## Alternative Solutions
  The first solution I came up with was to use the sliding window technique, which can easily traverse the array and the inner strings. This solution consisted of manipulating the initial array and reversing all its inner strings, and therefore making a comparison between the strings inside the original array and the ones on the sorted array using the sliding window technique. Although it was a very good solution; the time complexity wasn’t that good. You can see the original solution in the following piece of code.
```
    function maximumNumberOfStringPairs(words: string[]): number {
      let pairs = 0;
  
      const entries: {[key: string]: number} | {} = {};
  
      const sortedWords = words.map((el) => el.split('').sort().join(''));
  
      for(let word of sortedWords) {
          if(entries[word]) pairs++;
          else {
              entries[word] = 1;
          }
      }
      return pairs;
    }
```
