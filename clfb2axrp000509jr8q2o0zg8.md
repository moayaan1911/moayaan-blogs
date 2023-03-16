---
title: "Master React Hooks"
datePublished: Thu Mar 16 2023 12:02:58 GMT+0000 (Coordinated Universal Time)
cuid: clfb2axrp000509jr8q2o0zg8
slug: master-react-hooks
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1678967898738/410cdb5d-7446-4a41-b826-77f8b0f7002e.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1678968122588/09a6c19e-fbb0-4abf-a892-905628c79aa5.png
tags: javascript, frontend-development, state-management, reacthooks

---

React is a popular JavaScript library that allows developers to create dynamic user interfaces. One of the newer features of React is Hooks, which were introduced in React 16.8. Hooks provide an easier way to manage state and lifecycle methods in functional components, making it easier to write reusable and maintainable code.

If you're new to React, Hooks can be a bit intimidating at first. But don't worry, in this blog post, I'll introduce you to React Hooks and show you how to use them in your projects.

There are several different hooks available in React, each designed to accomplish a specific task. Here is a rundown of some of the most commonly used hooks:

1. **useState** \- The useState hook is used to manage state within a functional component. It takes an initial state as an argument and returns an array with the current state value and a function to update it.
    
2. **useEffect** \- The useEffect hook allows you to perform side effects within a functional component. Side effects might include fetching data from an API, subscribing to events, or modifying the DOM. It takes a function as an argument and executes it after every render.
    
3. **useContext** \- The useContext hook allows you to access context values within a functional component. Context provides a way to pass data through the component tree without having to pass props down manually at every level.
    
4. **useReducer** - The useReducer hook is a more powerful alternative to useState when dealing with complex state management. It takes a reducer function and an initial state as arguments and returns the current state value and a dispatch function to update it.
    
5. **useCallback** \- The useCallback hook is used to memoize functions so that they only change when their dependencies change. This can be useful for preventing unnecessary renders in child components.
    
6. **useMemo** \- The useMemo hook is used to memoize values so that they only change when their dependencies change. This can be useful for optimizing expensive calculations.
    
7. **useRef** \- The useRef hook is used to create a mutable reference to a value that persists across renders. This can be useful for accessing DOM elements or storing instance variables.
    

## useState()

```javascript
import React, { useState } from 'react';

function Example() {
  // Declare a state variable called "count" with an initial value of 0
  const [count, setCount] = useState(0);

  // Declare a function "incrementCount" that increases the count state variable by 1
  function incrementCount() {
    setCount(count + 1);
  }

  // Render the count state variable and a button that calls the incrementCount function
  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>
        Click me
      </button>
    </div>
  );
}
```

Explanation:

First, we import the useState hook from the React library and declare a functional component called "Example".

Inside the component, we use the useState hook to declare a state variable called "count" with an initial value of 0. The "useState" function returns an array with two elements: the current value of the state variable (in this case, "count") and a function to update the state variable (in this case, "setCount").

We then declare a function called "incrementCount" that calls the "setCount" function with the current value of "count" plus 1. This will update the "count" state variable and trigger a re-render of the component.

Finally, we render the current value of the "count" state variable and a button that calls the "incrementCount" function when clicked.

In summary, the useState hook allows us to add state to a functional component and manage it using the "useState" function and the state update function it returns. This makes it easy to add interactivity to a component without having to use class components and lifecycle methods.

## useEffect()

```javascript
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  // Declare a side effect that runs after every render
  useEffect(() => {
    // Update the document title with the current count value
    document.title = `You clicked ${count} times`;
  });

  function incrementCount() {
    setCount(count + 1);
  }

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={incrementCount}>
        Click me
      </button>
    </div>
  );
}
```

Explanation:

First, we import the useState and useEffect hooks from the React library and declare a functional component called "Example".

Inside the component, we use the useState hook to declare a state variable called "count" with an initial value of 0. We also use the useEffect hook to declare a side effect that runs after every render. This side effect updates the document title with the current value of the "count" state variable by setting the "document.title" property.

The useEffect hook takes a function as its first argument, which is the side effect to be executed. In this case, we provide an anonymous arrow function that sets the document title with the current count value.

The useEffect hook runs after every render by default, but we can add an optional array of dependencies as a second argument to control when the effect runs. If we want the effect to run only when the "count" state variable changes, we can pass an array with "count" as the only dependency: useEffect(() =&gt; { ... }, \[count\]);

Finally, we render the current value of the "count" state variable and a button that calls the "incrementCount" function when clicked.

In summary, the useEffect hook allows us to add side effects to a functional component, such as updating the DOM, fetching data, or subscribing to events. By default, the effect runs after every render, but we can control its execution with an array of dependencies. This makes it easy to add complex behavior to a component without having to use class components and lifecycle methods.

## useContext()

```javascript
import React, { useState, useContext } from 'react';

// Create a context object
const ThemeContext = React.createContext('light');

function App() {
  const [theme, setTheme] = useState('light');

  // Define a function to toggle the theme
  function toggleTheme() {
    setTheme(theme === 'light' ? 'dark' : 'light');
  }

  // Use the useContext hook to get the current theme from the context
  const currentTheme = useContext(ThemeContext);

  return (
    // Provide the current theme to the context provider
    <ThemeContext.Provider value={theme}>
      <div>
        <h1>{currentTheme} theme</h1>
        <button onClick={toggleTheme}>
          Toggle theme
        </button>
      </div>
    </ThemeContext.Provider>
  );
}
```

Explanation:

First, we import the useState and useContext hooks from the React library and create a context object called "ThemeContext" using the createContext function. The argument passed to createContext is the default value for the context, which is used when there is no matching provider in the component tree.

Inside the App component, we use the useState hook to declare a state variable called "theme" with an initial value of 'light'. We also define a function called "toggleTheme" that toggles the "theme" state variable between 'light' and 'dark'.

We then use the useContext hook to get the current theme value from the context. The useContext hook takes a context object as its argument and returns its current value. In this case, we pass the "ThemeContext" object and get the current theme value.

Finally, we render the current theme value and a button that calls the "toggleTheme" function when clicked. We also provide the current theme value to the "ThemeContext.Provider" component as its value prop. This allows child components to access the current theme value using the useContext hook.

In summary, the useContext hook allows us to get the current value of a context object in a functional component. This makes it easy to share data between components without having to pass props down the component tree.

##   
useReducer()

```javascript
import React, { useReducer } from 'react';

// Define a reducer function
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return { count: state.count + 1 };
    case 'decrement':
      return { count: state.count - 1 };
    default:
      throw new Error();
  }
}

function Counter() {
  // Use the useReducer hook to manage state with a reducer function
  const [state, dispatch] = useReducer(reducer, { count: 0 });

  // Define functions to dispatch actions to the reducer
  function increment() {
    dispatch({ type: 'increment' });
  }
  function decrement() {
    dispatch({ type: 'decrement' });
  }

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={increment}>
        Increment
      </button>
      <button onClick={decrement}>
        Decrement
      </button>
    </div>
  );
}
```

Explanation:

First, we import the useReducer hook from the React library and define a reducer function called "reducer". The reducer function takes two arguments: the current state and an action object. It returns the new state based on the action type.

Inside the Counter component, we use the useReducer hook to manage state with the reducer function. The useReducer hook takes two arguments: the reducer function and the initial state. It returns the current state and a dispatch function that we can use to dispatch actions to the reducer.

We then define two functions called "increment" and "decrement" that dispatch the "increment" and "decrement" actions to the reducer using the dispatch function.

Finally, we render the current count value from the state and two buttons that call the "increment" and "decrement" functions when clicked.

In summary, the useReducer hook allows us to manage state with a reducer function instead of using the useState hook. This can make state management more predictable and easier to reason about for complex applications. The useReducer hook returns the current state and a dispatch function that we can use to dispatch actions to the reducer. This pattern is often used in combination with the useContext hook to share state between components.

##   
useCallback()

```javascript
import React, { useState, useCallback } from 'react';

function App() {
  const [count, setCount] = useState(0);

  // Define a function using the useCallback hook
  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={handleClick}>
        Click me
      </button>
    </div>
  );
}
```

Explanation:

Inside the App component, we use the useState hook to declare a state variable called "count" with an initial value of 0.

We then use the useCallback hook to define a function called "handleClick" that increments the "count" state variable by 1 when called. The useCallback hook takes two arguments: the function to memoize and an array of dependencies. The function is only re-created when any of the dependencies change, which can help to optimize performance in some cases.

In this example, we pass the "count" state variable as a dependency to the useCallback hook. This ensures that the "handleClick" function always has access to the latest value of the "count" state variable.

Finally, we render the current count value from the state and a button that calls the "handleClick" function when clicked.

In summary, the useCallback hook allows us to memoize functions in a functional component to optimize performance. By memoizing a function, we ensure that it is only re-created when its dependencies change. This can be useful when passing functions as props to child components or when defining event handlers that depend on state variables.

##   
useMemo()

```javascript
import React, { useState, useMemo } from 'react';

function App() {
  const [count, setCount] = useState(0);

  // Define a memoized value using the useMemo hook
  const memoizedValue = useMemo(() => {
    return count * 2;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <p>Memoized value: {memoizedValue}</p>
      <button onClick={() => setCount(count + 1)}>
        Increment count
      </button>
    </div>
  );
}
```

Explanation:

Inside the App component, we use the useState hook to declare a state variable called "count" with an initial value of 0.

We then use the useMemo hook to define a memoized value called "memoizedValue" that is equal to the "count" state variable multiplied by 2. The useMemo hook takes two arguments: the function to memoize and an array of dependencies. The function is only re-evaluated when any of the dependencies change, which can help to optimize performance in some cases.

In this example, we pass the "count" state variable as a dependency to the useMemo hook. This ensures that the "memoizedValue" is only re-evaluated when the "count" state variable changes.

Finally, we render the current count value from the state, the memoized value, and a button that increments the "count" state variable when clicked.

In summary, the useMemo hook allows us to memoize values in a functional component to optimize performance. By memoizing a value, we ensure that it is only re-evaluated when its dependencies change. This can be useful when computing expensive values that depend on other variables, such as filtering or sorting an array of data.

##   
useRef()

```javascript
import React, { useRef } from 'react';

function App() {
  const inputRef = useRef(null);

  const handleClick = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input type="text" ref={inputRef} />
      <button onClick={handleClick}>
        Focus input
      </button>
    </div>
  );
}
```

Explanation:

Inside the App component, we use the useRef hook to declare a reference called "inputRef" with an initial value of null. A reference is an object that contains a current property, which can be used to store mutable values that persist between renders.

We then define a function called "handleClick" that calls the focus method on the "inputRef" reference when executed. The focus method is used to give focus to an input element, which means that it is ready to receive user input.

Finally, we render an input element with the ref attribute set to the "inputRef" reference and a button that calls the "handleClick" function when clicked.

In summary, the useRef hook allows us to create mutable references in a functional component. We can use these references to store mutable values that persist between renders and access them in event handlers or other functions. In this example, we use the useRef hook to create a reference to an input element and focus it when a button is clicked.

##   
Conclusion

In conclusion, React Hooks are a powerful feature that allows developers to write more concise and reusable code in React functional components. Each of the hooks - useState, useEffect, useContext, useReducer, useCallback, useMemo, and useRef - serve a specific purpose and can be used to manage different aspects of the component state and behavior. The useState hook is used to manage state variables, useEffect is used to handle side effects, useContext is used to share state across components, useReducer is used for more complex state management, useCallback and useMemo are used for performance optimization, and useRef is used to create mutable references. By using React Hooks, developers can write more modular and maintainable code that is easier to reason about and test.