---
layout: post
title:  "[Algorithm] Maximum difference between two elements"
author: "Yena Park"
---

Given an array, find out the maximum difference between any two elements such that larger element appears after the smaller number.

### Example 1:
```
Input : arr = {2, 3, 10, 6, 4, 8, 1}
Output : 8
```
Explanation : The maximum difference is between 10 and 2.   
   
   
### Example 2:
```
Input : arr = {7, 9, 5, 6, 3, 2}
Output : 2
```
Explanation : The maximum difference is between 9 and 7.   


### Solution
```javascript
const findMaxDifference = (array) => {
  let maxDifference = -1;
  for (let i=0; i<array.length; i++) {
    for(let j=i; j<array.length; j++) {
      if(array[j] > array[i] && (array[j] - array[i] > maxDifference)) {
        maxDifference = array[j] - array[i];
      }
    }
  }
  return maxDifference
}

const array=[2, 3, 10, 6, 4, 8, 1]
console.log(findMaxDifference(array)) //returns 8
```
