---
layout: post
title:  "[Algorithm] Hash Table"
author: "Yena Park"
---

Determine if two words are anagrams of each other.
Write a function to check whether two given strings are anagram of each other or not. An anagram of a string is another string that contains same characters, only the order of characters can be different. For example, “abcd” and “dabc” are anagram of each other. So the result will be returned true.
```javascript
const anagram = (a, b) => {
  a_ht = convertToHT(a);
  b_ht = convertToHT(b);
  return compareObjs(a_ht, b_ht);
}

const convertToHT = (word) => {
  const ht = {};

  for (let char of word) {
    if (ht[char]) {
      ht[char] += 1
    } else {
      ht[char] = 1
    }
  }
  return ht;
}

const compareObjs = (a_ht, b_ht) => {
  if (Object.keys(a_ht).length !== Object.keys(b_ht).length) {
    return false;
  }

  // Loop through one hash table or object, check if the key is in the 
  // other hash table, and the value is equal 
  for (let key in a_ht) {
    console.log(key);
    if (a_ht[key] !== b_ht[key]) {
      return false;
    }
  }
  return true;
}

console.log(anagram('abcbcgfd', 'abbccdfg')) //return 'true'
```
