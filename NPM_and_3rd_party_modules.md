# NPM and 3rd party modules

In Node.js, third-party modules are available for use in our code to extend its functionalities. We can manage these modules using Node Package Manager (NPM). NPM is a command-line interface that allows us to install, update, and remove packages.

To start, we need to create a package.json file in our project directory. This file contains metadata about our project and the dependencies required to run it. We can create this file using the command `npm init` and following the prompts.

Once we have our package.json file set up, we can start installing packages using the command `npm install <package-name>`. This command installs the package and saves it to our project's node_modules folder. It also adds the package as a dependency to our package.json file.

We can also install packages globally using the `-g` flag. These packages are installed in a global directory and are available to all projects. However, it is recommended to install packages locally to avoid version compatibility issues.

To run scripts using NPM, we can define them in our package.json file under the `scripts` field. For example, we can define a script to start our server using the command `node server.js` by adding the following line to our package.json file:

```json
"scripts": {
  "start": "node server.js"
}

```

We can then run this script using the command `npm run start`.

To import modules in our code, we can use the `require()` function. For example, if we want to use the `express` module, we can import it using the following code:

```jsx
import express from 'express'

```

This imports the `express` module and assigns it to a variable named `express`. We can then use the functionalities provided by the `express` module in our code.

In summary, NPM is a powerful tool that allows us to manage third-party modules in our Node.js projects. We can install packages, manage dependencies, run scripts, and import modules using NPM. With these functionalities, we can extend the capabilities of our Node.js applications and make them more efficient and effective.
