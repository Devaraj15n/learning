#


### redux toolkit:

- Manage state management in react Application.

it helps:
- Maintain global state.
- share data between the components.
- avoid unneccessary props drilling.
- handle asynchronous api calls.


### Main concepts:

Store - Hold global application state
Slice - contins State and reducers
Reducer - function how state changes
Action - describes what happens
Dispatch - Send an action
Selector - reads data from the store


### Redux store:

- Store the Global state Value.

const initialValue={
    count:0,
    username:"Deva"
};


### CreateSlice():
- create a slice of application state.

features/counter/counterSlice.js:

```javascript

import {createSlice} from '@reduxjs/toolkit';

const initialValue={
  count:0
}


const countSlice=createSlice({
  name:"counter",
  initialValue,
  reducers:{
    increment:(state)=>{
      state.count+1
    },
    decrement:(state)=>{
      state.count-1;
    },
    reset:(state)=>{
      state.count=0;
    }
  }
})


export const {
  increment,
  decrement,
  reset
}=countSlice.actions;

export default countSlice.reducer;

```

name - name of the slice
initialValue - initial state value
reducers - function to update the state value.
countSlice.actions - 
countSlice.reducer - Reducer function used by the store.


### ConfigureStore:

- configureStore create and configre store 

```javascript
import {configureStore} from '@reduxjs/toolkit';

import countReducer from '../features/counter/counterSlice.js'

const store =configureStore({
  reducer:{
      counter:countReducer
  }
});

export default store;

```



State can now accessible:

```state.counter.count```



### What is provider:

- Provider makes the store availble to the react components.

index.js


```javascript

import React from 'react'
import ReactDOM from 'react-dom/client'
import App from './App.jsx'
import {Provider} from 'react-redux';
import store from './app/store';


ReactDOM.createRoot(document.getElementById('root')).render(
  <Provider store={store} >
       <App />
  </Provider>
  )


```


### useSelector and useDispatch();
useSelector - get data
useDispatch - send action to the redux store.


```javascript

import {useDispatch} from 'react-redux';

function CounterButton(){

  const dispatch=useDispatch();
  return (
      <button onClick={()=>dispatch(increment())}>Increment</button>
  )
}

```

eg:

APP.jsx

```javascript
import React from 'react';
import {useSelector,useDispatch} from 'react-redux';

import {
  increment,
  decrement,
  reset
} from '../features/counter/counterSlice.js'



function App() {
  const count = useSelector((state)=>state.counter.count);

  const dispatch=useDispatch();


  return (
    <div >
      <p>{count}</p>
        <button onClick={()=>dispatch(increment())}>Increment</button>
        <button  onClick={()=>dispatch(decrement())}>Decrement</button>
        <button  onClick={()=>dispatch(reset())}>Reset</button>
    </div>
  )
}

export default App


```

### createAsyncThunk:
- handles the Asynchronous operations , such as API Requests.

```javascript
import {createAsyncThunk,createSlice} from '@redux/toolkit';



export const fetchEmployees=createAsyncThunk(
  'employees/fetchemployees',
  async()=>{
   const response =await fetch("https://dummyjson.com/users");

   if(!response.ok){
    throw new Error ("Something went wrong");
   }


    const data=response.json();

    return data.users
  }
)

const employeeSlice =createSlice({
  name:'employees',
  initalValue:{
    employee:[],
    loading:false,
    error:null
  },
  reducer:{},
  extraReducers:(builder)=>{
    builder
    .addCase(fetchEmployees.pending,(state)=>{
      state.loading=true,
      state.error=null
    })
    .addCase(fetchEmployees.fulfilled,(state,action)=>{
      state.loading=false,
      state.employee=action.payload

    })
     .addCase(fetchEmployees.rejected,(state,action)=>{
      state.loading=false,
      state.error=action.error.message

    })
  }
}) 


export default employeeSlice.reducer;

```
