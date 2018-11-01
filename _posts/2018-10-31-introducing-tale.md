---
layout: post
title:  "[Better Code] Javascript Closure"
author: "Yena Park"
---

# For loops
The basic ```for``` loop is a staple of JavaScript development. It will run until something in it is false; its natural state is to go on forever! A ```for``` loop consists of three clauses: an initialization expression, a conditional expression, and an update expression.

```javascript
for (var i = 1; i < 5; i++) {
  console.log(i);  // 1 2 3 4
}
```
Here our clauses are as follows:

- Initialization: ```var i = 1```
- Conditional: ```i < 5```
- Update: ```i++```   

But note that at the end of our ```for``` loop the variable ```i``` actually has the value 5, not 4. For each loop we start with our initialization value, increment it by 1, and then check against the conditional expression. In other words, we execute clauses in first, third, second order even though it’s logical to think they’d be executed first, second, third.

Let’s review what actually happens in our ```for``` loop:

- 1st pass: i is 1, increment to 2, check is 2 < 5? Yes, so output.
- 2nd pass: i is 2, increment to 3, check is 3 < 5? Yes, so output.
- 3rd pass: i is 3, increment to 4, check is 4 < 5? Yes, so output.
- 4th pass: i is 4, increment to 5, check is 5 < 5? No, so exit loop.   

Hopefully it’s clear now why i is equal 5 even though we only output 1-4. We can prove this with the following code:

```javascript
for (var i = 1; i < 5; i++) {
  console.log(i); // 1 2 3 4
}

console.log("The value of i is now: ", i); // "The value of i is now: 5"
```

# Closures
The ```var``` keyword is function-scoped, meaning it lies within an enclosing function. Since there’s no function in this example, the enclosing scope is global. The ```for``` loop creates a global ```i``` variable.

Note as well that since ```var``` is function-scoped, ```i``` will be set to the closest enclosing function. In this example, that would be the global scope. More on this fact shortly.

# setTimeout
What if we want a one second pause before outputting each number in our loop? It seems logical we could just add a ```setTimeout``` method to achieve this.

```javascript
for (var i = 1; i < 5; i++) {
    setTimeout(() => console.log(i), 1000)  // 5 5 5 5
}
```

Why isn’t the output ```1 2 3 4```? There’s actually a lot going on in this subtle example.

The short answer is that the ```for``` loop executes first, then it looks for the ```i``` value, which is 5, and then outputs four times, one for each loop iteration.

Consider that even if we use a ```setTimeout``` of 0, the result is still the same.

```javascript
for (var i = 1; i < 5; i++) {
    setTimeout(() => console.log(i), 0)  // 5 5 5 5
}
```
I trust you’re thoroughly confused at this point. Don’t worry: it’ll all make sense shortly.

# JavaScript runtime engine
JavaScript is a single threaded single concurrent language which means it can only handle one task or piece of code at a time. Let’s see this in action:

So how is it we can write asynchronous code with it, such as using ```setTimeout()``` in our example?

The answer is that JavaScript runs **within a browser** and browsers do a lot more than just execute code. In fact, there are four distinct parts of the browser to consider:

- JavaScript runtime engine
- Web APIs provided by the browser like the ```DOM```, ```setTimeout```, etc.
- a callback queue for events with callbacks like ```onClick``` and ```onLoad```
- an event loop

The **runtime engine** is what executes our code and each major browser has a slightly different engine under the hood. For example Chrome uses the V8 engine which also happens to power NodeJs. This engine can only execute one piece of code at a time.

**Web APIs** are provided to us by the browser and include methods like ```setTimeout()```. If you simply type ```window``` in your console you can scroll through the long, long list of APIs included by default.

# Closure
The ```setTimeout``` function can access the value of ```i``` because of closure. We ask for ```i``` within our ```console.log``` statement, but its value is set in an outer, enclosing scope, that of the ```for``` loop. Since inner functions have access to variables in an outer function, we are able to go up a level and retrieve the value of ```i```, which is 5.



From JavaScript Closures: [setTimeout Inside a For Loop](https://wsvincent.com/javascript-closure-settimeout-for-loop/)
