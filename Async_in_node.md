# Async in node

Asynchronous code is an important concept in Node.js. It allows the program to run non-blocking code, which means that other operations can be performed while waiting for a task to complete.

## Callbacks

Callbacks are a traditional way of handling asynchronous code in Node.js. A callback function is passed as an argument to a function that performs an asynchronous operation. When the operation is complete, the callback function is executed.

```jsx
fs.readFile('file.txt', (err, data) => {
  if (err) {
    console.error(err)
    return
  }
  console.log(data)
})

```

In the example above, the `readFile` function reads the contents of `file.txt`. When the file is read, the callback function is executed. If an error occurs during the operation, the error is passed to the callback function as the first argument.

## Promises

Promises provide a cleaner way of handling asynchronous code in Node.js. Promises represent a value that may not be available yet and allow you to chain multiple asynchronous operations together.

```jsx
const fs = require('fs/promises')

fs.readFile('file.txt')
  .then(data => {
    console.log(data)
  })
  .catch(err => {
    console.error(err)
  })

```

In the example above, the `readFile` function returns a promise. When the promise is resolved, the `then` function is executed. If the promise is rejected, the `catch` function is executed.

## Async/Await

Async/await is a newer way of handling asynchronous code in Node.js. It provides a more readable and concise way of writing asynchronous code by using the `async` and `await` keywords.

```jsx
const fs = require('fs/promises')

async function readFile() {
  try {
    const data = await fs.readFile('file.txt')
    console.log(data)
  } catch (err) {
    console.error(err)
  }
}

readFile()

```

In the example above, the `readFile` function is marked as `async`. This allows us to use the `await` keyword to wait for the `readFile` function to complete before executing the next line of code. If an error occurs during the operation, it is caught by the `try/catch` block.

## Error Handling

Error handling is an important part of handling asynchronous code in Node.js. In all of the examples above, error handling is performed using a `try/catch` block or a `catch` function.

It's important to handle errors properly to avoid crashing the application. In addition, it's important to provide meaningful error messages to help with debugging.
