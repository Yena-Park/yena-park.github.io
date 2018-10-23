---
layout: post
title:  "[Better Code] Pure function"
author: "Yena Park"
---

**_Pure function_** is a concept mainly used in functional programming lanuguages but it can be applied in any programming paradigm.

# Given same argument to the function, it should always return same output.
How can we be certain that above metioned point holds while writing pure function?
> ## Function must not use state of the program to compute its output.    
```javascript
const x = 5 //x is a global variable
const multiply = (y) => {
  return y*x
}
```

```multiply```is not a pure function becuase its ouput is computed using global variable x. If the value of x changes, output of ```multiply``` function also changes for same input.

```javascript
const x = 5
multiply(2); //returns 10

const x = 10 //value of global variable x changed from 5 to 10
multiply(2); // returns 20
```

In above example input to ```multiply``` function is same but output has changed depending on the state of the program.
**Since ```multiply``` function is not giving same output for same input, it is not pure.**

To make ```multiply``` pure, we can pass global variable x as argument to it.

```javascript
const multiply_pure = (y, x) => {
  return y*x
}
multiply_pure(2, 3);   //returns 6
multiply_pure(2, 3);   //returns 6
```
No matter how many times we call ```multiply_pure``` with same input, it will always return same output.
> ## Secondly, a function must not take mutable objects as arguments and should not use it to compute output of the function when working in a concurrent programming environment.



# Evaluation of the result should not cause any side effects such as mutation of mutable objects or output to I/O devices
> ## Pure function should not mutate any mutable object.
