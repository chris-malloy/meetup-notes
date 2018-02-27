# Asynchronus Patterns and MultiCore

## Notes

### Event Loop

Two things to think about - Concurrancy, Parallelism
Concurrancy - multithreading a single CPU to execute multiple tasks
Parallelism - using multiple CPU's to execute multiple tasks

JavaScript is highly concurrent in Node and the browser thanks to the event Loop

#### Event Loop Proccess

Call Stack - How we keep track of code to execute
Web API's natively implemented API's like DOM or timeout
Callback Queue - place for finished callbacks to go before they are executed in the call Stack

Call to completion - when code in callback queue has to wait on code in call Stack

look to bit.ly/event-loop-help for more in depth info

### Three pattern's to Cover

#### Declare concurrent dependencies with Async IIFE's

an async IIFE

```javascript
(async () => {
    /* do things */
})
```

so imagintion putting other tasks inside this IIFE (gulp does this)

look to bit.ly/async-iife for more in depth info

#### Manage Concurrency with Functional Programming

Semaphore - manages spots for task to sit in while they are being processed

```javascript
let semaphore = new Semaphore(4);

await semaphore.acquire();
semaphore.release();
```

this will work, but break as soon as there are other outside issues that the code is not built to handle

need to make sure that it releases something no matter what

look to bit.ly/sempaphorejs for more info

#### Web Worker Cluster

standard api for creating background threads

wrap a worker in a promise like interface
