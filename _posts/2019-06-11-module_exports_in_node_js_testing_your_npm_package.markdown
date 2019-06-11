---
layout: post
title:      "Module.exports in node.js (+ testing your npm package!)"
date:       2019-06-11 11:25:47 -0400
permalink:  module_exports_in_node_js_testing_your_npm_package
---

In a previous blog post, I discussed the process of creating and publishing an npm package. This will be a post on testing and using your own npm package and further understanding `module.exports` in node.js.

**To use your npm package: (testing w/ node.js)**

Install it in your project with `npm i @jk-me/practicenpm`. You can do this in a new project folder to test your code. 

Create a js file (ex. `index.js`) in the root directory of project. Import the package and set it to a variable of your choice. ```const pie = require(‘@jk-me/practicenpm’)```

Write code in index.js that uses the functions in the package and `console.log` the output. In terminal run `node index.js`to execute script and see output in the terminal.

```
const pie = require(‘@jk-me/practicenpm’)         //loads module, w exports.tiny fn 
console.log( pie.tiny("a string with spaces") )      //uses exported fn from required module
=> 'astringwithspaces'                                    //logged output in terminal
``` 

You can also use node (javascript) cli with `node` command, and `.exit` to exit

After installing your package in your test project folder, it will appear inside it in the `node_modules` directory. You can modify your code in here to test it using the above method before actually updating your module and publishing a new version to npm. Of course this is only for testing purposes and you normally wouldn't modify packages after installing them.

**module.exports**

Node.js uses a module system, where each file is treated as a separate module. Every JS file has `module.exports` as a special object by default.

Module.exports is the object returned by a `require(‘yourModule’)` call of the module in another file. It can be a function itself, a class constructor, an object pointing to multiple functions, or any other value.

Functions and objects are added to the root of a module file by specifying attributes to the `exports` object. For example, `module.exports.myFn = () => alert(‘Hello’)`

Exported functions can also be written as

```
module.exports = {
  addone: function(n) { return n+1 },
  minusone: function(n) { return n-1 }
};
```

`exports` is a shortcut for `module.exports` However, assigning a value to `exports` itself no longer binds it to module.exports and it will not be exported, so you should also assign that value to `module.exports`.

Variables local to module files are private. Node.js wraps the module in a function called module wrapper before executing a require statement.

There are 3 types of modules: core, local and third-party. Core modules are included in node.js. They must still be imported (ex. `require(‘http’)`), Some examples include `’http’`, `’path’`, and `’querystring’`, used to set up Node.js http servers, deal with file paths, and deal with query strings, respectively.

Local modules exist in your local node.js app, and third-party modules are, for example, imported npm packages.

Resources:
* [NodeJS docs - modules](https://nodejs.org/api/modules.html#modules_modules)
* [StackOverflow - modules](https://stackoverflow.com/questions/5311334/what-is-the-purpose-of-node-js-module-exports-and-how-do-you-use-it)

