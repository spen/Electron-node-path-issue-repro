Using the scripts in package.json, you can run either the Electron app or Node app to see the issue...

```bash
yarn run electron-root
# ..
yarn run root-message
# etc.
```

```js
"scripts": {
  // All of the electron scripts below throw a 'cannot find module' error ( 'module' not found )  
  "electron-root": "NODE_PATH=. electron .",
  "electron-message": "NODE_PATH=./message-lives-here electron .",
  "electron-another-message": "NODE_PATH=./another-message-lives-here electron .",

  // Works as expected - logs the message found in /message.js
  "root-message": "NODE_PATH=. node main-node",

  // Works as expected - logs the message found in message-lives-here/message.js
  "message": "NODE_PATH=./message-lives-here node main-node",

  // Works as expected - logs the message found in another-message-lives-here/message.js
  "another-message": "NODE_PATH=./another-message-lives-here node main-node"
}
```