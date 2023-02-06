# React Evaluation 4
## 1) What are the Differences between TypeScript and JavaScript?

| JavaScript  | TypeScript   |
| ------------ | ------------ |
| It doesn't support strongly typed or static typing.  | It supports strongly typed or static typing feature. |
| Netscape developed it in 1995.   | Anders Hejlsberg developed it in 2012.|
| JavaScript source file is in ".js" extension.	   | TypeScript source file is in ".ts" extension. |
| It is directly run on the browser.  | It is not directly run on the browser.|
| It doesn't support optional parameters. | It supports optional parameters. |
| JavaScript doesn't support generics. | TypeScript supports generics.  |

**Example**
JavaScript

```javascript
<script>
function addNumbers(a, b) {
    return a + b;
}
var sum = addNumbers(10, 10);
console.log('Sum of the numbers is: ' + sum); 
</script>
```

TypeScript

```javascript
function addNumbers(a: number, b: number): number {
    return a + b;
}
let sum: number = addNumbers(10, 10);
console.log('Sum of the numbers is: ' + sum);
```

## 2) List the Advantages of TypeScript

- TypeScript highlights errors at compilation time.
- TypeScript supports strongly typed or static typing.
- TypeScript runs on any browser or JavaScript engine.
- TypeScript compiler can compile the .ts files into Es3, ES4 and ES5 to any ES Version.

## 3) What is an interface?

- Interface is the structure or skeleton for object.
- Interface in typescript is types for the object
- The TypeScript compiler uses interface for type-checking (also known as "duck typing" or "structural subtyping") whether the object has a specific structure or not.

**Syntax**

```javascript
interface interface_name {
          // variables' declaration
          // methods' declaration
}
```

**Example**

```javascript
interface FullName {  
    firstName: String;  
    lastName: String;  
}  
let printName = (name: FullName): void => {  
  console.log(name);
};  
let name = {firstName: "John", lastName: "Doe"}  
printName(name);
```

## 4) Explain how enums work in TypeScript?

Enums is set of named constants.

**Example**
```javascript
enum Directions {
  Left = 1,
  Right,
  Up,
  Down
};
console.log(Directions.Left);
```

## 5) What are the differences between useEffect and useLayoutEffect hooks?

| useEffect  | useLayoutEffect  |
| ------------ | ------------ |
| useEffect hook works asynchronously. | useLayoutEffect hook works synchronously. |
| useEffect hook fires after the browser paints. | useLayoutEffect hook fires before the browser paints (before the user can see visual changes). |
| Uses: If you don't need to interact with the DOM. | If you need to mutate the DOM and/or do need to perform measurements.|

**Example**

useEffect

```javascript
import React,{useState,useEffect} from 'react';
import axios from 'axios';
function Data() {
    const [posts,setPosts] = useState({})
    const [id,setId] = useState(1)
    const [idBtn,setIdbtn] = useState(1)
    const handClick = () =>{
        setIdbtn(id)
    }
    useEffect(() => {
        axios.get(`https://jsonplaceholder.typicode.com/posts/${id}`)
        .then(res => {
           setPosts(res.data)
            console.log(res)
        })
        .catch(err => {
            console.log(err)
        })
    },[idBtn])
  return (
    <div>
        <input type="text" value={id} onChange={(e) => { setId(e.target.value)}} />
        <button onClick={handClick}>Click Me</button>
        <ul>
            {
               <li key={posts.id}>{posts.title}</li>
            }
        </ul>
    </div>
  )
}

export default Data;
```

useLayoutEffect

```javascript
import React, { useLayoutEffect, useState } from 'react';
const App = () => {
  const [value, setValue] = useState("");
  useLayoutEffect(() => {
      setValue('Good Morning!');
  }, [value]);
  return <div>{value}</div>;
};
export default App;
```

## 6) What is prop drilling?

Prop drilling is a passing data through several nested children components unitl you get to the component where the data is needed.

## 7) Is it possible to use react without JSX?
Yes, It is possible to use react without JSX

**Example**

```javascript
const myElement = React.createElement('h1', {}, 'I do not use JSX!');

const root = ReactDOM.createRoot(document.getElementById('root'));
root.render(myElement);
```

## 8) What is React lazy function?

React.lazy() makes it easy to create components that are loaded using dynamic import() but rendered like regular components.

React.lazy() takes as its argument a function that must return a promise by calling import() to load the component.

**Example**

```javascript
import React, { Suspense } from "react";
import OtherComponent from './OtherComponent';

const LazyComponent = React.lazy(() => import('./OtherComponent'));

const MyComponent = ( ) => (
    <div>
        <Suspense fallback={<div>Loading...</div>}>
            <LazyComponent/>
        </Suspense>
    </div>
)
```

## 9) What is Redux Thunk?

Redux Thunk is a middleware that allows you to call the action creators that return a function(thunk) which takes the store’s dispatch method as the argument and which is afterwards used to dispatch the synchronous action after the API or side effects has been finished.

**Example**

```javascript
function getCartItems() {
	return async function (dispatch) => {
	const cartItems =  await fetch("API");
	if(cartItems) 
		dispatch({
			type: CART_ITEMS,
			payload: cartItems.json()
		})
}
}
```

## 10) What is strict mode in React?

StrictMode is used for highlighting possible problems in react application. It checks deprecation and warnings for its child components.
It provides visual feedback (warning/error messages).

**Example**

```javascript
import React from "react";
import { createRoot } from "react-dom/client";
import App from "./App";
import "./index.css";

const container = document.getElementById("root");
const root = createRoot(container);

root.render(
  <React.StrictMode>
        <App />
  </React.StrictMode>
);

```
