---
layout: post
title:  "[Algorithm] Two sum problem"
author: "Yena Park"
---

The two sum problem is a common interview question, and it is a variation of the subset sum problem. There is a popular dynamic programming solution for the subset sum problem, but for the two sum problem we can actually write an algorithm that runs in O(n) time. The challenge is to find all the pairs of two integers in an unsorted array that sum up to a given S. 


### Example :
```
For example, if the array is [3, 5, 2, -4, 8, 11] and the sum is 7,
your program should return [[11, -4], [2, 5]] because 11 + -4 = 7 and 2 + 5 = 7.
``` 

### Solution
```javascript
const twoSum = (arr, S) => {
  let sum = [];
  for(let i=0; i<arr.length; i++) {
    for(let j=i+1; j<arr.length; j++) {
      if(arr[i] + arr[j] === S) {
        sum.push([arr[i], arr[j]])
      }
    }
  }
  return sum;
}

const arr = [3, 5, 2, -4, 8, 11];
const S = 7;

console.log(twoSum(arr, S)); //[[5, 2], [-4, 11]]
```
