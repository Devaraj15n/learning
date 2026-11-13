#


### Staplets:(10-11-2026)



```javascript
import React from 'react';
import { useState,useEffect } from 'react'

function App() {

  const [task,setTask]=useState("");
  const [list,setList]=useState([]);
  

  function addTask(){
    if(!task){
      return;
    }

    setList((prev)=>[
      ...prev,
      {
        id:crypto.randomUUID(),
        name:task
      }
      
    ]);
    setTask("");

  }

  // function deleteTask(id){
  //   let result=[];
  //   for(let obj of list){
  //     console.log();
  //       if(obj.id !=id){
  //           result.push(obj);
  //       }
  //   }

  //   setList(result);
  
  // }

  function deleteTask(id){
    setList((prev)=>prev.filter(obj=>obj.id !== id));
  }


  return (
    <div>
      <input type="text" value={task} placeholder="Enter Task" onChange={(e)=>setTask(e.target.value)}/>

      <button onClick={addTask}>Add Task </button>

      {list.map((val)=>(
        <div key={val.id}>
            <p>{val.name}</p><button onClick={()=>deleteTask(val.id)}>Delete</button>
          </div>
      ))}
    </div>
  )
}

export default App

```


# Platform Science technologies India private limited (12-11-2026)





