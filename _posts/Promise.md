---
layout: post
title:  "[JavaScript] Promise"
author: "Yena Park"
---


## What is Promise?
**"A promise is an object that may produce a single value some time in the future"**


## Why we need Promise?


## Basic code - promise


## 3 processes(states) of Promise
The most basic concept when you use promise is status of promise.
The status is process of promise. Promise has 3 status from execution to termination.
- Pending : initial state, neither fulfilled nor rejected.
- Fulfilled : meaning that the operation completed successfully.
- Rejected : meaning that the operation failed.

#### Pending
When you call `new Promise()` method like below, the process is in Pending status.

```js
new Promise();
```

We can approach resolve, reject by factor in function of callback when you call `new Promise()` method. 

```js
new Promise(function (resolve, reject) {
  // ...
});
```

#### Fulfilled
When you call resolve, factor of callback function, the status will be in Fulfilled.

```js
new Promise(function (resolve, reject) {
  resolve();
});
```

And you can get the result of process, when you use `then()` in fufilled status.

```js
function getData() {
  return new Promise(function (resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// get result data of resolve() through resolvedData
getData().then(function (resolvedData) {
  console.log(resolvedData); // 100
});
```

<p class="notice">Fulfillled status is similar with 'complete'.</p>


#### Rejected
I told you that you can use resolve and reject for factor of callback function when you create `new Promise()` for Promise object.
In here, the status will be in Rejected when you execute reject() method for factor of reject.

```js
new Promise(function (resolve, reject) {
  reject();
});
```


Therefore, when the status is failed, you can get the reason of fail by 'catch()'

```js
function getData() {
  return new Promise(function (resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// Get Error of reject() in err
getData().then().catch(function (err) {
  console.log(err); // Error: Request is failed
});
```

