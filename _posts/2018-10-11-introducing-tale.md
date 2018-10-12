---
layout: post
title:  "[Better Code] Fizz Buzz"
author: "Yena Park"
---

"Write a program that prints the numbers from 1 to 100. But for multiples of three print “Fizz” instead of the number and for the multiples of five print “Buzz”. For numbers which are multiples of both three and five print “FizzBuzz”."

## First time 
```javascript
const FizzBuzz = (num) => {
  if(num % 3 === 0 && num % 5 === 0) {
    console.log("FizzBuzz")
  } else if (num % 3 === 0) {
    console.log("Fizz")
  } else if (num % 5 === 0) {
    console.log("Buzz")
  } else {
    console.log(num)
  } 
}
```

## After refactoring
```javascript
const Fizz = (num) => {
  return ((num) % 3 === 0) ? "Fizz" : "";
};

const Buzz = (num) => {
  return (num % 5 === 0) ? "Buzz" : "";
};

const FizzBuzz = (num) => {
  const result = Fizz(num) + Buzz(num);
  return (result === "") ? num : result;
};


for(let i=1; i<=100; i++) {
  console.log(FizzBuzz(i));
}
```
