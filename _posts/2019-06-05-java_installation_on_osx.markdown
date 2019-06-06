---
layout: post
title:      "Java Installation on OSX"
date:       2019-06-06 02:20:04 +0000
permalink:  java_installation_on_osx
---


A quick post on installing Java versions and jenv, a Java environment manager on mac OS using Homebrew in terminal.

`brew help` or `brew cask help` to see help commands for Homebrew and Homebrew Cask, you may need to run `brew install brew-cask` 

`brew cask install java` - will install latest version of java, currently openjdk 12.0.1

Some programs need a specific java version to be able to run. I’m trying to attend a workshop on Samsung Wearable App development this week, which uses Samsung’s Tizen Studio IDE. Tizen Studio seems to require Java 8, 9 or OpenJDK 10. (OpenJDK is an open source version of Java, compared to the versions provided by Oracle)

try `brew search jdk` or `brew search java` to see if casks or brews are available to install for other java versions

`brew tap AdoptOpenJDK/openjdk` - I ended up using this command to tap for openjdk casks to install

`brew cask install adoptopenjdk10` to install openjdk10

Your installed Java versions should be in /Library/Java/JavaVirtualMachines 

`brew install jenv` - Install a Java environment manager to manage versions, like rvm (ruby version manager).

```
if which jenv > /dev/null; then eval "$(jenv init -)"; fi
```

Use the above line to initialize jenv in your terminal, then individually add each of your jenv versions.

```
jenv add  /Library/Java/JavaVirtualMachines/adoptopenjdk-10.jdk/Contents/Home
jenv add /Library/Java/JavaVirtualMachines/openjdk-12.0.1.jdk/Contents/Home
```

If you actually navigate to these files in finder (root directory, not in user!), your jdk versions may or may not have `/Contents/Home` files inside, but you must append it to your command in order to add the Java version to jenv.

`jenv versions` to see which Java versions you have installed.
`jenv global 10.0` to set a java version as global. Substitute 10.0 with a version from jenv versions list.
`jenv local 10.0` You can also navigate to a project specific directory and set a local default Java version. This will create a `.java-version` file at the project root

References: 
*[David Cai blog post](http://davidcai.github.io/blog/posts/install-multiple-jdk-on-mac/)
* [jenv docs](http://www.jenv.be/)
*[Dzone blog post](https://dzone.com/articles/install-openjdk-versions-on-the-mac)

