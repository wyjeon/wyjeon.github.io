---
layout: post
title: async, await
tags: [JS, Callback]
---
## 1. async
Promise
```
function fetchUser() {
  // do network request in 10 secs...
  return new Promise((resolve, reject) => {
    resolve("wyjeon");
  });
}

const user = fetchUser();
user.then(console.log);
```
<br/>

async
```
async function fetchUser() {
  // do network request in 10 secs...
  return "wyjeon"
}

const user = fetchUser();
user.then(console.log);
```
<br/>
<hr/>

## 2. await
```
function delay(ms) {
  return new Promise(resolve => setTimeout(resolve, ms));
}

async function getApple() {
  await delay(1000); // 1sec
  return "apple";
}

async function getBanana() {
  await delay(1000); // 1sec
  return "banana";
}

async function pickFruits() {
  const apple = await getApple();
  const banana = await getBanana();
  return `${apple} + ${banana}`;
}

pickFruits().then(console.log); // 2sec
```
<br/>

Parallel
```
async function pickFruits() {
  const applePromise = getApple();
  const bananaPromise = getBanana();
  const apple = await applePromise;
  const banana = await bananaPromise;
  return `${apple} + ${banana}`;
}

pickFruits().then(console.log); // 1sec
```
<br/>
<hr/>

## 3. Useful Promise APIs
Promise.all()
```
function pickAllFruits() {
  return Promise.all([getApple(), getBanana()])
  .then(fruits => fruits.join(" + "));
}

pickAllFruits().then(console.log);
```
<br/>

Promise.race()
```
function pickOnlyOne() {
  return Promise.race([getApple(), getBanana()])
}

pickOnlyOne().then(console.log);
```
<br/>

