# Creating a CLI

## CLI basics

We’re now ready to create the CLI for our note taking app. First thing we’re going to do is create a new Node.js project, we can do this by using the `npm` cli:

```bash
npm init
```

The init command will create a `package.json` file for us on the root of the directory in which we ran the command. Don’t worry about npm and the package.json, we’ll get to those soon enough.

Next, let’s create the file where we’ll write our JavaScript for the CLI. Create a file called `index.js` on the root if you don’t have one already. Here in this file add a for now, just add a `console.log`. We’ll create the logic for allowing a user to add a new note to the app. So we need a few things:

1. A command to use in the terminal
2. The ability for that command to accept arguments and flags
3.  Using the value of that argument to create a new note

Let’s start by creating a command we can use in our terminal. To do that, we have to register a command name in a package.json:

```bash
{
  "name": "note",
  "bin": {
    "note": "./index.js"
  }
}
```

Under the `bin` field, we can use pretty much any name we want. This name will end up being the command we use in the terminal as our CLI, so pick a good name! We’ll just use `note`. Notice we add the file path to that js file we created. That’s telling Node.js that we want to execute that file with the note command is ran. We need to augment that file with some hints for our machine. That’s because our computer might have many OS languages installed, like python or ruby, so it won’t know which one of these should be used to execute our program. We want to use Node.js to execute our js file. So at the top, the very first line of our JS file, we add:

```bash
#!/usr/bin/env node
```

This is a hashbang. A hashbang is a special comment placed at the top of a script that tells the operating system which interpreter to use when running the script. In the context of a Node.js CLI app, the hashbang tells the machine to use Node.js as the interpreter to execute the JS file. 

Next, we need to install this CLI on our machine so we can test it out. We could actually install this globally like it’s a 3rd party module, but instead we’re going to create a symlink.

A symlink, or symbolic link, is a special type of file that acts as a reference to another file or directory. In the context of a Node.js CLI app, creating a symlink allows us to run the CLI from anywhere in our file system, just like a globally installed third-party module. This means that we can run our `note` command from any directory on our machine, without having to navigate to the directory where the CLI code is stored. Creating a symlink is done using the `npm link` command, which creates a symlink from the globally installed npm package to the locally stored code. So run the command:

```bash
npm link
```

We should not be able to run the `note` command in our terminal and see our log output, try it out!

```bash
note
```

## Note logic

Now that we have a working CLI, let’s start creating the logic for our note taking app! For now, we want to be able to except some input from the terminal as a new note. Later we will figure out what to do with that input, but for now, lets just make sure we can read it. To do so, we can tap into the `process` . So in our index.js file:

```jsx
// index.js
const note = process.argv[2];
const newNote = {
  id: Date.now(),
  note,
}
console.log('your new note', newNote)
```

The above code assumes anything you place after the note command will be the note. It then takes that note and creates a new object and logs it. Simple. So the command would be:

```jsx
note "this is my note"
```

Notice I put the note in strings so the terminal doesn’t think each word is a new argument, but instead the while string is the argument. 

This is cool, but we need some more features here. We need to be able to save the notes somewhere, we also need some more flexibility on how we create notes. Like adding tags, a name, a status. Being able to list all notes and even removing a note would be useful too. So we’ll need more commands and flags for our CLI. We could parse this ourself, but there are some handy 3rd party modules we can install that will make this easier. What is a module you ask? We’re covering that next!
