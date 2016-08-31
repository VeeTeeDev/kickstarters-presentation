# Package managers

## What are package managers:

> A package manager or package management system is a collection of software tools that automates the process of installing, upgrading, configuring, and removing computer programs for a computer's operating system in a consistent manner. (Wikipedia)

### Package managers in our life:

<dl>
  <dt>Linux</dt>
    <dd>Yum (Fedora), apt-get, ...</dd>
  <dt>Php</dt>
    <dd>Composer</dd>
  <dt>Ruby</dt>
    <dd>gem</dd>
  <dt>Python</dt>
    <dd>Pip, easy_install</dd>
  <dt>Node</dt>
    <dd>npm</dd>
  <dt>Mac osX</dt>
    <dd>brew</dd>
  ...
</dl>

### Front-end

Why would we use a package manager:
1. Easy to install, update,...
2. Dependency management
3. Keep source (control) small
4. ...

#### Front-end package managers:
Bower and npm are widely used and even some (or a lot) packages are hosted in both. Before we go in deeper in which one to use, let's talk about the advantages. The list above already gives us a clue. Without going in depth now, we don't want external resources become part of our source. So how can we use them without including them ? Both, Bower and npm, use a package/dependency file. This file tells us something about the configuration. It tells us which packages we need to install, before we can use/dev the application. By doing this, we don't include these dependencies in our source but only the config file(s). Since different environments need to able to add the 'same' dependencies, putting them inside our repository won't even work everywhere.     

## Node and npm
> In software development, Node.js is an open-source,
cross-platform runtime environment for developing server-side
 Web applications. Although Node.js is not a JavaScript framework,
 many of its basic modules are written in JavaScript,
 and developers can write new modules in JavaScript.
 The runtime environment interprets JavaScript using Google's V8 JavaScript engine. (wikipedia)

 NPM is nodes package manager and can be found at https://www.npmjs.com/.
 > npm is the package manager for JavaScript. Find, share, and reuse packages of code from hundreds of thousands of developers — and assemble them in powerful new ways. (npmjs.com)

NPM is widely used for javascript packages (and dependency) management. It's most important file is the package.json which contains the current package's general info and dependencies.

Node.js can be installed by downloading the installers available for Windows, Mac osX and Linux distributions.
You can install npm manually from https://registry.npmjs.org/npm/-/npm-{VERSION}.tgz.

To start an npm project just runtime
```
$ npm init
```
This will create a package.json file.
Installing a package
```
$ npm install {{packageName}}
```
To keep track of it, based on it's purpose you can
```
$ npm install {{packageName}} --save (--save-dev)  
```

When a package.json file is available you can run
```
$ npm install
```
to install all dependencies or
```
$ npm update
```
to trigger an update.
```
$ npm update {{packageName}}
```
to only update the selected package.


### Global vs Local.
When running npm install, the dependencies are installed locally. This means they are added to the local (in project) node_modules (if not configured) folder. Sometimes we need a package available global like other binaries. This can be done by adding the '-g' option
```
npm install {{packageName}} -g
```
Doing this will make the package/application available in your $PATH.


## Bower (and wiredep)
> Bower: A package manager for the web (bower.io)

Bower is a package manager for the web and is dependent on Node and NPM.

```
npm install bower -g
```

To start a bower project just
```
bower init
```
This will create the bower.json file that can keep track of all your dependecies.

You can install packages by
```
bower install {{packageName}}
```
You can use the --save to insert the package into your bower.json file.
```
bower install {{packageName}} --save
```
When a bower.json file is supplied, running
```
bower install
```
will install all dependencies or
```
bower update
```
to trigger an update.


## Npm and bower

The main difference between npm and Bower is the approach for installing package dependencies. npm installs dependencies for each package separately, and as a result makes a big package dependency tree (node_modules/grunt/node_modules/glob/node_modules/...), where there could be several version of the same package. For client-side JavaScript this is unacceptable: you can't add two different version for jQuery or any other library to a page. With Bower each package is installed once (jQuery will always be in the bower_components/jquery folder, regardless of how many packages depend on it) and in the case of a dependency conflict, Bower simply won't install the package incompatible with one that's already installed.

> In almost all cases, it's more appropriate to use Browserify and npm over Bower. It is simply a better packaging solution for front-end apps than Bower is. At Spotify, we use npm to package entire web modules (html, css, js) and it works very well. (Mattias Petter Johansson, Software Engineer at Spotify)
