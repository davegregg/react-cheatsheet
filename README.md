<style>
summary {
  border-bottom: 4px dashed #02568B;
  outline: none;
  list-style-type: none;
}
summary::-webkit-details-marker {
  display: none;
}
details > summary:before {
    content: "＋";
    font-weight: bold;
    font-size: 2em;
    margin-right: 0.3em;
}
details[open] > summary:before {
    content: "－";
    font-weight: bold;
    font-size: 2em;
    margin-right: 0.3em;
}
details > summary:hover {
  border-bottom: 4px dashed #FDC54C;
  cursor: zoom-in;
}
details[open] > summary:hover {
  border-bottom: 4px dashed #FDC54C;
  cursor: zoom-out;
}
summary h1 {
  display: inline;
}
</style>

### Creating a component
+ If I want a component to be *static,* and I don't anything changed inside of it later:
  - I will write it as a **functional component**. Functional components only take inputs (props) and provide their output to the DOM.
+ If I want a component to be *smart* or if it needs to be interactive:
  - I will write it as a **class component**.

### Passing a value to a component (props)
+ If I have some unique input which I want each instance of this component to have, I will create a prop to pass into the JSX tag for that component (`<ComponentName propName="propValue" />`) and accepts in the props object inside my component definition (`props.propName` or `this.props.propName`).
+ If I need a prop to be a string, I will write it like this: `name="value"`.
+ If I need a prop to be the value of a variable: `name={variableName}`.
+ If I need a prop to be the anything other than a string literal, I will write it inside of curly braces. For an array literal, I would do: `name={[arrayValue1, arrayValue2, etc]}`. For an object literal, I would do `name={{ name1: value1 }}`. For a functional call, I would do `name={this.functionName()}`. To pass a callback function, I would do `callback={functionName}`

### Insert a value into JSX
+ If I want to put some arbitrary thing in my JSX, I will use curly braces to evaluate a JavaScript expression and output the result into the final HTML: `<div>{this.state.count}</div>` or `<div>{Math.random() + 10}</div>`.

### Handling state in a class component
+ If I want to set some **initial state**, I will add a constructor to my class component (pass in props), call `super` (pass in props), and set this.state to an object containing my initial state:
    ```js
    constructor (props) {
        super(props)
        this.state = {
            count: 0
        }
    }
    ```
+ If I want to change a state value entirely, I must call `this.setState`, passing in the new values as key-value pairs: `this.setState({ count: 10 })`.
+ If I want to change a state value based on its *previous* value, I need to pass a callback to `this.setState`, like so:
    ```js
    this.setState((state, props) => {
        return { count: state.count + 1 }
    })
    ```

### Handling events
+ If I want to create a callback for an event listener, I will define it as an arrow function assigned to a property (rather than normal method syntax). Instead of this:
    ```js
    handleIncrement (event) {
        // ...
    }
    ```
    Do this:
    ```js
    handleIncrement = (event) => {
        // ...
    }
    ```
+ OR... I will override the method with a *bound copy of itself* in the constructor:
    ```js
    constructor (props) {
        super(props)

        this.state = { count: 0 }

        this.handleIncrement = this.handleIncrement.bind(this)
    }
    ```

### Create React App

### Starting the application
  + To start an app with create-react-app type out "create-react-app" and a name for your application. IE 'npx create-react-app my-react-app'
  + If you haven't globally installed create-react-app, type "npx create-react-app foldername"
  + You must have the folder name be all lowercase, dashes (-) and underscores (_) are okay
  + To run it, type out "npm start" or "yarn start" depending on your package manager

### Looking through our files

  + gitignore - A file that contains a list of all the files git commands will ignore, important for larger projects with lots of dependancies. .gitignore allows you to make sure only the important files to your project are uploaded
  + package-lock.json - Automatically generated file which contains dependancy information. DON'T EDIT, its doing its own thing
  + package.json - This tells react what modules and dependencies that our react project is using. Run npm/yarn install when downloading a project or pulling down a project to make sure all the modules and files are up to date
  + readme.md - Contains descriptions of the scripts your react application can use, and helpful links to the react documentation


### Public Folder
  + favicon.ico - A very specifically formatted icon file for the small icon if your browser tabs when you're online
  + index.html - Where you can change the title of your page, it also contains the root div for displaying our React application. You generally will only edit the title for the browser. Internet browsers all expect to see an index.html for all websites.
  + manifest.json It stores the app's name, icons, and the url of the application
    src folder
  + robots.txt - List of files in your site/app for the bots or webscrapers to ignore

### SRC Folder
  + App.css - Where you'll put a lot of your CSS styling for apps. It contains the default styling for the basic create-react-app code In smaller applications feel free to use this file for all of your css needs.
  + index.js - This is where the <App /> is called, and where we put our routing for our react projects. This is where ReactDOM.render runs, and is the final step in the create-react-app before it is rendered in the browser
  + App.js - Your highest level component, and where you will import all highest level parts of your application. This is where the default react JSX is kept. 
  + serviceWorker.js - Runs in the background of a react project independantly of the react project itself.
  + App.test.js - Contains the code for some of the default tests , you won't be in this file very often in our program.

### Creating components in create-react-app and using them!
  + In the src folder create a new folder called "components" You are welcome to create as many different component folders inside this one, or in smaller scale applications you can
  + Components files should usually contain a SINGLE component, and should contain imports only important to that file.
  + All react components should start with the line "import React from 'react'"
  + At the bottom of the page you need to 'export default COMPONENTNAME'
  + Let's say we're importing a component named Gary to our App.js file. In App.js at the top of the page (imports should always go at the top of a React component) "import Gary from './components/Gary'" - We're importanting the Gary component from our Gary.js file which is located inside out components folder, in the Gary.js file.
  + IMPORTANT remember when you're importing files think of where they are relative to the file we're currently in. Use gitbash's/terminal's pathing to reach the file.
  + When importing things other than React, they are interchangeable variable names. If you are important a component named Jeff to your component you can call it Potato if you import it as 'import Potato from './Jeff'
  + After it is imported just call the component inside the return inside the parent div as a JSX expression like  <Gary />


# Test section

<details>
  <summary><h1>I want to create a component.</h1></summary>
  <br>
  <h3>If I want a component to be *static,* and I don't anything changed inside of it later:</h3>
  <ul>
    <li>I will write it as a **functional component**. Functional components only take inputs (props) and provide their output to the DOM.</li>
  </ul>
  <h3>If I want a component to be *smart* or if it needs to be interactive:</h3>
  <ul>
    <li>Then write it as a **class component**.</li>
  </ul>
</details>
