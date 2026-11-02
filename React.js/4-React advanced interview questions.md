# React advanced interview questions


### 1. prop drilling:
- happens when data passed to multiple components.
- even when not used in the intermediate components.

```javascript

export default function App() {
  const user = "Devaraj";
  return <Parent user={user} />;
}

function Parent({ user }) {
  return <Child user={user} />;
}

function Child({ user }) {
  return <h1>Hello, {user}</h1>;
}

```

Solutions: Context API.

### 2. React Context API:

- context provides to share values of themes,user authentication data and locales between the components.

- The main API's are `createContext` and `useContext`.

### 3. React Router.

- Is a library to handle the `client side navigation` and `routing` in react Application.
- When click the link, it should load the page without the refresh.

```javascript

import React, { useState } from 'react'
import {
    BrowserRouter,
    Routes,
    Link,
    Route
       } from "react-router-dom";


// Main App
export default function App() {
  // console.log("TEST")
  return (
    <div >
      <BrowserRouter>
        <nav>
          <Link to='/'>Home</Link>

          <Link to='/user'>User</Link>
        </nav>
        <Routes>
          <Route path="/" element={<h1>Home</h1>} />
          <Route path="/user" element={<h1>User</h1>} />
        </Routes>
      </BrowserRouter>
    </div>
  )
}

```
### 4. React.Memo:

- It is higher order component.
- Skip rendering a functional component when the props are unchanged (only render when the props are changed).
- It improves the performance.


```javascript
import React, { useState,useEffect,memo } from 'react'

// Main App
export default function App() {
  const [count,setCount]=useState(0);

  useEffect(()=>{
      console.log("count is changed");
  },[count]);
  return (
    <div >
      <button onClick={()=>setCount(count+1)}>Click Me</button>
      <Child count="Devaraj" />  // if the props is unchanged,child is not rendered.
    //   <Child count={count} /> // if the props is changed,child is rendered.

    </div>
  )
}

const Child=memo(function Child({count}){
  console.log("child is rendered",count);
  return 
})


```

### 5. useMemo,useCallback and React.memo:


useMemo - cached the value
useCallback - cached the function
memo - Stops the unwanted rendering, when props are unchanged.

### 6. Reconcilation in React:

- Is a process in React.
- which compares the Previous UI with the new UI and determine what needs to be in real DOM.


Example:
```
Hello Devaraj
count is 0
Click Me

```

When change the count to 1.

```
Hello Devaraj
count is 1
Click Me

```
