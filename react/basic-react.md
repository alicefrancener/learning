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