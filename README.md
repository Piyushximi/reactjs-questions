# React Interview Questions & Answers

---


### Table of Contents


| No. | Questions | No | Questions |
| ----- | ------------------- | ---- | ------------------- |
|     | **Core React**     | 
| 1   | [What is React?](#what-is-react) | 16  | [What is Controlled component and uncontrolled Component](#16) |
| 2   | [What are the major features of React?](#what-are-the-major-features-of-react) | 17 | [What is reconciliation in ReactJS?](#17) |
| 3   | [What is JSX?](#what-is-jsx)  | 18 | [What are Pure Components?](#18) |
| 4   | [What do you understand by Virtual DOM](#what-do-you-understand-by-virtual-dom) | 19 | [What is Diffing and Prop Drilling](#19)|
| 5   | [What is Higher order components(HOC)](#5) | 20 | [What are the differences between a class component and functional component?](#20)|
| 6   | [Differentiate between stateful and stateless components.](#6) | 21 | [Component Composition](#21) |
| 7   | [What is the difference between state and props?](#7) | 22 | [What is forwardRef](#22)|
| 8   | [What is setState()](#8) | 23 | [What is Hooks](#23) |
| 9   | [What is React Lifecycle](#9) | 24 | [What is super / createPortal / createRoot](#24)|
| 10   | [What is React Fragments, and when should you use them?](#10) | 25 | |
| 11   | [What is Keys in React? lists and why they are essential.](#11) |
| 12  | [What are error boundaries in React](#12) |
| 13  | [What is Profiler](#13) | 28 | [What are the differences between useEffect and useLayoutEffect hooks?](#28) |
| 14  | [What is the Optimization ways in react](#14) | 29 | [What is Babel. or Transpiler ](#29)|
| 15  | [What is Ref](#15) | 30 | [What is Webpack.](#30) |







## Core React

1.  ### What is React?

    React is an open-source JavaScript frontend UI library. It is used to create reusable UI components for Building user interface for web and mobile app. It is used by Facebook, Instagram and many more web apps

* React is used to build single page applications.
* React allows us to create reusable UI components. and these components display data as it changes over time.

    **[⬆ Back to Top](#table-of-contents)**

2.  ### What are the major features of React?

    The major features of React are:

    - It is easy to Learn and USE
    - We can Create Dynamic Web Applications easily
    - We can create Reusable Components
    - It helps us to Performance Enhancement.
    - Uses **JSX** syntax, a syntax extension of JS that allows developers to write HTML in their JS code.
    - It uses **Virtual DOM** instead of Real DOM considering that Real DOM manipulations are expensive.
    - Supports **server-side rendering** which is useful for Search Engine Optimizations(SEO).
    - Follows **Unidirectional or one-way** data flow or data binding.
    - Uses **reusable/composable** UI components to develop the view.

    #### Disadvantage
    - We get Frequent updates and development. So it becomes difficult to implement new things immediately.
    - Its library is very large and takes time to understand

    **[⬆ Back to Top](#table-of-contents)**

3.  ### What is JSX?
       JSX stands for javaScript XML. It is simply a syntax extension of JavaScript. It allows us to directly write HTML in React (within JavaScript code). It is faster than normal JavaScript as it performs optimizations while translating to regular JavaScript.
    
    Basically it just provides the syntactic sugar for the `React.createElement(type, props, ...children)` function, giving us expressiveness of JavaScript along with HTML like template syntax.

    In the example below, the text inside `<h1>` tag is returned as JavaScript function to the render function.

    ```jsx harmony
    export default function App() {
      return (
          <h1 className="greeting">{"Hello, this is a JSX Code!"}</h1>
      );
    }
    ```
    If you don't use JSX syntax then the respective JavaScript code should be written as below,

    ```javascript
    import { createElement } from 'react';

    export default function App() {
      return createElement(
        'h1',
        { className: 'greeting' },
        'Hello, this is a JSX Code!'
      );
    }
    ```

     <details><summary><b>See Class</b></summary>
     <p>

    ```jsx harmony
    class App extends React.Component {
      render() {
        return (
            <h1 className="greeting">{"Hello, this is a JSX Code!"}</h1>
        );
      }
    }
    ```

     </p>
     </details>

    **Note:** JSX is stricter than HTML

    **[⬆ Back to Top](#table-of-contents)**
4. ### What do you understand by Virtual DOM
   A virtual DOM is a lightweight JavaScript object which is just a copy of the real DOM.The virtual DOM (VDOM) is an in-memory representation of Real DOM.
   - it updates faster than real DOM
   -  We Can’t directly update HTML.
   -  It Updates the JSX if element updates.
   -  There is no memory wastage in case of virtual DOM

    **React maintains two Virtual DOM at each time, one contains the updated Virtual DOM and one which is just the pre-update version of this updated Virtual DOM.**
       
     | Virtual DOM                                                                                       | Real DOM                                                                                                                            |
     | ------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------- |
    | It is a lightweight copy of the original DOM | It is a tree representation of HTML elements |
    |It is maintained by JavaScript libraries|It is maintained by the browser after parsing HTML elements|
    |   After manipulation it only re-renders changed elements|After manipulation, it re-render the entire DOM|
    |Updates are lightweight|Updates are heavyweight|
    |Performance is fast and UX is optimised|Performance is slow and the UX quality is low|
    |Highly efficient as it performs batch updates|Less efficient due to re-rendering of DOM after each update|

    **[⬆ Back to Top](#table-of-contents)**
    ### 5
      ### What is Higher order components

    Higher Order Component is an advanced way of reusing the component logic In simple terms, it takes the original component and returns enhanced component. Its a very clever way to follow the DRY (Dont Repeat Yourself) motto and cut down on code clutter.
    - Easy handling of code
    - Code reuse so you don’t have to copy the same login in every component
    - logic and bootstrap abstraction
    - State abstraction and manipulation
    - Props manipulation

    ```javascript
    const withLogger = (WrappedComponent) => {
        const EnhancedComponent = (props) => {
            console.log('Component props:', props);
            return <WrappedComponent {...props} />;
        };
        return EnhancedComponent;
    };
    // Usage
    const MyComponent = (props) => {
        // Component logic here
    };
    export default withLogger(MyComponent);
    
    ```
    **[⬆ Back to Top](#table-of-contents)**
### 6
### Differentiate between stateful and stateless components. 
- A stateless component can render props, whereas a stateful component can render both props and state.
- If we go through the syntax; In stateless components, the props are displayed like `{props.name}` but in stateful components, the props and state are rendered like `{this.props.name}` and `{this.state.name}` respectively.
- Stateful components can use react life cycle hooks but stateless components cannot use react life cycle hooks.
- In some of the stateful components, the data keeps changing, for example, watching the cricket score etc. In some component, the data remains the same, for example, showing the static data.

| Stateful Component | Stateless Component |
| ----- | ------------------- |
| A component that manages the state in class-based with state or functional with useState.| A component that has no internal state management in it called stateless. it Calculates the internal state of the components |
| Have authority to change the state | Do not have the authority to change state |
| And it Contains the knowledge of past, current and possible future changes in state | Stateless components can not use the react life cycle hooks |
| Stateless components notify them about the requirement of the state change, then they send down the props to them. | They receive the props from the Stateful components and treat them as callback functions. |

**[⬆ Back to Top](#table-of-contents)**
### 7
### What is the difference between state and props?

1. **State:** The state is a built-in React object that is used to contain data or information about the component. A component’s state can change over time; whenever it changes, the component re-renders. The change in state can happen as a response to user action or system-generated events and these changes determine the behavior of the component and how it will render.
2. **Props:** Props mean properties,We use props in React to pass data from one component to another (from a parent component to a child component(s)). It is basically a communication channel between components. They are useful when you want the flow of data in your app to be dynamic.

#### Diffrence
1. Props are used to pass data from a parent component to a child component, while state is used to manage data within a component.
2. Props are immutable and cannot be changed within a component, while state is mutable and can be updated using the setState function.
3. Props can be used to customize the behavior or appearance of a component, while state is used to keep track of information that can change over time.

**[⬆ Back to Top](#table-of-contents)**
### 8
### What is setState()
`setState()` allows you to change state in a React class component. and `setState()` tell React that this component and its children need to be re-rendered with the updated state. This is the primary method you should use to update the UI.

```javascript
// (prevState) which will provide you a snapshot from the previous state.
    this.setState(prevState =>{
        return{
            ...prevState,
	        counter : prevState.counter + 1
	   }
	})
// But if the change does not rely on any other previous value, then a shorter version is recommended
this.setState({counter : 2})
```

**[⬆ Back to Top](#table-of-contents)**
### 9
### What is React Lifecycle
The React LifeCycle is mainly classified into three stages  `Mounting`, `Updating`, and `Unmounting`. First is the mounting where we create a react component and insert it into the DOM. Second is updating where the state of the component is updated and the last is unmounting where the component is unmounted from the DOM.
- **Mounting:** - Mounting is the first stage in which our React Component is created and inserted into the DOM.
    * **constructor():** Constructor is the first method that gets called before the component mounted which helps to initialize the component State.
    * **Constructor:** Constructor is a method that is used to create and initialize an object created with a class and this must be unique within a particular class.
    * getDerivedStateFromProps()
    * **render():** The render() method is responsible for generating the component's virtual DOM representation based on its current props and state.
    * **componentDidMount()** - Executed on the client side only after the first render.
- **Updating:** - Updating is the stage when the state of a component is updated
    * **componentDidUpdate ()**- Called immediately after rendering takes place.
- **Unmounting:** -
    * **componentWillUnmount**  - Called after the component is unmounted from the DOM. It is used to clear up the memory spaces.

**[⬆ Back to Top](#table-of-contents)**
### 10
### What is React Fragments, and when should you use them?
React Fragments allow us to group multiple components without introducing an additional parent element in the DOM. Fragment are useful when you need to return multiple elements from a component's render method.

**WHEN SHOULD WE USE THE REACT FRAGMENTS:**

You should use the React Fragment when you want to add a parent element to fulfil the JSX syntax, but without introducing an extra node to the DOM. After compilation, the fragment component does not make it to the DOM—only the children element do
```javascript
import React, { Fragment } from 'react';

const MyComponent = () => {
 return (
  <Fragment>
   <h1>Title</h1>
   <p>Paragraph 1</p>
   <p>Paragraph 2</p>
  </Fragment>
 );
};
```

**[⬆ Back to Top](#table-of-contents)**
### 11
### What is Keys in React? lists and why they are essential.
A `key` is a special attribute you **should** include when mapping over arrays to render data. _Key_ prop helps React identify which items have changed, are added, or are removed.

Keys should be unique among its siblings. Most often we use ID from our data as _key_:

 ```jsx harmony
const todoItems = todos.map((todo) => <li key={todo.id}>{todo.text}</li>);
 ```
 When you don't have stable IDs for rendered items, you may use the item _index_ as a _key_ as a last resort:

```jsx harmony
    const todoItems = todos.map((todo, index) => (
      <li key={index}>{todo.text}</li>
    ));
```
**Note:**
1. Using _indexes_ for _keys_ is **not recommended** if the order of items may change. This can negatively impact performance and may cause issues with component state.
2. If you extract list item as separate component then apply _keys_ on list component instead of `li` tag.
3. There will be a warning message in the console if the `key` prop is not present on list items.
4. The key attribute accepts either string or number and internally convert it as string type.

**[⬆ Back to Top](#table-of-contents)**

### 12
### What are error boundaries in React
Error Boundaries basically provide some sort of boundaries or checks on errors, Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed.

**Reason to Use:**

Suppose there is an error in JavaScript inside component then it used to corrupt React’s internal state. Error boundaries help in removing these errors and display a Fallback UI instead(Which means a display of an error that something broke in the code).

```javascript
// A class component becomes an error boundary if it defines either (or both) of
// the lifecycle methods static getDerivedStateFromError() or componentDidCatch(). 
class ErrorBoundary extends React.Component {
    constructor(props) {
    super(props);
    this.state = { hasError: false };
  }
    static getDerivedStateFromError(error) {
        // Update state so the next render will show the fallback UI.
        return { hasError: true };
    }
    componentDidCatch(error, errorInfo) {
        // You can also log the error to an error reporting service
        logErrorToMyService(error, errorInfo);
      }
}
```

**[⬆ Back to Top](#table-of-contents)**
### 13
### What is Profiler
It measures how many times the react application renders. It helps to identify the part of the application which are slow so that the developer can optimize it for better performance. It is lightweight and no third-party dependency is required. The profiler takes two props one is an id which is a String and another one is onRender which is a callback function.

Profiler lets you measure rendering performance of a React tree programmatically.

```javascript
function onRender(id, phase, actualDuration, baseDuration, startTime, commitTime) {
  // Aggregate or log render timings...
}

<Profiler id="App" onRender={onRender}>
  <App />
</Profiler>
```
* id: A string identifying the part of the UI you are measuring.
* onRender: An onRender callback that React calls every time components within the profiled tree update. It receives information about what was rendered and how much time it took.

**[⬆ Back to Top](#table-of-contents)**
### 14
### What is the Optimization ways in react
Minimizing the number of re-renders is an important optimization technique in React that involves reducing the amount of unnecessary updates to the DOM caused by changes in state or props. Re-rendering a component can be an expensive operation, especially if it involves updating many child components.

* Use the production build
* Use React.Fragments to Avoid Additional HTML Element Wrappers
* Avoid Inline Function Definition in the Render Function.: - Since functions are objects in `JavaScript ({} !== {})`, so arrow function will create a new instance of the function on each render if it's used in a JSX property. This might create a lot of work for the garbage collector.

**[⬆ Back to Top](#table-of-contents)**
### 15
### What is Ref
Refs is the short hand for References in React Refs are a function provided by React to access the DOM element and the React element that you might have created on your own. They are used in cases where we want to change the value of a child component, without making use of props and all. They have wide functionality as we can use callbacks with them.

It is an attribute which helps to store a reference to a particular React element or component, which will be returned by the components render configuration function

**There are a few good use cases for refs:**
* Managing focus, text selection, or media playback.
* Triggering imperative animations.
* Integrating with third-party DOM libraries.

```javascript
//For class component:- in constructor
this.textInput = React.createRef();
//in render
<input type="text"ref={this.textInput} />
//For function component:- hooks
const textInput = useRef(null);
//in return
<input ref={textInput} type="text" />
```

**[⬆ Back to Top](#table-of-contents)**

### 16
### What is Controlled component and uncontrolled Component
1. **Controlled Components:** In React, Controlled Components are those in which form’s data is handled by the component’s state. It takes its current value through props and makes changes through callbacks like onClick,onChange, etc. A parent component manages its own state and passes the new values as props to the controlled component. You could also call this a "dumb component".

For example, to write all the names in uppercase letters, we use handleChange as below,

```javascript
handleChange(event) {
    this.setState({value: event.target.value.toUpperCase()})
}
```
**You can use the controlled component when you create**
* Form validation so you always need to know the value of the input when typing to check if it’s a valid character or not!
* Disable the submit button unless all fields have valid data
* If you have a specific format like the credit card input

2. **Uncontrolled Components** are the components that are not controlled by the React state and are handled by the DOM (Document Object Model). So in order to access any value that has been entered we take the help of refs. Ref to find its current value when you need it. This is a bit more like traditional HTML.

In the below UserProfile component, the `name` input is accessed using ref.

```jsx harmony
    class UserProfile extends React.Component {
      constructor(props) {
        super(props);
        this.handleSubmit = this.handleSubmit.bind(this);
        this.input = React.createRef();
      }

      handleSubmit(event) {
        alert("A name was submitted: " + this.input.current.value);
        event.preventDefault();
      }

      render() {
        return (
          <form onSubmit={this.handleSubmit}>
            <label>
              {"Name:"}
              <input type="text" ref={this.input} />
            </label>
            <input type="submit" value="Submit" />
          </form>
        );
      }
    }
```

**[⬆ Back to Top](#table-of-contents)**

### 17
### What is reconciliation in ReactJS?
The reconciliation process makes React work faster. Reconciliation is the process through which React updates the Browser DOM.

* Reconciliation is the process by which React updates the UI to reflect changes in the component state. The reconciliation algorithm is the set of rules that React uses to determine how to update the UI in the most efficient way possible.
* React uses a virtual DOM (Document Object Model) to update the UI. The virtual DOM is a lightweight in-memory representation of the real DOM, which allows React to make changes to the UI without manipulating the actual DOM. This makes updates faster, as changing the virtual DOM is less expensive than changing the real DOM.
* `The reconciliation algorithm works by comparing the current virtual DOM tree to the updated virtual DOM tree, and making the minimum number of changes necessary to bring the virtual DOM in line with the updated state`.

**Important concepts behind the working of the Reconciliation process are:**
1. Virtual DOM
	* React renders JSX components to the Browser DOM, but keeps a copy of the actual DOM to itself. This copy is the Virtual DOM. We can think of it as the twin brother of the real or Browser DOM. The following actions take place in React:
	* React stores a copy of Browser DOM which is called Virtual DOM.
	* When we make changes or add data, React creates a new Virtual DOM and compares it with the previous one.
	* Comparison is done by Diffing Algorithm. The cool fact is all these comparisons take place in the memory and nothing is yet changed in the Browser.
2. Diffing Algorithm
	* How does this Virtual DOM compare itself to its previous version? This is where the Diffing Algorithm comes into play

**[⬆ Back to Top](#table-of-contents)**
### 18
### What are Pure Components?
Pure Components in React are the components which do not re-renders when the value of state and props has been updated with the same values.
If the value of the previous state or props and the new state or props is the same, the component is not re-rendered. Since Pure Components restricts the re-rendering when there is no use of re-rendering of the component. Pure Components are Class Components which extends React.PureComponent. 

Pure components are the components which render the same output for the same state and props. In function components, you can achieve these pure components through memoized `React.memo()` API wrapping around the component. This API prevents unnecessary re-renders by comparing the previous props and new props using shallow comparison. So it will be helpful for performance optimizations. 
    
But at the same time, it won't compare the previous state with the current state because function component itself prevents the unnecessary rendering by default when you set the same state again.

The syntactic representation of memoized components looks like below,

```jsx
const MemoizedComponent = memo(SomeComponent, arePropsEqual?);
```

Below is the example of how child component(i.e., EmployeeProfile) prevents re-renders for the same props passed by parent component(i.e.,EmployeeRegForm).

```jsx
import { memo, useState } from 'react';

const EmployeeProfile = memo(function EmployeeProfile({ name, email }) {
  return (<>
        <p>Name:{name}</p>
        <p>Email: {email}</p>
        </>);
});
export default function EmployeeRegForm() {
  const [name, setName] = useState('');
  const [email, setEmail] = useState('');
  return (
    <>
      <label>
        Name: <input value={name} onChange={e => setName(e.target.value)} />
      </label>
      <label>
        Email: <input value={email} onChange={e => setEmail(e.target.value)} />
      </label>
      <hr/>
      <EmployeeProfile name={name}/>
    </>
  );
}
```
In the above code, the email prop has not been passed to child component. So there won't be any re-renders for email prop change.

In class components, the components extending _`React.PureComponent`_ instead of  _`React.Component`_ become the pure components. When props or state changes, _PureComponent_ will do a shallow comparison on both props and state by invoking `shouldComponentUpdate()` lifecycle method. 

**Note:** `React.memo()` is a higher-order component.

**[⬆ Back to Top](#table-of-contents)**


### 19
### What is Diffing and Prop drilling
* DOM Diffing:  Whenever there is a change in the state of the UI elements, a new virtual DOM is created. Then the new virtual DOM and the previous virtual DOM are compared with each other. This comparing is called DOM diffing.  The intention is to perform minimal operations on the real DOM, hence after diffing, the best way to update the real DOM is calculated, leading to an efficient update of the UI.
* Prop Drilling: Prop Drilling is the process by which you pass data from one component of the React Component tree to another by going through other components that do not need the data but only help in passing it around.
    * It is not a good idea to pass data via several components when building neat, reusable, and DRY code.
    * Prop drilling in react is sometimes advantageous for smaller apps since there are lesser components and conditions to control.
 
**[⬆ Back to Top](#table-of-contents)**
### 20
### What are the differences between a class component and functional component?
**Class components** A class component requires you to extend from React. Component and create a render function which returns a React element.
   
* It must have the render() method returning HTML 
* Also known as Stateful components because they implement logic and state.
* React lifecycle methods can be used inside class components (for example, componentDidMount). 
```javascript
    	class Car extends React.Component {
		  render() {
		    return <h2>Hi, I am a Car!</h2>;
		  }
		}
```

**Functional Components**

* A functional component is just a plain JavaScript function that accepts props as an argument and returns a React element. 
* There is no render method used in functional components. 
* Also known as Stateless components as they simply accept data and display them in some form, that they are mainly responsible for rendering UI.
* React lifecycle methods (for example, componentDidMount) cannot be used in functional components. 
```javascript
    function Car() {
	return <h2>Hi, I am a Car!</h2>;
    }
```

**[⬆ Back to Top](#table-of-contents)**
### 21
### Component Composition
Component composition is one of the most fundamental concepts in React that gives power to developers to build complex user interfaces by breaking them into smaller, reusable building blocks.

**Techniques for Component Composition:**
* **Parent-child component:** The simplest form of composition, where a parent component renders a child component and passes data as props.
* **Higher-Order Components (HOCs):** HOCs are functions that take components and return an enhanced version of them, enabling code reuse and logic sharing.
* **Render Props:** Components expose a prop that’s a function, allowing the consumer to render content based on the component’s internal state.
* **Context API:** It provides a way to share state globally. There is no need to pass down the props through all levels to share state.
* **Hooks:** With hooks like useState and useEffect, components can encapsulate state and side effects while remaining reusable.

### 22
### What is forwardRef?
When a child component needs to reference its parent component’s current node, the parent component needs a way to send down its `ref` to the child. The technique is called ref forwarding. It’s very useful when building reusable component libraries. forwardRef is a function used to pass the ref to a child component.

```javascript
const inputRef = useRef(null);

const ref = () => {
        inputRef.current.value = 1000;
    };
<input ref={inputRef}/> 
<Button onClick={ref}/>
// Other component with Button component 
const Button = (props,refs) => {
return(<button ref={refs} >{props.children}</button>)
}
export default forwardRef(Button);
```
**[⬆ Back to Top](#table-of-contents)**
### 23 
### What is Hooks?
Hooks is a special JavaScript function that allows you use state and other React lifecycle features without writing a class. This pattern has been introduced as a new feature in React 16.8 and helped to isolate the stateful logic from the components.

**Rules of Hooks:**
* Hooks should not be called inside loops, conditions, or nested functions.
* Hooks should be used inside React function components

**Built-in Hooks:**

| Hooks               | Description                                                                     |
|---------------------|---------------------------------------------------------------------------------|
|[useState()](#useState)           |To manage states. Returns a stateful value and an updater function to update it. |
|[useEffect()](#useEffect)          |To manage side-effects like API calls, subscriptions, timers, mutations, and more.|
|[useContext()](#useContext)         |To return the current value for a context.|
|[useReducer()](#useReducer)         |A useState alternative to help with complex state management.|
|[useCallback()](#useCallback)        |It returns a memorized version of a callback to help a child component not re-render unnecessarily.|
|[useMemo()](#useMemo)            |It returns a memoized value that helps in performance optimizations.|
|[useRef()](#useRef)             |It returns a ref object with a `.current` property. The ref object is mutable. It is mainly used to access a child component imperatively.|
|useImperativeHandle()|It customizes the instance value that is exposed to parent components when using ref.|
|[useLayoutEffect()](#useLayoutEffect)    |It fires at the end of all DOM mutations. It\'s best to use useEffect as much as possible over this one as the useLayoutEffect fires synchronously.|
|useDebugValue()      |Helps to display a label in React DevTools for custom hooks.

## Q. How to create custom Hooks?

React also allows us to create custom Hooks with unique features that extracts component logic into reusable functions.

A custom Hooks has following features:

* As a function, it takes input and returns output.
* Its name starts with **use** like useQuery, useMedia…
* Unlike functional components, custom hooks return a normal, non-jsx data.
* Unlike normal functions, custom hooks can use other hooks such as useState, useRef… and other custom hooks.

**Example:** Custom Hook - useFetch()

```js
/**
 * Custom Hook
 */
import { useState, useEffect } from "react";

const useFetch = (url) => {
  const [data, setData] = useState(null);

  useEffect(() => {
    fetch(url)
      .then((res) => res.json())
      .then((data) => setData(data));
  }, [url]);

  return [data];
};

export default useFetch;
```

```js
/**
 * App Component
 */
import "./styles.css";
import useFetch from "./useFetch";

export default function App() {
  // custom hook
  const [data] = useFetch("https://jsonplaceholder.typicode.com/todos");
  return (
    <>
      {data &&
        data.map((item) => {
          return <p key={item.id}>{item.title}</p>;
        })}
    </>
  );
}
```
**[⬆ Back to Question](#23)**

### useState
useState used to manage state in functional component. it accepts an initial state and returns two values

* The current state.
* A function that updates the state.

```jsx
import { useState } from "react";

function Example() {
// Declare a new state variable, which we'll call "count"
const [count, setCount] = useState(0);

return (
 <>
   <p>You clicked {count} times</p>
   <button onClick={() => setCount(count + 1)}>Click me</button>
 </>
);
}
```

### useEffect
useEffect(callback, dependencies): is used to handle side effects in function components. like fetching data or updating the DOM, and timers. you can think of useEffect Hook as componentDidMount, componentDidUpdate, and componentWillUnmount combined. useEffect accepts two arguments. The second argument is optional.
```javascript
const [count, setCount] = useState(0);

useEffect(() => {
  document.title = `Count: ${count}`;
}, [count]); //Runs on the first render And any time any dependency value changes

useEffect(() => {
  //Runs on every render
});

useEffect(() => {
  //Runs only on the first render
}, []);
```
**[⬆ Back to Question](#23)**
### useContext
useContext is a way to manage data between components without passing it through props.It's useful for managing global state. You create a context using `createContext()` and provide it at a higher level. Consumers can access the context using `useContext()`
```javascript
const ThemeContext = createContext();

function App() {
 return (
  <ThemeContext.Provider value="dark">
   <Component />
  </ThemeContext.Provider>
 );
}

function Component() {
 const theme = useContext(ThemeContext);
 // Use theme value here
} 
```
**[⬆ Back to Question](#23)**
### useReducer
useReducer() is a hook to use sometimes to manage the state of the application. It is very similar to the useState hook, just more complex. It acts as an alternate hook to the useState hook to manage complex state in your application

**Example:**

```js
import React, { useReducer } from 'react'

const initialState = 0
const reducer = (state, action) => {
  switch (action) {
    case 'increment': return state + 1
    case 'decrement': return state - 1
    case 'reset': return 0
    default: throw new Error('Unexpected action')
  }
}

const ReducerExample = () => {
  const [count, dispatch] = useReducer(reducer, initialState)
  return (
    <div>
      {count}
      <button onClick={() => dispatch('increment')}>+1</button>
      <button onClick={() => dispatch('decrement')}>-1</button>
      <button onClick={() => dispatch('reset')}>reset</button>
    </div>
  )
}

export default ReducerExample
```

Here, we first define an initialState and a reducer. When a user clicks a button, it will dispatch an action which updates the count and the updated count will be displayed. We could define as many actions as possible in the reducer, but the limitation of this pattern is that actions are finite.

**[⬆ Back to Question](#23)**

### useCallback
React\'s `useCallback()` Hook can be used to optimize the rendering behavior of your React function components. The `useCallback` will return a memoized version of the callback that only changes if one of the dependencies has changed.
**const cachedFn = useCallback(fn, dependencies)**

This is useful when passing callbacks to optimized child components that rely on reference equality to prevent unnecessary renders (e.g. shouldComponentUpdate).

**Example:**

```js
/**
 * useCallback()
 */
import React, { useState, useCallback, useEffect } from "react";

const count = new Set();

export default function App() {
  const [counter, setCounter] = useState(0);

  const increment = useCallback(() => {
    setCounter(counter + 1);
  }, [counter]);

  useEffect(() => {
    count.add(increment);
    console.log(count.size);
  }, [increment]);

  return (
    <>
      <h1>useCallback()</h1>
      <h2>Function Call: {count.size}</h2>
      <button onClick={increment}>Increment</button>
    </>
  );
}
```
**[⬆ Back to Question](#23)**
### useMemo
useMemo():**

The `useMemo()` is similar to `useCallback()` except it allows you to apply memoization to any value type. It does this by accepting a function which returns the value and then that function is only called when the value needs to be retrieved.

**Example:**

React application which renders a list of users and allows us to filter the users by their name. The filter happens only when a user explicitly clicks a button; not already when the user types into the input field.

```js
import React from 'react'

const users = [
  { id: 'a', name: 'Robin' },
  { id: 'b', name: 'Dennis' },
]

const App = () => {
  const [text, setText] = React.useState('')
  const [search, setSearch] = React.useState('')

  const handleText = (event) => {
    setText(event.target.value)
  }

  const handleSearch = () => {
    setSearch(text)
  }

  // useMemo Hooks
  const filteredUsers = React.useMemo(
    () =>
      users.filter((user) => {
        console.log('Filter function is running ...');
        return user.name.toLowerCase().includes(search.toLowerCase());
      }),
    [search]
  );

  return (
    <div>
      <input type="text" value={text} onChange={handleText} />
      <button type="button" onClick={handleSearch}>
        Search
      </button>

      <List list={filteredUsers} />
    </div>
  )
}

const List = ({ list }) => {
  return (
    <ul>
      {list.map((item) => (
        <ListItem key={item.id} item={item} />
      ))}
    </ul>
  )
}

const ListItem = ({ item }) => {
  return <li>{item.name}</li>
}

export default App
```

Here, the **filteredUsers** function is only executed once the search state changes. It doesn\'t run if the text state changes, because that\'s not a dependency for this filter function and thus not a dependency in the dependency array for the useMemo hook.

**[⬆ Back to Question](#23)**

### useRef

The useRef is a hook that uses the same ref throughout. It saves its value between re-renders in a functional component and doesn\'t create a new instance of the ref for every re-render. It persists the existing ref between re-renders.

**Example:**

```js
/**
 * useRef()
 */
export default function App() {
  const [count, setCount] = useState(0);
  const ref = useRef();

  useEffect(() => {
    ref.current = "SomeInitialValue";
  }, []);

  useEffect(() => {
    console.log(count, ref.current);
  }, [count]);

  return (
    <div className="App">
      <button onClick={() => setCount((c) => c + 1)}>Increment</button>
      <p>{count}</p>
    </div>
  );
}
```
**[⬆ Back to Question](#23)**
### useLayoutEffect

This runs synchronously immediately after React has performed all DOM mutations. This can be useful if you need to make DOM measurements (like getting the scroll position or other styles for an element) and then make DOM mutations or trigger a synchronous re-render by updating state.

As far as scheduling, this works the same way as `componentDidMount` and `componentDidUpdate`. Your code runs immediately after the DOM has been updated, but before the browser has had a chance to "paint" those changes (the user doesn\'t actually see the updates until after the browser has repainted).

**Example:**

```js
import React, { useState, useLayoutEffect } from 'react'
import ReactDOM from 'react-dom'

const BlinkyRender = () => {
  const [value, setValue] = useState(0)

  useLayoutEffect(() => {
    if (value === 0) {
      setValue(10 + Math.random() * 200)
    }
  }, [value])

  console.log('render', value)

  return (
    <div onClick={() => setValue(0)}>
      value: {value}
    </div>
  )
}

ReactDOM.render( <BlinkyRender />, document.querySelector('#root'))
```

**useLayoutEffect vs useEffect:**

* **useLayoutEffect**: If you need to mutate the DOM and/or do need to perform measurements
* **useEffect**: If you don\'t need to interact with the DOM at all or your DOM changes are unobservable (seriously, most of the time you should use this).


**[⬆ Back to Top](#table-of-contents)**

### 24
### What is the purpose of using super constructor with props argument?

The `super()` keyword is used to call the parent constructor and data. It is used for the inheritance model of class. `super(props)` would pass `props` to the parent constructor.

```js
class App extends React.Component {
  constructor(props) {
      super(props)
      this.state = {}
   }
}
export default App
```

Here, `super(props)` would call the `React.Component` constructor passing in props as the argument.

### createPortal()
createPortal allow us to render a component into a DOM node that resides outside the current DOM hierarchy of the parent component.
### createRoot
The React.createRoot lets you create a root to display React components inside a browser DOM node.

**What is the difference between createPortal vs createRoot?**
* createRoot is rendered inter App in root id, while createPortal renders children in the same component based on id.
* createRoot Returns an object with two methods: render and unmount.


### 28
### What are the differences between useEffect and useLayoutEffect hooks?
useEffect and useLayoutEffect are both React hooks that can be used to synchronize a component with an external system, such as a browser API or a third-party library. However, there are some key differences between the two:
- **Timing:** useEffect runs after the browser has finished painting, while useLayoutEffect runs synchronously before the browser paints. This means that useLayoutEffect can be used to measure and update layout in a way that feels more synchronous to the user.
- **Browser Paint:** useEffect allows browser to paint the changes before running the effect, hence it may cause some visual flicker. useLayoutEffect synchronously runs the effect before browser paints and hence it will avoid visual flicker.
- **Execution Order:** The order in which multiple useEffect hooks are executed is determined by React and may not be predictable. However, the order in which multiple useLayoutEffect hooks are executed is determined by the order in which they were called.
- **Error handling:** useEffect has a built-in mechanism for handling errors that occur during the execution of the effect, so that it does not crash the entire application. useLayoutEffect does not have this mechanism, and errors that occur during the execution of the effect will crash the entire application.

In general, it's recommended to use useEffect as much as possible, because it is more performant and less prone to errors. useLayoutEffect should only be used when you need to measure or update layout, and you can't achieve the same result using useEffect.

**[⬆ Back to Top](#table-of-contents)**
### 29
### What is Babel. or Transpiler?
Babel is a javascript compiler that converts modern Javascript(ECMAScript) code into version compatible with all the browsers. Browsers can't understand JSX code. So with the help of transpiler to convert your JSX to regular Javascript that browsers can understand. The most widely used transpiler right now is Babel

**[⬆ Back to Top](#table-of-contents)**
### 30
### What is Webpack.
WebPack is a javascript module bundler that is commonly used in react to bundle and manage dependancies. it takes all the individual javascript files and other assets in project like Css, images and combine them into a single bundle that can be loaded by the browser. `Minify JS and CSS`

**Make build: Make build in single file as requirement (Dev, UAT, Qa, Production )**
