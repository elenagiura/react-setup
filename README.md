# REACT SETTING UP ENVIRONMENT

## TABLE CONTENTS
* [WHY DO WE NEED TO SETUP ENVIRONMENT ?]
* [WHAT DO WE NEED TO SETUP ?]
* [PROJECT REPO]
* [CREATING PROJECT FOLDER STRUCTURE]
* [NPM]
* [WHAT IS PACKAGE.JSON FILE ?]
* [WHAT ARE DEPENDENCIES ?]
* [SETTING UP WEBPACK]
* [COMPILING HTML FILE TO DIST FOLDER]
* [SETTING UP DEV SERVER]
* [SETTING UP BABEL]
* [ADD CSS LOADER]
* [ADD GITIGNORE FILE]
* [SETTING UP REACT]
* [REACT STRUCTURE]

## WHY DO WE NEED TO SETUP ENVIRONMENT ?

- Any of MODERN JS apps need certain ENVIRONMENT
- That's because all of the ES6 features are STILL NOT fully supported, but also because we want to have CERTAIN PROJECT STRUCTURE
- Environment we need for REACT is the same as for any MODERN JS PROJECT

## WHAT DO WE NEED TO SETUP ?

- We need to setup few things before we start working:
  Project repo (github)
  NPM
  Webpack
  Babel

## PROJECT REPO

- We'll create a NEW REPO on github with README file, and then CLONE it locally
- Inside of this REPO will SETUP our APP STRUCTURE

## CREATING PROJECT FOLDER STRUCTURE

- For our files we'll need two FOLDERS: SRC and DIST
- SRC folder will contain our development files
- DIST folder will contain distribution files

## NPM

- NPM represents NODE PACKAGE MANAGER
- It's based on Node.js
- We need it in order to setup packages and extensions
- Before doing anything, we need to have NODE.JS installed on our computer
- To check if there is node installed do:
```
$ node -v
```
- Also we can check if NPM is present by doing:
```
$ npm -v
```
- To GET STARTED with NPM we need to navigate to project folder, and do:
```
$ npm init 
```
- It will automatically create package.json file, and terminal will WALK US through setup
- For most options we can just hit ENTER

## WHAT IS PACKAGE.JSON FILE ?

- package.json file is kind of map file, which describes our app
- It may contain app name, version, repository link and other thing
- In order to install single package with NPM we'll do:
```
$ npm install <package_name>
```
- However, when we install package like this it will exist ONLY LOCALY in our files, and DEPENDENCY WILL NOT EXIST
- This means, when somebody else get our files, they WILL NOT HAVE that PACKAGE, NOR INSTRUCTIONS that it should be installed
- So, if we want it to be saved we can do:
```
$ npm install --save <package_name>
```
- This will INSTALL PACKAGE, but also save it's version INFORMATION in DEPENDENCIES object in package.json
- If there is some package we want to INSTALL, but it's ONLY NEEDED in DEVELOPMENT version, not for APP to work, we can do it by doing:
```
$ npm install --save-dev <package_name>
```
- This will allow us to skip installing it later in PRODUCTION VERSION
- We can also install packages GLOBALLY, so it can be used anywhere on machine
- To do that we can do:
```
$ npm install -g package_name
```

## WHAT ARE DEPENDENCIES ?

- Dependencies are just data about different packages that OUR APP need to be installed
- Once we have it in package.json file we can do:
```
$ npm install
```
- It will install all packages listed in our dependencies object
- So, the next time when we share our app with someone, we DON'T NEED to share all installed packages, instead we just share app files with package.json file, and based on that they can install all PACKAGES needed

## SETTING UP WEBPACK

- We need Webpack in order to bundle our files
- Because modules are STILL NOT FULLY SUPPORTED, we use WEBPACK
- It will take main javascript file, then take all js files that we called from it, and join all those files in one, and add it to our dist folder
- Then we'll use that joined file
- Webpack can also bundle CSS files and IMAGES
- In order to INSTALL WEBPACK we'll do:
```
$ npm install webpack webpack-dev-server webpack-cli --save-dev
```
- Then we need to CREATE following file in our project folder:

  webpack.config.js 
  
- That's the file that will contain WEBPACK CONFIGURATION (which files to bundle and where to place it)
- Once we have base WEBPACK configuration, we need some COMMANDS in order to make it RUN
- To do that we will change our SCRIPTS object in package.json file
- We need script:

  "dev" : "webpack"

- This way it will COMPILE FILES, when we RUN IN TERMINAL:
```
$ npm run dev
```
- Now we can extend our SCRIPTS, instead of having it like this:

  "dev" : "webpack"

- We can have:

  "dev": "webpack --mode development",
  "build": "webpack --mode production"

- This way:
```
$ npm run dev  -  will create development version, it will finish faster, but it will not be compressed
$ npm run build  -  will create compressed version, once our files are ready
```

## COMPILING HTML FILE TO DIST FOLDER

- In order to AUTOMATICALLY compile HTML file to DIST folder we need to use WEBPACK PLUGIN called:

  html-webpack-plugin

- So we run:
```
$ npm install html-webpack-plugin --save-dev
```
- Now we need to adjust webpack.config file

## SETTING UP DEV SERVER

- Our app BUILDING works, but we have to do it MANUALY each time
- In order to do that we want to SETUP DEV SERVER
- We already installed webpack-dev-server
- We need to make some changes in our webpack.config file
- Also we need to add to our scripts:

  "start" : "webpack-dev-server --mode development --open"

## SETTING UP BABEL

- Webpack config file will also contains some LOADERS, which are there to BUNDLE CERTAIN TYPE of files
- One of those loaders is BABEL, which converts ES6 to ES5, in order to make it COMPATIBLE
- For MOST OF THE ES6 FEATURES it's not REQUIRED
- But we'll need it because REACT uses JSX, and we need BABEL to transpile it
- In order to setup BABEL we'll need to install a few things:
```
$ npm install @babel/core @babel/preset-env babel-loader --save-dev
```
- After that we need to adjust webpack.config file
- Also we need to add babel file called:

  babel.config.js 

- There are some things in ES6 that CAN'T be converted to ES5, that's why we need to use POLYFILLS
- Polyfills will create same functionality using ES5 code
- In order to install it we need to do:
```
$ npm install @babel/polyfill --save
```
## ADD CSS LOADER

- For CSS to be transpiled you will add ADDITIONAL STYLE LOADERS to webpack.config file

## ADD GITIGNORE FILE 

- Now that we have APP STRUCTURE READY, we want to add .gitignore file in order to AVOID PUSHING node_modules folder

## SETTING UP REACT

- In order to SET UP REACT we'll need to do:
```
$ npm install react react-dom --save
$ npm install @babel/preset-react --save-dev
```
- Also we need to add:

  "@babel/preset-react"  to presets in babel.config file

## REACT STRUCTURE

- In REACT we need to have one main javascript file which imports:
```
  import React from 'react';
  import ReactDOM from 'react-dom';
  import App from './App';
```
- And it should RENDER:
```
  ReactDOM.render(<App />, document.getElementById('app'));
```
- In this case App is MAIN COMPONENT, which then includes OTHER COMPONENTS

## CREATE REACT APP

- Also, there is an EASIER WAY to set REACT APP
  https://reactjs.org/docs/create-a-new-react-app.html
