---
layout: post
title:      "Javascript Closures"
date:       2019-05-26 02:07:34 +0000
permalink:  javascript_closures
---


A question I’ve been asked frequently as a basic test of JS understanding is how to explain the concept of a closure. 

Whether in phone screens, interviews, or even Flatiron project evaluations, this seems to be a common first evaluation for technical competency in javascript.

> “A closure is the combination of a function and the lexical environment within which that function was declared.” 
-MDN web docs

A closure is an inner function. It retains the scope it was defined in (the outer function), and the value of the variables defined in that scope.  

```
function makeFunc() {
  let name = 'Mozilla';
  function displayName() {
    alert(name);
  }
  return displayName;
}

let a = makeFunc();      //a has value of displayName function
a();      //triggers an alert 'Mozilla'
```

In the above example, the inner function displayName retains the scope of the outer function inside which it was declared, and can still refer to the value of the *name* variable from the outer function. 

Even when it the value of makeFunc's return value is assigned to a new variable, the scope is still retained and a() still returns an alert with the value of 'Mozilla'

Closures can be used to make similar functions with slightly different standard values. 

For example a tip calculator function. The outer function takes the argument of the tip percentage, and the inner function takes the argument of the total payment. 

```
function calcTip( percent ){
  return function( payment ){
	  return (percent / 100) * payment
	}
}

let tip18 = calcTip(18)   //tip18 is now a function calculating 18% tip
```


