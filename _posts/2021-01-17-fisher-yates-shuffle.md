---
layout: post
title: Fisher Yates Shuffle
tags: [JS, Fisher Yates Shuffle]
---
## Fisher Yates Shuffle
```
function shuffle(array) {
  var copy = [],
    n = array.length,
    i

  // While there remain elements to shuffle…
  while (n) {
    // Pick a remaining element…
    i = Math.floor(Math.random() * array.length)

    // If not already shuffled, move it to the new array.
    if (i in array) {
      copy.push(array[i])
      delete array[i]
      n--
    }
  }

  return copy
}
```
<br/>

```
function shuffle(array) {
  var copy = [],
    n = array.length,
    i

  // While there remain elements to shuffle…
  while (n) {
    // Pick a remaining element…
    i = Math.floor(Math.random() * n--)

    // And move it to the new array.
    copy.push(array.splice(i, 1)[0])
  }

  return copy
}
```
<br/>

```
function shuffle(array) {
  var m = array.length,
    t,
    i

  // While there remain elements to shuffle…
  while (m) {
    // Pick a remaining element…
    i = Math.floor(Math.random() * m--)

    // And swap it with the current element.
    t = array[m]
    array[m] = array[i]
    array[i] = t
  }

  return array
}
```
<br/>

