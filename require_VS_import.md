# Require vs. Import

In Node.js, `require` and `import` are two ways to include external modules in your code. Both of them serve the same purpose, but they have some differences that are worth noting.

## Require

`require` is a built-in function in Node.js that allows you to load external modules. It works synchronously, which means that it blocks the execution of the rest of the code until the module is loaded. Here is an example:

```jsx
const fs = require('fs');
const data = fs.readFileSync('file.txt', 'utf8');
console.log(data);

```

In this example, we are loading the `fs` module, which provides a way to interact with the file system. We then use the `readFileSync` method to read the contents of a file called `file.txt`. Finally, we log the contents to the console.

## Import

`import` is a newer way to include external modules in your code. It is part of the ES6 (ECMAScript 2015) specification, and it works asynchronously. Here is an example:

```jsx
import fs from 'fs/promises';
async function readFile() {
  const data = await fs.readFile('file.txt', 'utf8');
  console.log(data);
}
readFile();

```

In this example, we are using the `import` statement to load the `fs/promises` module, which provides a way to interact with the file system using promises. We then define an `async` function called `readFile`, which uses the `readFile` method to read the contents of a file called `file.txt`. Finally, we log the contents to the console.

## Exporting

In addition to loading external modules, you may also want to export your own code as a module that can be used by other parts of your application. There are several ways to do this, depending on the module system you are using.

### CommonJS

CommonJS is the module system used by Node.js. To export a module in CommonJS, you can use the `module.exports` or `exports` objects. Here is an example:

```jsx
// module.js
function hello(name) {
  console.log(`Hello, ${name}!`);
}
module.exports = { hello };

// app.js
const module = require('./module');
module.hello('world');

```

In this example, we define a function called `hello` in a module called `module.js`. We then export the function using `module.exports`. In `app.js`, we load the module using `require`, and we call the `hello` function.

### ES6 Modules

ES6 modules are a newer module system that is supported by some browsers and by Node.js with the `--experimental-modules` flag. To export a module in ES6, you can use the `export` keyword. Here is an example:

```jsx
// module.js
function hello(name) {
  console.log(`Hello, ${name}!`);
}
export { hello };

// app.js
import { hello } from './module.js';
hello('world');

```

In this example, we define a function called `hello` in a module called `module.js`. We then export the function using the `export` keyword. In `app.js`, we load the module using `import`, and we call the `hello` function.

## Conclusion

In conclusion, `require` and `import` are two ways to load external modules in Node.js. They have some differences in their syntax and behavior, but they both serve the same purpose. Additionally, there are different ways to export your own code as a module, depending on the module system you are using.
