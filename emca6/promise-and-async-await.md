# Promise and Async/Await

A good article can be found here : 

\[[https://blog.sessionstack.com/how-javascript-works-event-loop-and-the-rise-of-async-programming-5-ways-to-better-coding-with-2f077c4438b5](https://blog.sessionstack.com/how-javascript-works-event-loop-and-the-rise-of-async-programming-5-ways-to-better-coding-with-2f077c4438b5)\]\(How javascript eventloop works\) 

```javascript
function doSomething(){
    return new Promise(function(resolve,reject){
        console.log('doSomething, returning 3');
        setTimeout(resolve.bind(null,42),1000)
    })
}

doSomething().then(function(res){
    console.log('Got return value using promise.then(): ' + res);
});


// Use async await to implement this

(async () =>{
    res = await doSomething();
    console.log('Got return value using async/await: '+res);
})();
```

Some important notes:

1. Await waits for a promise
2. async function will return a promise object when called
3. In async function, return sets the value to be fulfilled when async function succeed. return\(val\) is the same as resolve\(val\) for promise.

 

