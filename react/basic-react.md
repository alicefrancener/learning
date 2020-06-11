# React

- Used to render the User Interface (UI) of web applications
- React uses a syntax extension of JavaScript called JSX that allows you to write HTML directly within JavaScript
- To write JavaScript directly within JSX you simply include the code you want to be treated as JavaScript within curly braces: `{ 'this is treated as JavaScript code' }`.
- Because JSX is not valid JavaScript, JSX code must be compiled into JavaScript. The transpiler Babel is a popular tool for this process.

## Exemplo básico

```jsx
const JSX = (
  <div>
    {/* isso é um comentário*/}
    <h1>This is a block of JSX</h1>
    <p>Here's a subtitle</p>
  </div>
);
```

## Render HTML Elements to the DOM

- With React, we can render this JSX directly to the HTML DOM using React's rendering API known as ReactDOM.
- ReactDOM offers a simple method to render React elements to the DOM which looks like this: `ReactDOM.render(componentToRender, targetNode)`, where the first argument is the React element or component that you want to render, and the second argument is the DOM node that you want to render the component to.
- `ReactDOM.render()` must be called after the JSX element declarations, just like how you must declare variables before using them.

```jsx
const JSX = (
  <div>
    <h1>Hello World</h1>
    <p>Lets render this to the DOM</p>
  </div>
);

ReactDOM.render(JSX, document.getElementById("challenge-node"));
```

## Define an HTML Class in JSX

- One difference between HTML and JSZ is that you can no longer use the word `class` to define HTML classes. This is because `class` is a reserved word in JavaScript. Instead, JSX uses `className`.

```jsx
const JSX = (
  <div className='myDiv'>
    <h1>Add a class to this div</h1>
  </div>
);
```

- In fact, the naming convention for all HTML attributes and event references in JSX become camelCase. For example, a click event in JSX is `onClick`, instead of `onclick`

## Self-Closing JSX Tags

- In HTML, almost all tags have both an opening and closing tag: `<div></div>`. However, there are special instances in HTML called "self-closing tags", or tags that don’t require both an opening and closing tag before another tag can start. For example the line-break tag can be written as `<br>` or as `<br />`, but should never be written as `<br></br>`, since it doesn't contain any content.
- In JSX, the rules are a little different. *Any JSX element can be written with a self-closing tag*, and **every element must be closed**. The line-break tag, for example, must always be written as `<br />` in order to be valid JSX that can be transpiled. A `<div>`, on the other hand, can be written as `<div />` or `<div></div>`. The difference is that in the first syntax version there is no way to include anything in the `<div />`.

## Create a React Component

There are two ways to create a React component:
- The first way is to use a JavaScript function. Defining a component in this way creates a **stateless functional component**. 
- React requires your function name to begin with a capital letter. 

```jsx
// example of a stateless functional component that assigns an HTML class in JSX
const DemoComponent = function() {
  return (
    <div className='customClass' />
  );
};
```

- The other way to define a React component is with the ES6 class syntax

```jsx
class Kitten extends React.Component {
  constructor(props) {
    super(props);
  }

  render() {
    return (
      <h1>Hi</h1>
    );
  }
}
```

## Create a Component with Composition

- Imagine you are building an App and have created three components, a Navbar, Dashboard, and Footer.
- To compose these components together, you could create an App parent component which renders each of these three components as children. To render a component as a child in a React component, you include the component name written as a custom HTML tag in the JSX. 

```jsx
return (
 <App>
  <Navbar />
  <Dashboard />
  <Footer />
 </App>
)
```

- When React encounters a custom HTML tag that references another component (a component name wrapped in `< />` like in this example), it renders the markup for that component in the location of the tag. 

## Render a Class Component to the DOM

- React components are passed into `ReactDOM.render()` a little differently than JSX elements. 
- For JSX elements, you pass in the name of the element that you want to render. 
- However, for React components, you need to use the same syntax as if you were rendering a nested component, for example `ReactDOM.render(<ComponentToRender />, targetNode)`. You use this syntax for both ES6 class components and functional components


## Pass Props to a Stateless Functional Component

- You can pass props, or properties, to child components
- You use custom HTML attributes created by you and supported by React to be passed to the component
- It is standard to call this value `props` and when dealing with stateless functional components, you basically consider it as an argument to a function which returns JSX

```jsx
// nesse caso criei prop.date com a data atual e passei para CurrentDate

const CurrentDate = (props) => {
  return (
    <div>
      <p>The current date is: {props.date}</p>
    </div>
  );
};

class Calendar extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h3>What date is it?</h3>
        <CurrentDate date={Date()} />
      </div>
    );
  }
};

```

## Use Default Props

- React also has an option to set default props
- This allows you to specify what a prop value should be if no value is explicitly provided

```jsx
const ShoppingCart = (props) => {
  return (
    <div>
      <h1>Shopping Cart Component</h1>
    </div>
  )
};

ShoppingCart.defaultProps = {items: 0}
```

## Override Default Props

```jsx
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
}

Items.defaultProps = {
  quantity: 0
}

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items quantity={10}/>
  }
};
```

## Use PropTypes to Define the Props You Expect

- React provides useful type-checking features to verify that components receive props of the correct type
- It's considered a best practice to set propTypes when you know the type of a prop ahead of time
- Note: As of React v15.5.0, PropTypes is imported independently from React, like this: `import PropTypes from 'prop-types';`

```jsx
const Items = (props) => {
  return <h1>Current Quantity of Items in Cart: {props.quantity}</h1>
};

Items.propTypes = { 
  quantity: PropTypes.number.isRequired
  };
Items.defaultProps = {
  quantity: 0
  };

class ShoppingCart extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return <Items />
  }
};
```

# Access Props Using this.props

- But what if the child component that you're passing a prop to is an ES6 class component, rather than a stateless functional component? - Anytime you refer to a class component within itself, you use the `this` keyword. For example, if an ES6 class component has a `prop` called `data`, you write `{this.props.data}` in JSX.

```jsx
class ReturnTempPassword extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
        <div>
            <p>Your temporary password is: <strong>{this.props.tempPassword}</strong></p>
        </div>
    );
  }
};

class ResetPassword extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
        <div>
          <h2>Reset Password</h2>
          <h3>We've generated a new temporary password for you.</h3>
          <h3>Please reset this password from your account settings ASAP.</h3>
            <ReturnTempPassword tempPassword="temporary123"/>
        </div>
    );
  }
};
```

***

Fonte: [Freecodecamp - React](https://www.freecodecamp.org/learn/front-end-libraries/react)
