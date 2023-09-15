# Non blocking I/O

Node.js is known for its efficient and scalable I/O model, which is based on a non-blocking, event-driven architecture. This means that I/O operations are handled asynchronously and do not block the execution of the main program. In contrast to traditional blocking I/O models, where the program waits for each I/O operation to complete before continuing to the next one, Node.js can execute multiple I/O operations simultaneously.

Here are some key points that explain how Node.js achieves non-blocking I/O:

- **Event Loop**: Node.js uses an event loop to manage I/O operations. The event loop is a loop that listens for events and triggers the corresponding callback functions. When an I/O operation is initiated, Node.js registers the corresponding callback function with the event loop. Once the operation completes, the event loop triggers the callback function, which can then process the result.
- **Callbacks**: Callbacks are functions that are passed as arguments to other functions. In Node.js, callbacks are used to handle the results of I/O operations. When an I/O operation is initiated, a callback function is provided that will be called when the operation completes. By using callbacks, Node.js can execute other code while waiting for I/O operations to complete.
- **Non-Blocking APIs**: Node.js provides a set of non-blocking APIs that allow developers to perform I/O operations asynchronously. For example, the `fs` module provides non-blocking methods for reading and writing files. When these methods are called, Node.js immediately returns control to the program, allowing it to continue executing other code. Once the I/O operation completes, the callback function is called with the result.
- **Single-Threaded**: Node.js is a single-threaded environment, which means that all I/O operations are handled by a single thread. This allows Node.js to handle large numbers of simultaneous connections without consuming a lot of system resources. In contrast, other environments like Python and Ruby use multiple threads to handle I/O operations, which can lead to higher resource consumption and slower performance.

## Example

Blocking code example:

```jsx
const getUserSync = (userId) => {
  const users = {
    1: { name: 'John', age: 35 },
    2: { name: 'Jane', age: 28 }
  };
  return users[userId];
}

const user = getUserSync(1);
console.log(user);
```

In this example, the `getUserSync` function returns a user object from a hardcoded list of users. This function is **blocking**, because it executes synchronously and returns the result immediately.

Non-blocking code example:

```jsx
const getUserAsync = (userId, callback) => {
  const users = {
    1: { name: 'John', age: 35 },
    2: { name: 'Jane', age: 28 }
  };
  setTimeout(() => {
    callback(users[userId]);
  }, 1000);
}

getUserAsync(1, (user) => {
  console.log(user);
});
```

In this example, the `getUserAsync` function returns a user object from a hardcoded list of users, but it executes asynchronously, using the `setTimeout` function to delay the execution of the callback function by 1 second. The `getUserAsync` function takes a callback function as its second argument, which is called with the user object once it has been retrieved.
