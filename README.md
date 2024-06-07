resolve("There is a count value.");
    } else {
        reject("There is no count value");
    }
});

console.log(countValue);
```


* Method
- all: Waits for all promises to be resolved or any one to be rejected
- any: Returns the promise value as soon as any one of the promises is fulfilled
- race: Wait until any of the promises is resolved or rejected
- reject: Returns a new Promise object that is rejected for the given reason
- resolve: Returns a new Promise object that is resolved with the given value
- catch: Appends the rejection handler callback
- then: Appends the resolved handler callback


A Javascript Promise is like having a box with a red and green light on it. One of the lights will light up, but you don't know when. If the light turns green(promise resolves), a cookie appears inside the box. If the light turns red(promise rejects or error), a note will appear in the box with a reason why the cookie didn't appear. You need to promise ahead of time what you will do right after the light turns green(maybe eat the cookie?) and what you will do if the light turns red(throw a tantrum?).

From ES7, we were provide Async/await to handle asynchronous
We use the async keyword with a function to represent that the function is an asynchronous function. The async function returns a promise.
The await keyword is used inside the async function to wait for the asynchronous operation.

```
// a promise
let promise = new Promise(function (resolve, reject) {
    setTimeout(function () {
    resolve('Promise resolved')}, 4000); 
});

// async function
async function asyncFunc() {

    // wait until the promise resolves 
    let result = await promise; 

    console.log(result);
    console.log('hello');
}

// calling the async function
asyncFunc();
```