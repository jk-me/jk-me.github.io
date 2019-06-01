---
layout: post
title:      "Creating an npm package"
date:       2019-05-31 22:56:30 -0400
permalink:  creating_an_npm_package
---


I wrote a blog post recently on how creating developer tools can be beneficial in understanding how to write programs that have real users. This post is my experience attempting to create an npm package for practice and to understand its underlying principles.

I followed this [freecodecamp](https://www.freecodecamp.org/news/how-to-make-a-beautiful-tiny-npm-package-and-publish-it-2881d4307f78/) blog post on how to create and publish a very tiny npm package. I will include an abbreviated version of the steps listed in this post, along with some additional explanations I found helpful.

Basically an npm module only requires a package.json file with name and version properties to be published.

In order to publish an npm package, you will need to sign up for an npm account at [npmjs.com](http://npmjs.com)

Use the following commands in your computer terminal to login to npm with your username, password, and email
```
npm adduser
```
or 
```
npm login
```

You can create a new directory (`md folder_name`) with a package.json file (`cd folder_name && touch package.json`) in your terminal. In the package.json file you will need name and version properties in order to publish

```
{"name": "@jk-me/practicenpm",
 "version": "1.0.0"}
```

You may then want to create a repository on GitHub to track your code changes. [Here](http://jellyjen.com/git_cheat_sheet) is a blog post I wrote on basic git commands. You can add a README, a license, and other helpful descriptions to make your module more user friendly.

Prefacing the name of the package with your username, will create a scoped package. This allows you to use short names that have already been used for other npm packages, or group related packages together (for example, modules you have created or modules made for a specific project)

In package names, scopes are preceded by an @ and followed by a / (for example, @angular/core). The module is required or installed in the same format `npm install @angular/core`

Npm follows SemVer (semantic versioning) conventions, which has a basic form of 0.0.0, each number referring to major.minor.patch versions. Major refers to a backwards incompatible version change. Minor and patch versions are backwards compatible, where minor adds functionality and patch fixes bugs. There are also other additional versioning conventions in SemVer. 

You can also add `"description"` (string) and `"keywords"` (array of strings) attributes to your package.json. This will help users discover your module through `npm search`

The main script file of a module is specified in the `"main"` attribute in package.json, also known as the entry point to your program. In this case the entry point will be an index.js file, which you will create.

The package.json will then look something like this:

```
{
 "name": "@jk-me/practicenpm",
  "version": "1.0.0",
  "description": "Removes all spaces from a string",
  "license": "MIT",
  "repository": "jk-me/practicenpm",
  "main": "index.js",
	keywords: [
    "practicenpm",
    "npm"
  ]
}
```

Examples of other package.json attributes (such as bin executables or dependencies) can be found here. [npmjs docs](https://docs.npmjs.com/files/package.json#main)

In this example, index.js is the main script of the package. When a user requires your npm package, the main module's export will be returned. A basic npm module can have the main script and not much else. 

```
//sample code in index.js
module.exports = function tiny(string) {
  if (typeof string !== "string") throw new TypeError("Tiny wants a string!");
  return string.replace(/\s/g, "");
};
```
This code error checks so that the function argument is a valid string, then uses regular expressions to remove spaces. In Javascript regex, `/\s/` refers to whitespace characters, and `g` refers to global/all matches. [W3Schools JS Regex ref](https://www.w3schools.com/js/js_regexp.asp)

`module.exports` is an object that contains functions. In this case it is a function, which is also a JS object. 

Publish your package using this command in terminal:

```npm publish --access=public```

For initial creation, npm will attempt to publish modules privately when using the `npm publish` command only, so you must specify that a package will be public. Publishing private modules requires a subscription on npmjs.

When successful your terminal output should show a plus sign with your package name and version. You will also receive an email from your npmjs account.

You can signal a major version update with `npm version major` in terminal.
Follow with `npm publish` to publish to the same public module.

The blog post I referenced also included some links to see info about npm packages:

[PackagePhobia](https://packagephobia.now.sh/ ) - see how large a module is before installing
[Unpkg](https://unpkg.com/) - see files and code inside module (similar to what git repo would look like) -> use format `unpkg.com/@scope/name@version/` to see full index



