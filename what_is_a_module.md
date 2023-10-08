# What is a module

In Node.js, a module is a self-contained piece of code that performs a specific task. It can be a function, an object, or a piece of functionality that can be used in other parts of your application.

There are three types of modules in Node.js: internal, user-created, and third-party modules from npm.

## Internal Modules

Internal modules are built into Node.js and can be accessed using the require function without any additional installation. For example, the built-in `http` module is used to create a web server:

```jsx
const http = require('http');

http.createServer(function (req, res) {
  res.writeHead(200, {'Content-Type': 'text/plain'});
  res.end('Hello World!');
}).listen(8080);

```

In this example, we use the `require()` function to load the `http` module and use it to create a web server that listens on port 8080.

## User-created Modules

User-created modules are modules that you create yourself and can be included in your application using the require function. For example, you can create a module that exports a function that adds two numbers:

```jsx
// math.js

function add(a, b) {
  return a + b;
}

module.exports = add;

```

And then use it in another file:

```jsx
// index.js

const add = require('./math');

console.log(add(2, 3)); // output: 5

```

In this example, we create a module called `math.js` that exports a function called `add`. We then use the `require()` function to load the `add` function from the `math.js` module and use it to add two numbers.

## Third-party Modules

Third-party modules from npm are modules that are created by other developers and can be downloaded from the npm registry using the npm package manager. For example, you can use the `axios` module to make HTTP requests:

```jsx
const axios = require('axios');

axios.get('<https://jsonplaceholder.typicode.com/users>')
  .then(function (response) {
    console.log(response.data);
  })
  .catch(function (error) {
    console.log(error);
  });

```

In this example, we use the `require()` function to load the `axios` module and use it to make an HTTP GET request to the `jsonplaceholder` API.

## Exporting Modules

To export a module from a file, you need to use the `module.exports` or `export` keyword. This allows you to make the module available to other parts of your application. For example, you can create a module that exports an object:

```jsx
// logger.js

const logger = {
  log: function(message) {
    console.log(message);
  }
};

module.exports = logger;

```

And then use it in another file:

```jsx
// index.js

const logger = require('./logger');

logger.log('Hello, world!'); // output: Hello, world!

```

In this example, we create a module called `logger.js` that exports an object with a `log` function. We then use the `require()` function to load the `logger.js` module and use it to log a message.

## Importing Modules

In the latest versions of Node.js, you can also use the `import` statement to import a module. This statement is similar to the `require()` function but has some differences in syntax and behavior. For example, you can import a named export:

```jsx
// math.js

export function add(a, b) {
  return a + b;
}

```

And then use it in another file:

```jsx
// index.js

import { add } from './math';

console.log(add(2, 3)); // output: 5

```

In this example, we create a module called `math.js` that exports a named function called `add`. We then use the `import` statement to load the `add` function from the `math.js` module and use it to add two numbers.

## Conclusion

Modules are an essential part of Node.js development, and understanding how to create, import, and export them is crucial to building efficient and scalable applications.
