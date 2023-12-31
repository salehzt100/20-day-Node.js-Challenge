# Thinking in modules 

When developing node.js apps, it's essential to think about modules as separate pieces of functionality that can be easily maintained and reused. By dividing your code into smaller, self-contained modules, you can create more modular, maintainable, reusable, and efficient code.

## What should be a module?

Each module should have a clear and specific purpose, and should not be overly complex or tightly coupled to other modules. This means that you should aim to create modules that are focused on a single task or responsibility, and that can be used in different parts of the app or in different apps altogether.

For example, a module that handles database connections should only be responsible for managing the connection to the database, and should not be responsible for any other tasks, such as data validation or business logic. This allows the module to be reused across different parts of the app or in different apps, without having to modify its code.

On the other hand, a module that handles user authentication should only be responsible for authenticating users, and should not be responsible for any other tasks, such as database access or UI rendering. This allows the module to be easily maintainable, as any changes to the authentication logic can be made without affecting other parts of the app.

## Best export and import patterns

When exporting from a module, use the `export` keyword followed by the name of the function, variable, or class you want to export. You can also use `export default` to export a single value from a module.

When importing a module, use the `import` keyword followed by the name of the module, and then use dot notation to access the exported values. This allows you to selectively import only the functions, variables, or classes that you need from a module, and to avoid polluting the global namespace of your app.

For example:

```
// modules/myModule.js
export function myFunction() {
  // ...
}

export const myVariable = 42;

// app.js
import { myFunction, myVariable } from './modules/myModule.js';

```

## Index.js pattern

It's common to use an `index.js` file inside a folder to export several modules at once. This allows you to group related modules together, and to provide a clean and simple interface for importing them.

For example, suppose you have two modules, `myModule1` and `myModule2`, that you want to export from a folder called `modules`. You can create an `index.js` file inside the `modules` folder that exports both modules:

```jsx
// modules/myModule1.js
export function myFunction1() {
  // ...
}

// modules/myModule2.js
export function myFunction2() {
  // ...
}

// modules/index.js
export { myFunction1 } from './myModule1.js';
export { myFunction2 } from './myModule2.js';

// app.js
import { myFunction1, myFunction2 } from './modules';

```

By using the `index.js` pattern, you can simplify your import statements and make your code more readable.

In conclusion, thinking in modules is a fundamental concept in node.js development that can help you create more modular, maintainable, and reusable code. By following these guidelines, you can write code that is easier to understand, easier to modify, and easier to scale.
