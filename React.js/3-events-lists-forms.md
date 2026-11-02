# React events, lists, and forms



### 1. Event Handling in react

- Allows a component to respond user actions like click,typing and form submission.

```javascript

export default function App() {

    function handleClick(value){
        console.log("button is clicked!",value);
    }
    
  return (
      <div>
      <button onClick={() => handleClick("TEST")}>Click ME</button>
      </div>
  )
}


```

onClick={() => handleClick("TEST")}  - when pass the value to the function.

onClick={handleClick("TEST")} - calls only while rendering - dont use like this way(it is not wokring when pass the value).

### 2. What is the difference between onClick={handleClick} and onClick={() => handleClick()}?


onClick={handleClick}
1. passed the function directly.
2. React calls `handleClick` on click.
3. Best for simple event handlers.(without arguments).

onClick=(()=>handleClick("test));

1. Passes a wrapper arrow function.
2. react call a arrow function and then it calls `handleClick`.
3. useful for arguments passed functions.

### 3. Keys important in React Lists:

- react identify which item is removed,deleted or reordered.

```javascript

     export default function App() {

const users=[
        {
            id:1,
        name:"Deva"
        },
        {
            id:2,
        name:"Deva2"
        }
    ];
        
  return (
      <div>
            <ul>
            {
                  users.map((user) => (
                  <li key={user.id}>{user.name}</li>
                 )
                )
            }
            </ul>
      </div>
  )
}


```

- use a stable and Unique Id

**avoid array indexes**: If we remove the element or add, key can associate the items.

### 4. Controlled components:

- Handled the form value in the state.


```javascript

import {useState,useEffect} from 'react';

export default function App() {

    const [email,setEmail]=useState();

    useEffect(()=>{
        console.log(email);
    },[email]);
  return (
      <div>
          <input 
              value={email}
              onChange={(e) => setEmail(e.target.value)} />
      </div>
  )
}

```

### 5. UnControlled components:

- Element value managed through the DOM instead of react state.

```javascript
import {useRef} from "react";

export default function App() {
    const nameRef =useRef( null);
    const ageRef =useRef( null);

    function handleSubmit(){
        console.log(nameRef.current.value);
        console.log(ageRef.current.value)

    }
  return (
      <div>
          
              <input ref={nameRef} placeholder="Enter Name"/>
              <input ref={ageRef}  placeholder="Enter Age"/>
              <button type="button"  onClick={handleSubmit}>Submit</button>
      </div>
      
  )
}

```


### 6. 