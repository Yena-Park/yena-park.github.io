---
layout: post
title:  "[Better Code] Longest word in the world"
author: "Yena Park"
---

"Return the length of the longest word in the provided sentence. Your response should be a word."

## Return word 
```javascript
const longestWord = (str) => {
  const words = str.split(' ');
  const findLongestWord = (a, b)=> {

  return a.length > b.length ? a : b;
}

  const result = words.reduce(findLongestWord, "")
  return result;
}

console.log(longestWord('The quick brown fox jumped over the lazy dog.'));
```

"Return the length of the longest word in the provided sentence. Your response should be a number."

## Return number
```javascript
const longestWordLength = (str) => {
  const words = str.split(' ');
  const findMax = (x, y) => {
  
  return Math.max(x, y.length)
}  
  
  const longest = words.reduce(findMax, 0); 
  return longest;
}

console.log(longestWordLength('The quick brown fox jumped over the lazy dog.'));
```
