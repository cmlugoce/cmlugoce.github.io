---
layout: post
title:      "A JavaScript Promise..."
date:       2019-01-10 02:30:11 +0000
permalink:  a_javascript_promise
---


![](https://images.unsplash.com/photo-1531417666976-ed2bdbeb043b?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=500&q=60)

I've always had a love/hate relationship with JavaScript, but now I'm starting to love it a lot!  One of the topics that I found very interesting and cool in JS was the `Promise`. 


### Promise

A `Promise` is an object representing the eventual completion or failure of an asynchronous operation. 

It  comes with some guarantees:

* Callbacks will never be called before the completion of the current run of the JavaScript event loop.

* Callbacks added with `then()` even after the success or failure of the asynchronous operation, will be called, as above.

* Multiple callbacks may be added by calling `then()` several times. Each callback is executed one after another, in the order in which they were inserted.

According to the MDN a promise is describes as :

> a proxy for a value not necessarily known when the promise is created. It allows you to associate handlers with an asynchronous action's eventual success value or failure reason. This lets asynchronous methods return values like synchronous methods: instead of immediately returning the final value, the asynchronous method returns a promise to supply the value at some point in the future.
> 


A promise can be:

*    **fulfilled** - The action relating to the promise succeeded

*    **rejected** - The action relating to the promise failed

*    **pending** - Hasn't fulfilled or rejected yet

*    **settled** - Has fulfilled or rejected

A pending promise can either be fulfilled with a value, or rejected with a reason (error). When either of these options happens, the associated handlers queued up by a promise's then method are called. (If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached.)

#### Chaining

Creating a promise chain will execute two or more asynchronous operations back to back, where each subsequent operation starts when the previous operation succeeds, with the result from the previous step.

For instance:
```
const promise2 = doSomething().then(successCallback, failureCallback);

```

In this case, `promise2` represents the completion not just of `doSomething()`, but also of the `successCallback` or `failureCallback` you passed in, which can be other asynchronous functions returning a promise.



![](https://mdn.mozillademos.org/files/15911/promises.png)


Let's go ahead and build a simple promise:

```
// We make a new promise: 

let aPromise = new Promise((resolve, reject) => {
  // The executor function is called with the ability to resolve or
        // reject the promise
  // // This is only an example to create asynchronism 
  setTimeout(function(){
    resolve("AWESOME!"); // simulate when async succeeds
  }, 1000);
});

aPromise.then((successPhrase) => {
  console.log("I am " + successPhrase);
});
```

And now, test, test, test!!

<iframe height="400px" width="100%" src="https://repl.it/@cmlugoce/QuizzicalMotionlessBit?lite=true" scrolling="no" frameborder="no" allowtransparency="true" allowfullscreen="true" sandbox="allow-forms allow-pointer-lock allow-popups allow-same-origin allow-scripts allow-modals"></iframe>


You can also go ahead and test this code using the console in the browser!


### References

[Using promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)

[Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

