# Using yargs

We’re now going to install and use a 3rd party module to help us create our Note taking app. Its called `yargs`.

```json
npm i yargs
```

Once you install it, create a src folder with a commands.js file and let’s add some commands.

```jsx
import yargs from 'yargs'
import { hideBin } from 'yargs/helpers'

yargs(hideBin(process.argv))
  .command('new <note>', 'create a new note', yargs => {
    return yargs.positional('note', {
      describe: 'The content of the note you want to create',
      type: 'string'
    })
  }, async (argv) => {
    
  })
  .option('tags', {
    alias: 't',
    type: 'string',
    description: 'tags to add to the note'
  })
  .command('all', 'get all notes', () => {}, async (argv) => {
    
  })
  .command('find <filter>', 'get matching notes', yargs => {
    return yargs.positional('filter', {
      describe: 'The search term to filter notes by, will be applied to note.content',
      type: 'string'
    })
  }, async (argv) => {
    
  })
  .command('remove <id>', 'remove a note by id', yargs => {
    return yargs.positional('id', {
      type: 'number',
      description: 'The id of the note you want to remove'
    })
  }, async (argv) => {
    
  })
  .command('web [port]', 'launch website to see notes', yargs => {
    return yargs
      .positional('port', {
        describe: 'port to bind on',
        default: 5000,
        type: 'number'
      })
  }, async (argv) => {
    
  })
  .command('clean', 'remove all notes', () => {}, async (argv) => {
    
  })
  .demandCommand(1)
  .parse()


```

another example : 

```jsx

import yargs from 'yargs'
import { hideBin } from 'yargs/helpers'
yargs(hideBin(process.argv)).check((argv) => {
    if (!isNaN(argv.name)) {
        console.error('Error: The name must be a string value.');
        process.exit(1)
    }
    return true; // Validation passed
})
    .command('hello [name]', 'welcome', (yargs) => {
        return yargs.option('name', {
            type: 'string',
            describe: 'name to print hello name',
            default: 'saleh'
        });
    }, (argv) => {
        console.log(`hello ${argv.name}`);
    })
    .demandCommand(1)
    .parse();



```

We’re using yargs to setup different commands we can use from our cli, for example, the new command can be used like:

```jsx
note new "this is my new note"
```

Right now, the function for each command is blank, we need to make them actually do something next.
