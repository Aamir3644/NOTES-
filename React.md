## Commands to get started with React using vite :
- npm create vite@latest

## What is React ?
>> A javascript library for building user interfaces

## What is VDOM ?
>> The Virtual DOM in React.js is a performance optimization technique. It's a lightweight copy of the real DOM that React uses to efficiently update the user interface. When the application's state changes, React creates a new Virtual DOM and calculates the minimal set of changes needed to update the real DOM, reducing unnecessary updates. This process is known as reconciliation.

>> How It Works:
        (1) Initial Rendering:
        When a web page is initially loaded, both the Real DOM and the Virtual DOM are created to represent the page structure.

        (2) Rendering Changes:
        When data changes in a web application (due to user interaction, for example), the change is first reflected in the Virtual DOM.
        The entire Virtual DOM is much faster to update than the Real DOM.
        
        (3) Diffing (Determine the Difference):
        After the Virtual DOM is updated, a process called "diffing" compares the updated Virtual DOM with the previous version (before the change).
        This process determines exactly what parts of the Real DOM need to be updated.
        
        (4) Reconciliation (Update Real DOM):
        Once the differences are identified, only those specific parts of the Real DOM that need updating are modified.
        This is a more efficient process than updating the entire Real DOM, especially for complex web applications.

## What is create-react-app ?
>> Create React App is a command-line tool that helps developers set up and bootstrap React.js applications quickly. It provides a pre-configured development environment, it handles Babel configurations also. It's a great choice for starting React projects without the need for extensive configuration.

## What is Babel ?
>> Babel is a JavaScript compiler and transpiler. Its primary purpose is to convert modern JavaScript code, which may use the latest language features and syntax, into an older version of JavaScript that can run in older browsers and environments that don't support those new features.

## What is State ?
>> In React, "state" is a JavaScript object that stores data specific to a component. It allows components to manage and reflect changes in data, triggering automatic re-renders when the state is updated. State can be initialized using "useState" in functional components or in the constructor of class components.

## What is useState() Hook ?
>> useState is a built-in React hook used for managing state in functional components. It allows developers to declare and update state variables within these components. When state changes, React re-renders the component, reflecting the updated state in the user interface.
`` const [count, setCount] = useState(0); ``

## What is useEffect() Hook?
>> useEffect is a built-in React hook that allows you to perform side effects in functional components. Side effects are operations that occur after the component has rendered, such as data fetching, DOM manipulation, etc.
-  Its first argument is a callback function which contains the code for the side effect that you want to perform. and there's second argument that is a array of dependencies. This array specifies when the effect should run.

## What is useNavigate() Hook?
>> useNavigate() is used to programmatically navigate to different routes within a React component.
```js
        import {useNavigate} from 'react-router-dom';

        function Landing(){
            const navigate = useNavigate();
            const handleClick = () => {
                                        navigate('/about')
                                      };

            return <>
                        <button onClick={handleClick}>Go to About</button>
                   </>
        }
```

## Lazy Loading in React :
>> When you initially build any React application, it is bundled into single Javascript file. To divide them into small-small bundles you can use lazy loading in react. When we implement lazy loading, application will load components or other resources when needed, rather than loading them upfront all at once.
```js
        const MyComponent = React.lazy(() => import('./MyComponent'));
```
>> When using lazy loading with React, you also need to use the <Suspense> component to handle loading states. <Suspense> is a component provided by React that allows you to specify fallback content to display while the lazily loaded component is being loaded.
```js
        <Suspense fallback={<div>Loading...</div>}>
            <MyComponent />
        </Suspense>
```

## What is the Difference between Class Component and Function Component ?
>> Class Components are defined using ES6 class syntax and Contains a render() method to return JSX.
>> Defined as JavaScript functions that take props as an argument and return JSX.

>> Supports lifecycle methods like componentDidMount, componentDidUpdate, etc. for handling side effects and component updates.
>> Uses the useEffect hook for handling side effects and component lifecycle events.

>> Can be more verbose due to the class structure and lifecycle methods.
>> Generally considered more concise and readable, especially with hooks, which reduce boilerplate code.

>> Predates hooks and may not support the latest React features introduced after hooks.
>> Allows you to leverage hooks for state management and other features introduced in recent versions of React.

## What is Stateless and Statefull component ?
>> Stateless Components :
- Stateless components, often called functional components, are primarily responsible for rendering the UI based on the props they receive.
- They do not manage their own state. They produce output based solely on the input (props).
- With the introduction of hooks in React 16.8, functional components can now manage state and side effects using hooks like    useState and useEffect, making them more versatile.

>> Statefull Components :
- Stateful components, often called class components, can manage their own state.
- They can also implement lifecycle methods like componentDidMount and componentDidUpdate to handle side effects, data fetching, and updates.
- However, class components tend to be more verbose and complex compared to functional components with hooks.

## What is React Life Cycle ?
>> The three phases are: Mounting, Updating, and Unmounting.

```
        1. Mounting:
            - Constructor:
            The constructor is like the birth certificate. It's where a component is initialized and gets its initial state.
            - render:
            The render method is like creating the blueprint for how the component will look.
            - componentDidMount:
            componentDidMount is like the component's first day of school. It's called right after the component is added to the DOM.
            You can do things like fetch data from a server or set up subscriptions here.
        2. Updating:
            - shouldComponentUpdate:
            Before making any updates, React checks with shouldComponentUpdate. It's like asking, "Should we proceed with these changes?".
            If it returns true, the component updates; if false, it doesn't.
            - render:
            The render method is called again to update the component with new data or state.
            - componentDidUpdate:
            After the update, componentDidUpdate is like saying, "Okay, the changes are done!".
            It's often used for side effects like fetching additional data based on the updated props or state.
        3. Unmounting:
            - componentWillUnmount:
            componentWillUnmount is like saying goodbye. It's called right before a component is removed from the DOM.
            Cleanup tasks, like canceling network requests or clearing up subscriptions, are often done here.
        4. Error Handling:
            componentDidCatch:
            If an error occurs during rendering, the componentDidCatch method is like a safety net.
            It catches errors in components below it in the tree and logs the error or displays a fallback UI.
```

## What is Props ?
>> In react, props is short for properties. Props is a concept of passing data from parent component to child component. A parent can pass data to its child components by using attributes or props in JSX while rendering child component. basically, props are immutable so it means child component can not modify data it receives. i.e read-only.
```js
        // App.js
        import React from 'react';
        import Header from './Header';
        import './App.css';

        export default function App() {
        return (
            <>
            <Header title="First Header" /> 
            // This is a parent component which is passing data to child component
            </>                        
        );
        }
```
- There are two ways we can catch and access props in React
- (1) We can catch it in props object. The entire props object would be { title: "Hello" }
```js
        // Header.js
        export default function Header(props) {
        return <div>
                    {props.title}
               </div>;
        }
```
-(2) We can use destructuring syntax in function parameters.
```js
        // Header.js
        export default function Header({ title }) {
        return <div>
                    {title}
               </div>;
        }
```

## Prop Drilling :
>> Passing props can become very inconvenient when you need to pass some props deeply through the tree or if many components need the same props.
>> The nearest common ancestor could be far away from the components that needs the data and lifting state up means putting the state in that much higher position component can lead to a situation like prop drilling.     

## Re-rendering in React :
>> Re-rendering happens when
- (1) A state variable that is being used inside a component changes
- (2) A parent component re-render triggers all children re-rendering.

## Why use keys when rendering array elements as list ?
>> Basically, keys provide identity to each element in the list. React uses keys to efficiently update the UI when the list changes.
>> Using keys, React can identify which items are added, removes or edited or reordered and update only the affected items in the dom.

## Wrapper Component :
>> Wrapper Component is a component that wraps around another component, providing additional features,behaviours, styling, etc.
>> Wrapper Component are also called as High-Order Component (HOC).

```js
export default function App() {

  return (
    <>
      <WrapperComponent>
        <Component></Component> 
        // I can use any component inside wrapper component that I want to apply the CSS to.
        // Anything that i write inside wrapper component becomes children prop and i can render them
      </WrapperComponent>
    </>
  )
} 

function WrapperComponent({children}){
  return (
              <div style={{border :"4px solid black", padding :50}}>
                {children}
              </div>
         )
}

function Component(){
  return(
    <>
        <button>Click Here</button>
    </>
  )
}
```