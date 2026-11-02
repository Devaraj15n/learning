#
# 1. React.js fundamentals

### 1. React.js


- Is an Open Source Javascript library.
- Which is used to build single page applications(SPA).
- Allows to build resusable UI components.

```javascript
function Welcome(){
    return <h1>Hi Deva, Welcome !</h1>
}

export function Welcome;

```

### 2. Main features of react.


- Component based archietecture. - (Build using Reusable UI components)
- JSX(write HTML like in javascript).
- state management.
- hooks( we can use and create the hooks )


### 3. JSX:

- Stands for Javascript XML
- Write the HTML markup inside the javascript

```javascript

const name='Deva';

export default function App() {
  return <h1>My name is {name}</h1>
}


```
### 4. Components

 - Resusable piece of UI that can contain markup,logic and style.

```javascript

function Button(){
        return <button>click Me!</button>
}
export default function App() {
  return(
              <div>
                  <Button />
                  <Button />
              </div>
  )
}

```

### 5. diff between functional and class components:


| functional             | class               |
| ---------------------- | ------------------- |
| Defined using function | Defined using class |
| Using hooks state      | Using `this.state`  |
| Do not use `this`      | Use `this`          |

**functional:**
```javascript
function Welcome(){
    return <h1> Welcome home</h1>
}

```

**Class:**

```javascript

import React from 'react';

class Welcome extends React.component{
    render(){
        return <h1>Welcome Home</h1>
    }
}

```

### 6. diff between props and state.

| props                                | state                                   |
| ------------------------------------ | --------------------------------------- |
| passed from parent to child          | managed by the component                |
| read only                            | updated using the appropriate State API |
| changes when Parent value is changed | trigger when UI Updates.                |

```javascript

import { useState } from 'react';

function Welcome({ name }) {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>My name is {name}</h1>
      <h1>Count is {count}</h1>
      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </>
  );
}

export default Welcome;



import Welcome from './Welcome';

export default function App() {
  return (
    <>
      <Welcome name="Deva" />
    </>
  );
}


```



### 7. Virtual Dom:

- Virtual Dom is conceptual representation of the UI.
- State or props is changed, it compares the original UI with the previous one, and necassary to the actual DOM.



### 8. React and React Dom:


React:

- React provides core concepts, hooks and rendering concepts.

React DOM:

- used to render react applications with the actual DOM.

```javascript

import {createRoot} from 'react-dom/client';
import App from './App';

createRoot(document.getElementById('root')).render(<App/>)

```

### 9. What is single page Applications:

- View the entire page without the reloading of the page.


### 10. conditional rendering

- displaying different UI based on the condition

```javascript

function userStatus({loggedIn}){
    return (
        <div>
            {loggedIn ? <h1>if condition</h1> : <h1>Else condition</h1>}
        </div>
    )
}

```





