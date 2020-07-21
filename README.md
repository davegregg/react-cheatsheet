<style>
summary {
  border-bottom: 3px dashed #02568B;
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

# Test section

<details>
  <summary><h1>I want to create a component</h1></summary>
  <h3>If I want a component to be *static,* and I don't anything changed inside of it later:</h3>
  <ul>
    <li>I will write it as a **functional component**. Functional components only take inputs (props) and provide their output to the DOM.</li>
  </ul>
  <h3>If I want a component to be *smart* or if it needs to be interactive:</h3>
  <ul>
    <li>Then write it as a **class component**.</li>
  </ul>
</details>
