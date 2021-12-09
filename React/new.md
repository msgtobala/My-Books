# React

* React is a library for building user interfaces. React heavily embraces the usage of components.
* React aims at the reusability of the components and in creating reactive components.
* It uses JSX with ES6 heavily.
* It uses declarative approach(As developer, we will not manipulate the DOM, React contolls manipulating the DOM).
* It is developed by Facebook

## What are Components?

Components are pieces of code that can be reused across the webpage.
For Example, Button, header, footer are kind of components. It mainly enforces reusability and maintainability.

Extension of React files: .js/.jsx

## What is JSX?

It is not related to React. It is a seperate feature. JSX is an extension for JS language syntax. It enables writing HTML inside of JS.
Full form: Javascript XML.
Note: It is not template language. JSX will be converted to broswer understandable code by Babel.

## Installing React

The Easiest way of installing React is using Create React App. This gives basic scaffold with pre-configured files. This saves the time of building the React from Scratch. Also it comes with Hot Reload.

### Prerequisites

* [Node JS](https://nodejs.org/en/).
* Run the command to install CRA `npm install -g create-react-app`.-g for global installation.
* cd {favorite_folder}
* Run `create-react-app <project_name>`

!!! Note:

1. project-name should not contain special characters except '_ and -'.
2. Should not contain capital letters.
3. Cannot contain leading or trailing spaces.
4. Should be meaningful
5. Cannot start with special characters.

Actually React uses ES6, JSS syntax which will be compiled by Babel and webpack to make it work.

## Dependencies of React

* React - The actual Framework.
* ReactDOM - Depedency used for interacting/communicating with React and real DOM.

## Folder Structure of CRA

* public - It is the static output folder. It contains the production ready code. Also it contains an index.html with id 'root' which will be refered in index.js
* index.js - Starting point/First file to be executed. Replaces id root with App.
* App.js - It holds the starting of actual React code.
* package.json - Holds information and dependency of the React project
* package.lock.json - Maintains all the dependency and internal dependency information that can be refered across different developers to avoid version clashes in the packages.
* reportWebVitals - File for capturing user experience
* setupTests.js - Basic setup for testing
