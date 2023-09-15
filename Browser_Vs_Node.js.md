# Browser vs. Node.js

JavaScript is a popular programming language used in both the browser and server-side applications. However, there are significant differences between how it works in the browser and in Node.js.

### Global Object

In a browser, the global object is `window`, while in Node.js, it is `global`. For example, to log the global object in a browser, we can use:

```jsx
console.log(window);
```

To do the same in Node.js, we use:

```jsx
console.log(global);
```

### Modules

We can import modules in the browser using script tags with the `type` attribute set to `module` and the `src` attribute set to the path of the module file. For example:

```html
<script type="module" src="./module.js"></script>
```

We can then use the exported functions in our JavaScript code. For instance, we can import a `sayHello` function from a module called `module.js` and use it in our main JavaScript file as follows:

```jsx
import { sayHello } from './module.js';
sayHello();
```

On the other hand, in Node.js, we use the `require`  or `import` statement to import modules:

```jsx
import { module } from './module.js';
```

### DOM

The browser has a Document Object Model (DOM) that allows us to interact with HTML elements. For example, to change the text of an HTML element in the browser, we can use:

```jsx
document.getElementById('elementId').innerHTML = 'New text';
```

However, in Node.js, there is no DOM, so we cannot access or manipulate HTML elements.

### Server vs. Website

Node.js is mainly used for server-side applications, while the browser is used for websites. For example, we can create a simple server in Node.js using:

```jsx
const http = require('http');

const server = http.createServer((req, res) => {
  res.write('Hello World!');
  res.end();
});

server.listen(3000);
```

On the other hand, in the browser, we can create a website using HTML, CSS, and JavaScript.

### Console

The `console` object works the same way in both the browser and Node.js. For example, to log a message in the browser, we can use:

```jsx
console.log('Hello World!');
```

Similarly, in Node.js, we can use:

```jsx
console.log('Hello World!');
```

JavaScript is used in both the browser and Node.js, but there are significant differences in how it works in each environment. However, there are also many similarities, and if you already know JavaScript, you should be able to quickly pick up Node.js. Understanding the differences and similarities between the two environments is crucial when developing applications in either of them.
