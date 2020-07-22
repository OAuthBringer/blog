# "Would you like to develop an app?" - React Components in 3 Core Concepts 

I've been getting a lot of questions about building React applications recently so I decided to jot down some core concepts I've learned over the last few years while working on production React Applications. What makes React powerful (if not unique) is that it consolidates UI elements and logic into a single coherent abstraction - The Component.  The component is the fundamental unit of work in React and if you don't understand it, well... you don't understand React.

In this article I will cover 3 main concepts to help you understand Components and how they behave in the wild:

1. Component lifecycles.
1. Component state
1. Component properties (AKA props).

Because showing is often better than telling, I've written working examples of all the [code snippets](https://codepen.io/neolytics/pen/abdXRvm) I share in this article so you can follow along or poke around.

Let's get to it.

## Components and Lifecycles

As I mentioned above. The component is a core concept in React, arguably *the core* concept.  Simply put [a component is any function that returns a JSX element](https://reactjs.org/docs/introducing-jsx.html) *while react is in scope*.  If you're not familiar with JSX it's not a concept unique to React, other popular frameworks such as Vue utilize similar approaches.

```
import React from 'react' // React must be in scope

const Header = () => <h2>I am a Header Component</h2>
const Content = () => <div>I am a Content Component</div>
const Blog = () => <div>I am a Blog component that implements the Header and Content components<Header/><Content/></div>
```

Each example above is a valid component, the `Header` and `Content` components simply return HTML elements while the `Blog` component returns both HTML elements and React Components, illustrating how components can be reused witin other components.

Because React is a [Single Page Application](https://en.wikipedia.org/wiki/Single-page_application) (SPA) framework, components are conditionally rendered or "mounted" and "unmounted" depending on the *state* of your application.  This means that a component has a natural ["lifecycle"](https://reactjs.org/docs/state-and-lifecycle.html).  The topic of the "component lifecycle" is one of the most important in react and an in depth discussion is beyond the scope of this article.

Concisely, within the scope of the component's life a developer may perform operations:

1. Before a component mounts
1. When a component mounts
1. While a component is already mounted
1. When a component unmounts.

When a component mounts, it "renders" content based on its *state* and any associated logic.

You can mount and unmount components in the [companion codepen](https://codepen.io/neolytics/pen/abdXRvm) by toggling the available buttons under the "Lifecycle and State Examples" butttons.

## Components and State

Intimately connected to the concept of the "component lifecycle" is the issue of "state", or any information that is persisted during the lifetime of a component.

React components have built in mechanisms for managing state, prior to React 16.8 state was managed via the implementation of Class based components that extended the core `React.Component` definition. 

Below is an example of a class-based stateful component:

```
import React, {Component} from 'react';

class MyClassComponent extends Component {
  state = {
    loading: false
  }

  // React built in lifecycle method
  componentDidMount = () => {
    this.setState({loading: true})
     setTimeout(()=>{
      this.setState({loading: false})
    }, 500)
  }


  render = () => {
    const { loading } = this.state;
    const content = loading ? "I am loading as a class!" : "I, a class, have loaded!"
    return <h2>{content}</h2>
  }
}
```

Class components are quite common, especially if you are encountering React in the context of work, but they will likely fall out of favor and are (arguably) no longer a best practice because of recent updates to React.


In React 16.8 the [hooks](https://reactjs.org/docs/hooks-intro.html) `useState` and `useEffect` were introduced as alternatives to managing component state and component lifecycle operations illustrated in the example above.  Hooks are another powerful concept worth exploring, but today I will just illustrate how to write a "functional" component implementing *similar* logic to the class component demonstrated above using hooks.

```
import React, {useState, useEffect} from 'React';

const MyFunctionalComponent = () => {
  // set default value of loading to `false`
  const [loading, setLoading] = useState(false)
  
  useEffect(()=>{
    setLoading(true)
    setTimeout(()=>{
      setLoading(false)
    }, 500)
  }, [])
  
  const content = loading ? "I am loading as a function!" : "I, a function, have loaded!"

  return <h2>{content}</h2>
```

The functional component requires less boilerplate to write and implements the same "loading" functionality as the class based component. Whether or not one is easier to understand over the other is a matter of debate (and probably just preference) as they both require some implicit knowledge of React and it's class method API or the newer hooks API and its nuances.

In practical terms the major advantage I've found of using functional components is convenience.  Functional components are just easier to write and I usually start with just the display elements of a component before adding in logic and state.  Prior to react 16.8 if you began writing a component as a function and later determined it needed state you'd either need to wrap it in a container component or refactor it into a class (which is annoying).

If you didn't catch the link earlier, for convenience I've thrown together a quick [codepen](https://codepen.io/neolytics/pen/abdXRvm) that implements the two component types above.

## Components and Props

[Props or "properties"](https://reactjs.org/docs/components-and-props.html) are just params that you pass to a Component. That's really it, there's no real magic here, but this is something I've seen newcomers to React struggle with.  I suspect part if this is related to fuzziness around just exactly what a "component" is and how JSX syntax is used in React..

### Props are Objects

Prop values can be of any type, but props are always represented as objects (i.e. `{key: value}`). Because props can be any type I highly recommend becoming familiar with and using [prop-types](https://www.npmjs.com/package/prop-types) when you are defining components, or even better explicitly defining your named props by using [object destructuring syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment).

The example below is conveys the concept:

```
// Destructured
const DestructuredHeader = ({ title }) => <h2>{title}</h2>
const PropHeader = (props) => <h2>{props.title}</h2>
```

The two components are identical in terms of output, but their definitions are quite different.  `DestructuredHeader` *only* accepts a `title` key/value pair  while the `PropHeader` is accepting *any* key/value pair passed into it as `props`.

For the sake of your sanity and anyone who comes after you I advocate that you explicitly define the props your components take using destructuring syntax.  Not only does it make your component more readible, it also makes setting default values quite easy, which has a profund impact on the overall stability and qualitty of your components.

For Example:

```
const DestructuredHeaderWithDefault = ({title = "A Default Title"}) => <h2>{title}</h2>
```

### "Composing" Specialized Components with Props

Consder the example below where I've used [object destructuring syntax](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Destructuring_assignment) to explicitly define the props `title` (a string), and `onClick` (a function) and have set some default values.

```
// A generic button component, useful for.... butttony things.
const Button = ({
  title = "Click",
  onClick = () => console.log({ clicked: true }),
}) => (
  <div>
    <button onClick={onClick}>
      {title}
    </button>
  </div>
);
```

If I wanted to take that same `Button` component and [compose](https://reactjs.org/docs/composition-vs-inheritance.html) a new "specialized" `SubmitButton` component I could JSX syntax to pass in props as so:

```
const SubmitButton = () => <Button title="A Specialized Component defined in JSX syntax"/>
```

However, I could also define the component as a function with an object as the param (i.e. props) and the result would be the same.

```
const SubmitButton = () => Button({title: "A Specialized Component defined in function syntax"})
```

The submit button examples above convey 2 important points:

1. You can easily make specialized components from another component simply by using props.
1. JSX syntax is just syntactic sugar for a particular type of function (A React Component in this case) that takes an Object as it's only parameter.

Basic implementations of these components are available in the [companion codepen](https://codepen.io/neolytics/pen/abdXRvm) "Props and Composition examples" section.

## Recap

1. Components are just functions (or classes).
1. Components have a lifecycles and can be *stateful* or *stateless*
1. Components take params called `props`. Props are named and can be of any type (including other components).

## Tips

1. Whether you write class or functional components aim to keep them narrowly scoped and as stateless as you can. Ideally any single component should have 1 explicit responsibility.  In general the overall "reusability" of a component is inversely proportional to the amount of state managed and the lines of code it takes to implement.
1. Props are just params, don't overthink it!
1. Explicitly name your props and set reasonable default values

## Closing Thoughts

I consider the concepts outlined here as *foundational* to a working understanding of React.  In my profiessional experience with React I have found that nearly every head scratching moment I've encountered boils down to the interplay between state and the component lifecycle.  Without an understanding of these principles the behavior of React applications can be extremely challenging to Reason about, and these are core ideas that have only really come to me through "trial by fire".


To build on these foundational concepts I suggest a few questions to mull over:
- How do you manage state that needs to persist *beyond* the lifecycle of a component?
- Aside from classes and functions, are there other "types" of components?

If you've made it this far, thanks for reading. My goal here is to provide what insight I can into a difficult subject.  If you have any comments, corrections, or suggestions please let me know.  If you found this valuable I am working on a companion piece on working with React w/ Redux so stay tuned.


