# 2. React Hook Interview Questions;


### 11. React hooks
- Special Functions that let you use state and other react features inside the functional components.

    - useState
    - useEffect
    - useContext
    - useRef
    - useMemo
    - useCallback
    - useReducer.


### 12. What is useState:
-  add the State to the functional component.

```javascript

import {useState} from 'react';


function Counter(){
    const [count,setCount]=useState(0);

    return(
        <div>
            <h2>Count is {count}</h2>
            <button onClick={()=>setCount(count+1)}>Increment</button>
        
        </div>
    )

}

```

count -> State Value.
setCount -> State setter function
0 -> Initial Value

### 13. useEffect:

- used to handle the side effects in functional components.

    - fetching data from API.
    - setting up timers or intervals.
    - Adding Event listeners.


```javascript
import {useEffect,useState} from 'react';


export default function App() {

        const [users, setUsers] = useState([]);

  useEffect(() => {
    async function fetchUsers() {
      const response = await fetch(
        "https://jsonplaceholder.typicode.com/users"
      );
      const data = await response.json();
        console.log("data===",data);
      setUsers(data);
    }

    fetchUsers();
  }, []);
    
  return <h1>Hello {users.length}</h1>
}


```


output:
Hello 10

### 14. diff between useEffect dependency arrays:

1. 

```javascript
useEffect(()=>{

});

```
- Runs after every committed rerun.


```javascript
    const [count,setCount]=useState(0);
    useEffect(()=>{
        console.log("Count is ",count);
    })


    <p onClick={()=>setCount(count+1)}>Click me</p>

```

    - every click ,useffect runs, so it is not cause the infinite loop.



```javascript
    const [count,setCount]=useState(0);
    useEffect(()=>{
        setCount(count+1);
    })

```

  - it will cause the infinite loop due to the reason of state is updated inside the useEffect.



2. useEffect(() => {}, [])
 - Runs after initial amonut.

3. useEffect(() => {}, [count])
 - run after initial mount and count value changes.



### 15. Cleanup Function:

```javascript
import {useEffect,useState} from "react";

export default function App() {
    const [count,setCount]=useState(0);
        useEffect(()=>{
             const  timer= setInterval(()=>{
                 setCount(previous => previous+1);
                } , 1000);

                return () => {
                    clearInterval(timer);
                }
        }, [] );

    // useEffect(() => {
    //   console.log("Count changed:", count);
    // }, [count]);

    // to check the count value
  return <h1>Count : {count}</h1>
}

```



with `clearInterval` -> when the component unmounts, react runs the cleanup function.


Detailed Example:

```javascript

import { useEffect, useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Counter mounted");

    const timer = setInterval(() => {
      setCount(previous => previous + 1);
    }, 1000);

    return () => {
      console.log("Counter unmounted - cleanup runs");
      clearInterval(timer);
    };
  }, []);

  return <h2>Count: {count}</h2>;
}

export default function App() {
  const [show, setShow] = useState(true);

  return (
    <div>
      <button onClick={() => setShow(previous => !previous)}>
        Toggle Counter
      </button>

      {show && <Counter />}
    </div>
  );
}

```

When <Counter /> unmounts, clearInterval is executed.



### 16. What is useRef:

- stores the values between renders without triggers the re-renders when the Value changes.




```javascript
import { useState , useRef } from 'react';

export default function App() {
    const input=useRef(0);

    const [count,setCount]=useState(0);
   function refInput(){
        input.current+=1;

       console.log(input.current);
    }
  return(
          <div>

              <button onClick={refInput}>Increase useRef</button>
        
              <button onClick={ () => setCount(count+1) }>Increase State</button>
                <h1>State {count}</h1>
          </div>
  ) 
}


```


output:
Increase State - Increase the value.
State 10

console.log(input.current); - It is changed when click, but not changed the state value and re-render.



#### Focus an input using useRef


```javascript
import { useRef } from "react";

export default function App() {
  const inputRef = useRef(null);

  function focusInput() {
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} placeholder="Enter your name" />
      <button onClick={focusInput}>
        Focus Input
      </button>
    </>
  );
}

```

### 17. useMemo:

- useMemo cached the value between renders until it dependencies changes


```javascript

const total = useMemo(()=>{
    return products.reduce((sum,product)=> sum + product.price,0)
},[products]);


```

- only calculated when the products value changes.


```javascript
import {useState,useMemo} from "react"

export default function App() {

    const [count,setCount]=useState(10);
    const [number,setNumber]=useState(10);

    const total=useMemo(()=>{
         return  number +1;
    },[number]);
  return (
         <div>
            <button onClick={()=>setCount(count+1)}>Increase State</button>

             <h1>State Value is {count}</h1>
    
            <button onClick={()=>setNumber(number+1)}>Increase Number</button>
            <h1>State Value is {number}</h1>
         
         </div>
  )
}


```

- only `number` dependencies changes, the total calculation is executed.



### 18. useCallback:

- caches a function definition between renders until its dependencies changes.


```javascript
const handleClick=useCallback(()=>{
    console.log('Button is clicked!');
},[]);
```


- Imagine when parent sent the function to child, when parent value changes, child unnecessarily change. 
- to avoid this `useCallback` is used.

### 19. useContext:

- Pass the value to the component without passing to every component.


```javascript
import {useContext,createContext,useState} from 'react';

const themeContext=createContext();

function Heading(){

    const {theme,setTheme}=useContext(themeContext);
    return(
            <div>
                <h1>Theme color is {theme}</h1>
                
                <button onClick={()=>setTheme(
                theme==="Dark" ? "light" : "Dark"
            )}>Click me to change the theme</button>
            
            </div>
        
    )
}

export default function App() {
    const [theme,setTheme]=useState("light");
  return (
      <themeContext.Provider value ={{theme,setTheme}}>
          <Heading/>
      </themeContext.Provider>
  )
}

```

- useContext() - use the value.
- createContext() - create the context.
- Provider is pass the value to the component.


### 20. Rules of Hooks:

1. 
- Call hooks at the top of the functions.
- Not inside loops,conditions or nested functions.


2. 
- Call hooks only in `functional components` not in ordinary javascript or class components.
