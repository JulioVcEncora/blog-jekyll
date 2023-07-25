---
layout: post
title: LRU Cache Tech Log
---
  This technical log explains the process and solution to design an algorithm that simulates an LRU Cache. The implemented algorithm utilizes a Doubly Linked List data structure, and it has a time complexity of O (1). The following implementation uses this time complexity to pass all tests provided by LeetCode platform. The implementation must be written in Java, Python and Typescript.

## Context
  This algorithm is the solution to the following [LeetCode problem](https://leetcode.com/problems/lru-cache/description/).

  For us to come to a solution, it is a must to understand how the LRU Cache (least recently used) system internally works. We can refer to the following picture, to have a wider overview of how this system works. 
![LRU Cache Structure]({{ site.baseurl }}/images/LRUCacheStructure.png "LRU Cache Structure")
This picture was taken from this [article](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU).

  As we can see from the previous picture, the LRU Cache system possesses a length limit, and when that limit is overflowed, we must delete the least used data. This length limit is going to be referred to as capacity. We must also use two predefined methods, which will be put and get. The put method will take as parameters a key and a value, and lastly, the get method will take as parameter a key, returning the value corresponding to that key. 

## Solution
  The language that I’m most comfortable with is TypeScript, and since JavaScript possesses predefined methods for its data structures, I had to come up with a solution that doesn’t use them since other languages don’t have them. The first constraint to consider is the time complexity, there aren’t many data structures that can run in a O(1) time constraint, so the get method can easily be solved and achieved by accessing the value in an object or HashMap. 

  The trickiest part will be the put method, this method must verify if the key already exists on the Cached keys so that it can update it, otherwise create a new key. 

  Since every time we call both previous methods, we need to consider the accessed values as the most recent values, we will use a doubly linked list data structure so that we can have a head (indicating the most recently used value) and a tail (indicating the least used value). The get and put methods will have the following structures: 

```
  getMethod(key: number) { 

    if(HashMap(key)) {// if key exists in HashMap 

      value = hashMap(key) // get value from HashMap 
  
      Move to head of doubly linked list (key) // indicate that this key is the most recently used value 
  
      return value 

    } 

    return –1; // if key doesn’t exist return –1  

  } 
```

```
  postMethod(key: number, value: number) { 

    if (HashMap(key) {// verify if key exists on the HashMap 

      hashMap(key) = value; // update key value 

    } else { 

      node = new LinkedList(key) // create a new linkedlist node 

      hashMap(key) = {// create a HashMap entry with its value and its node 

      value: value, 

      node: node, 

    } 

    Move to head of doubly linked list (key) // indicate that this key is the most recently used value 

    if (HashMap.length > capacity) {// verify that the HashMap capacity doesn’t exceeds predefined capacity 

      delete LinkedList tail 

    }  

  }
```
  Since explaining the algorithm to traverse a Doubly Linked List is outside of this scope, it will be omitted.

## Alternative Solutions
  The first solution I came up with was to do a LIFO or Stack data structure, so that the last input data will be in the top of the stack, and if the stack length exceeded the predefined capacity, remove the bottom of the stack. I didn’t use this data structure since traversing through arrays can lead to O (n) time complexity therefore conflicting the given constraint of O (1). 
