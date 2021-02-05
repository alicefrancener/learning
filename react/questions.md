# Questions

- [Questions](#questions)
    - [What is a stateful component in React?](#what-is-a-stateful-component-in-react)
    - [What is a stateless component?](#what-is-a-stateless-component)

### What is a stateful component in React?

A stateful component is a component whose behavior depends on its state. This means that two separate instances of the component if given the same props will not necessarily render the same output, unlike pure function components.

```javascript
// Stateful class component
class App extends Component {
  constructor(props) {
    super(props)
    this.state = { count: 0 }
  }
  render() {
    // ...
  }
}

// Stateful function component
function App() {
  const [count, setCount] = useState(0)
  return // ...
}
```

Good to hear:
- Stateful components have internal state that they depend on.
- Stateful components are class components or function components that use stateful Hooks.
- Stateful components have their state initialized in the constructor or with `useState()`.

Font: [30 seconds of interviews]

### What is a stateless component?

A stateless component is a component whose behavior does not depend on its state. Stateless components can be either functional or class components. Stateless functional components are easier to maintain and test since they are guaranteed to produce the same output given the same props. Stateless functional components should be preferred when lifecycle hooks don't need to be used.

Good to hear: 
- Stateless components are independent of their state.
- Stateless components can be either class or functional components.
- Stateless functional components avoid the `this` keyword altogether.

Font: [30 seconds of interviews]


[30 seconds of interviews]: https://30secondsofinterviews.org/

