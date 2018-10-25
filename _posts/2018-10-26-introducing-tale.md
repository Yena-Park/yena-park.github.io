---
layout: post
title:  "[Algorithm] Jewels and Stones"
author: "Yena Park"
---

You're given strings J representing the types of stones that are jewels, and S representing the stones you have.  Each character in S is a type of stone you have.  You want to know how many of the stones you have are also jewels.
The letters in J are guaranteed distinct, and all characters in J and S are letters. Letters are case sensitive, so "a" is considered a different type of stone from "A".


### Example 1:
```
Input: J = "aA", S = "aAAbbbb"
Output: 3
``` 
### Example 2:
```
Input: J = "z", S = "ZZ"
Output: 0
``` 

### Solution
```javascript
const findJewels = (Stones, Jewels) => {
  const charsOfStones = Stones.split('');
  let count = 0;
  for(let i=0; i<charsOfStones.length; i++) {
    if(Jewels.includes(charsOfStones[i])) {
      count ++;
    }
  }
  return count;
}

const Stones = 'aAAbbbb';
const Jewels = 'aA';

console.log(findJewels(Stones, Jewels));
```
