Basic fundamental of react js                



Basic fundamental of react js                

Q.  how to use react-router dom
solution :
    1. Install the react-router-dom using    " npm i react-router-dom "
    2. import the browsetRouter in our project and set the routes like this
        [
            ## <Routes >
            ## <Route path='/' element={<Home />} />
            ## <Route path='/about' element={<About />} />
            ## <Route path='/contect' element={<Contect />} />
            ## </Routes>
        ]

    3.Set Link whare we can use this route (Navbar me use karna hai )
        [
            # <div className='child'>
            #        <Link to="/"> <li>Home</li> </Link>
            #        <Link to="/about"> <li>About</li> </Link>
            #        <Link to="/contect"> <li>Contect</li> </Link>  
            # </div>
        ]




<!--  All Hooks with syntex -->

React provides several built-in hooks that allow you to manage state, side effects, context, refs, and other aspects of your components without writing class components. Here's an overview of the most commonly used hooks with their syntax and basic usage:

1. useState
Purpose: Manages state in functional components.

Syntax:

javascript
Copy code
const [state, setState] = useState(initialState);
Example:

javascript
Copy code
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
2. useEffect
Purpose: Handles side effects (e.g., data fetching, subscriptions) in functional components.

Syntax:

javascript
Copy code
useEffect(() => {
  // Effect code here

  return () => {
    // Cleanup code here
  };
}, [dependencies]);
Example:

javascript
Copy code
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `You clicked ${count} times`;

    return () => {
      document.title = 'React App'; // Cleanup on unmount
    };
  }, [count]);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
3. useContext
Purpose: Accesses context in functional components.

Syntax:

javascript
Copy code
const value = useContext(MyContext);
Example:

javascript
Copy code
import React, { useContext } from 'react';

const MyContext = React.createContext();

function MyComponent() {
  const value = useContext(MyContext);
  return <div>{value}</div>;
}

function App() {
  return (
    <MyContext.Provider value="Hello, World!">
      <MyComponent />
    </MyContext.Provider>
  );
}
4. useReducer
Purpose: Manages more complex state logic in functional components.

Syntax:

javascript
Copy code
const [state, dispatch] = useReducer(reducer, initialState);
Example:

javascript
Copy code
import React, { useReducer } from 'react';

const initialState = { count: 0 };

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
  const [state, dispatch] = useReducer(reducer, initialState);

  return (
    <div>
      <p>Count: {state.count}</p>
      <button onClick={() => dispatch({ type: 'increment' })}>
        Increment
      </button>
      <button onClick={() => dispatch({ type: 'decrement' })}>
        Decrement
      </button>
    </div>
  );
}
5. useRef
Purpose: Accesses DOM nodes or persists mutable values across renders.

Syntax:

javascript
Copy code
const refContainer = useRef(initialValue);
Example:

javascript
Copy code
import React, { useRef, useEffect } from 'react';

function TextInputWithFocusButton() {
  const inputEl = useRef(null);

  const onButtonClick = () => {
    inputEl.current.focus();
  };

  return (
    <div>
      <input ref={inputEl} type="text" />
      <button onClick={onButtonClick}>Focus the input</button>
    </div>
  );
}
6. useMemo
Purpose: Optimizes performance by memoizing expensive calculations.

Syntax:

javascript
Copy code
const memoizedValue = useMemo(() => computeExpensiveValue(a, b), [a, b]);
Example:

javascript
Copy code
import React, { useState, useMemo } from 'react';

function ExpensiveComponent({ a, b }) {
  const memoizedValue = useMemo(() => {
    // Expensive calculation
    return a + b;
  }, [a, b]);

  return <div>{memoizedValue}</div>;
}
7. useCallback
Purpose: Memoizes callback functions to prevent unnecessary re-renders.

Syntax:

javascript
Copy code
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);
Example:

javascript
Copy code
import React, { useState, useCallback } from 'react';

function MyComponent() {
  const [count, setCount] = useState(0);

  const handleClick = useCallback(() => {
    setCount(count + 1);
  }, [count]);

  return <button onClick={handleClick}>Increment</button>;
}
8. useLayoutEffect
Purpose: Similar to useEffect, but fires synchronously after all DOM mutations.

Syntax:

javascript
Copy code
useLayoutEffect(() => {
  // Effect code here

  return () => {
    // Cleanup code here
  };
}, [dependencies]);
Example:

javascript
Copy code
import React, { useLayoutEffect, useRef } from 'react';

function LayoutEffectExample() {
  const ref = useRef();

  useLayoutEffect(() => {
    // Runs after DOM update
    console.log(ref.current.offsetHeight);
  }, []);

  return <div ref={ref}>Hello, world!</div>;
}
9. useImperativeHandle
Purpose: Customizes the instance value exposed to parent components when using ref.

Syntax:

javascript
Copy code
useImperativeHandle(ref, () => ({
  customMethod() {
    // Custom behavior
  }
}), [dependencies]);
Example:

javascript
Copy code
import React, { useRef, useImperativeHandle, forwardRef } from 'react';

const MyInput = forwardRef((props, ref) => {
  useImperativeHandle(ref, () => ({
    focus: () => {
      inputRef.current.focus();
    },
  }));
  
  const inputRef = useRef();
  
  return <input ref={inputRef} />;
});

function ParentComponent() {
  const inputRef = useRef();
  
  return (
    <div>
      <MyInput ref={inputRef} />
      <button onClick={() => inputRef.current.focus()}>Focus Input</button>
    </div>
  );
}
These are the most commonly used hooks in React.
#   R e a c t - J s - S t  
 