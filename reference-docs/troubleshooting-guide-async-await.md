# Introduction to Async/Await

In JavaScript programming, 𝗔𝘀𝘆𝗻𝗰 starts tasks asynchronously, and 𝗔𝘄𝗮𝗶𝘁 patiently waits for them to complete before moving on.  The 𝘢𝘸𝘢𝘪𝘵 keyword pauses execution until the promise resolves. 

## Functions not Returning a `Promise()`
When you use 𝗮𝘀𝘆𝗻𝗰/𝗮𝘄𝗮𝗶𝘁, your function must return a 𝗣𝗿𝗼𝗺𝗶𝘀𝗲(). 

A 𝗣𝗿𝗼𝗺𝗶𝘀𝗲() in JavaScript is an object that represents the eventual completion or failure of an asynchronous operation. It allows you to handle the resulting value or error when it becomes available.

Without a 𝗣𝗿𝗼𝗺𝗶𝘀𝗲(), 𝗮𝘄𝗮𝗶𝘁 won’t work properly, and your code will behave unexpectedly. 

```
ex
```

Always return the 𝗣𝗿𝗼𝗺𝗶𝘀𝗲() explicitly.

```
ex
```

## Forgetting `await`
Forgetting to use 𝗮𝘄𝗮𝗶𝘁 when calling an 𝗮𝘀𝘆𝗻𝗰 function causes your program to move on before your 𝗣𝗿𝗼𝗺𝗶𝘀𝗲() resolves. 

Unfortunately, this mistake leads to incomplete or incorrect data.

```
ex
```

Always use 𝗮𝘄𝗮𝗶𝘁 when calling 𝗮𝘀𝘆𝗻𝗰 functions.

```
ex
```

## Handling Errors with `try/catch`
When working with 𝗮𝘀𝘆𝗻𝗰 functions, if you don’t wrap your 𝗮𝘄𝗮𝗶𝘁 calls in 𝘁𝗿𝘆/𝗰𝗮𝘁𝗰𝗵, unhandled errors can break the program.

```
ex
```

Always handle errors in 𝗮𝘀𝘆𝗻𝗰 functions with 𝘁𝗿𝘆/𝗰𝗮𝘁𝗰𝗵.

```
ex
```

## Using `Promise.all()`
Using 𝗣𝗿𝗼𝗺𝗶𝘀𝗲.𝗮𝗹𝗹() when making multiple async requests ensures:
- 𝗮𝘀𝘆𝗻𝗰 requests run concurrently
- handling their results in parallel

```
ex
```

Use 𝗣𝗿𝗼𝗺𝗶𝘀𝗲.𝗮𝗹𝗹() to run requests concurrently.

```
ex
```
