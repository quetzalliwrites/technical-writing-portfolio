# Introduction to Async/Await

In JavaScript programming, `𝗔𝘀𝘆𝗻𝗰` starts tasks asynchronously, and `𝗔𝘄𝗮𝗶𝘁` patiently waits for them to complete before moving on. 

The `𝗔𝘄𝗮𝗶𝘁` keyword pauses execution until the promise resolves. 

## Functions not Returning a `Promise()`
When you use `𝗮𝘀𝘆𝗻𝗰/𝗮𝘄𝗮𝗶𝘁`, your function must return a `𝗣𝗿𝗼𝗺𝗶𝘀𝗲()`. 

A `𝗣𝗿𝗼𝗺𝗶𝘀𝗲()` in JavaScript is an object that represents the eventual completion or failure of an asynchronous operation. It allows you to handle the resulting value or error when it becomes available.

Without a `𝗣𝗿𝗼𝗺𝗶𝘀𝗲()`, `𝗮𝘄𝗮𝗶𝘁` won’t work properly, and your code will behave unexpectedly. 

```js
async function fetchSuperCoolData() {
    // Missing return statement for the promise
    fetch('https://api.example.com/data');
  }
  
  async function getSuperCoolData() {
    // Oops! Won't work!
    const data = await fetchSuperCoolData(); 
    // Oops! Undefined.
    // Cause fetchSuperCoolData() didn't return a promise
    console.log(data); 
  }
  
  getSuperCoolData();
```

Always return the `𝗣𝗿𝗼𝗺𝗶𝘀𝗲()` explicitly.

```js
async function fetchSuperCoolData() {
// Properly returning the promise
return fetch('https://api.example.com/cool-data');
}

async function getSuperCoolData() {
const data = await fetchSuperCoolData();
// Correctly handles the resolved promise
console.log(data); 
}

getSuperCoolData();
```

## Forgetting `await`
Forgetting to use `𝗮𝘄𝗮𝗶𝘁` when calling an `𝗮𝘀𝘆𝗻𝗰` function causes your program to move on before your `𝗣𝗿𝗼𝗺𝗶𝘀𝗲()` resolves. 

Unfortunately, this mistake leads to incomplete or incorrect data.

```js
async function fetchSuperCoolData() {
return fetch('https://api.example.com/data');
}

async function processSuperCoolData() {
// AHHH! You forgot to use await!
const data = fetchSuperCoolData(); 
// Outputs a Promise object, not actual data
console.log(data); 
}

processSuperCoolData();
```

Always use `𝗮𝘄𝗮𝗶𝘁` when calling `𝗮𝘀𝘆𝗻𝗰` functions.

```js
async function fetchSuperCoolData() {
const response = await fetch('https://api.example.com/data');
// Assume the response is JSON
return response.json(); 
}

async function processSuperCoolData() {
// Correct usage of await
const data = await fetchSuperCoolData(); 
// Outputs the actual data
console.log(data); 
}

processSuperCoolData();
```

## Handling Errors with `try/catch`
When working with `𝗮𝘀𝘆𝗻𝗰` functions, if you don’t wrap your `𝗮𝘄𝗮𝗶𝘁` calls in `𝘁𝗿𝘆/𝗰𝗮𝘁𝗰𝗵`, unhandled errors can break the program.

```js
async function fetchSuperCoolData() {
const response = await fetch('https://api.example.com/data');
// This might fail if there's a network issue
return response.json(); 
}

async function getSuperCoolData() {
// No error handling
const data = await fetchSuperCoolData(); 
console.log(data);
}

getSuperCoolData();
// Yikes! If an error occurs, it won't be caught. The program could crash!
```

Always handle errors in `𝗮𝘀𝘆𝗻𝗰` functions with `𝘁𝗿𝘆/𝗰𝗮𝘁𝗰𝗵`.

```js
async function fetchSuperCoolData() {
const response = await fetch('https://api.example.com/data');
return response.json();
}

async function getSuperCoolData() {
try {
const data = await fetchSuperCoolData();
// Will only log if fetchSuperCoolData() succeeds
console.log(data); 
} catch (error) {
// Catches errors and prevents program crash
console.error('Error fetching superCoolData:', error); 
}
}

getSuperCoolData();
```

## Using `Promise.all()`
Using `𝗣𝗿𝗼𝗺𝗶𝘀𝗲.𝗮𝗹𝗹()` when making multiple async requests ensures:
- `𝗮𝘀𝘆𝗻𝗰` requests run concurrently
- handling their results in parallel

```js
async function fetchSuperCoolData1() {
return fetch('https://api.example.com/data1');
}

async function fetchSuperCoolData2() {
return fetch('https://api.example.com/data2');
}

async function processSuperCoolData() {
const data1 = await fetchSuperCoolData1();
const data2 = await fetchSuperCoolData2();
// These requests are processed one after another, increasing wait time
console.log(data1, data2);
}

processSuperCoolData();
```

Use `𝗣𝗿𝗼𝗺𝗶𝘀𝗲.𝗮𝗹𝗹()` to run requests concurrently.

```js
async function fetchSuperCoolData1() {
return fetch('https://api.example.com/data1');
}

async function fetchSuperCoolData2() {
return fetch('https://api.example.com/data2');
}

async function processSuperCoolData() {
const [data1, data2] = await Promise.all([fetchSuperCoolData1(), fetchSuperCoolData2()]);
// Fetches both data concurrently, speeding up the process
console.log(data1, data2);
}

processSuperCoolData();
```
