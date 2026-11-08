#



### Callback Function:
- Callback is a function which is passed as an argument to another function and executes later.


```javascript
function getData(callback){

  console.log("Getting data")
  callback("data Received");
}


getData((result)=>{
  console.log(result);

});

```


### callback Hell:

- Multiple Asynchronous operations are nested inside the loop.
- Making code difficult to read, debug.

```javascript
getUser(userId,(user)=>{
      getOrders(user.id,(orders)=>{
          getPayments(orders.id,(payment)=>{
              console.log("order is completed")
          });
      });
});

```


Solution:
Promise and aync/await


### Promise:
- Async operation.


three states:
1. Pending.
2. Fulfilled.
3. Rejected


```javascript
const promise =new Promise((resolve,reject)=>{
  const success=true;
  if(success){
    resolve("Success");
  }else{
    reject("Error");
  }
});

promise
  .then(result=>console.log(result))
  .catch(error => console.log(error));

```

### aync/await:
- Asynchronous operation 
- Made up by the promises.

```javascript


getEmployees();

function fetchEmployee(){
    return new Promise((resolve)=>{
        setTimeout(()=>{
            resolve({
                id: 101,
                name: "Devaraj",
                role: "Full Stack Developer"
            });
        },2000)
    })
}


async function getEmployees(){

  console.log("Processing Employee")

  try{
    const employee=await fetchEmployee();
    console.log(employee);
    console.log("Employee data is Received");

  }catch(error){
    console.log("error",error);
  }

}

```

**Output:**
Processing Employee
{ id: 101, name: 'Devaraj', role: 'Full Stack Developer' }
Employee data is Received



### Diff between Promise and async/await:

Promise | Async\await
| ---- | ---|
| use then() and catch() | use await, try and catch |
| can create promise chains | use asynchronous code easier to read |


### Promise.all():
- executes all promise concurrently and got the resolve if all resolves.
- if any Promise rejects,the returned Promise is rejected with rejected reason.


```javascript


const results=Promise.all([
  getUsers,
  getProducts,
  getSalary
]);


results
.then((result)=>console.log(result))
.catch((error)=>console.log(error));

```



### Promise.allSettled():


- wait all Promise settled either if any success or fail.

```javascript

const results=await Promise.allSettled([
  Promise.resolve("Success"),
  Promise.reject("Error")
]);


console.log(results);

```


Output:
{
    [status:"success",value:"Success"]
    [status:"error",reason:"Error"]
}

### Promise.all() and Promise.allSettled():


Promise.all() | Promise.allSettled()
| ------- | ------ |
| Returns reject if any one rejects | waits for all Promise to settle |
use when all promise is required | Useful when Partial results are acceptable

### Promise.race():


- Settles with the First Promise that settles if either success or failure.

```javascript


const promise1=new Promise((resolve)=>{
    setTimeout(()=>{
        resolve("Promise 1 is resolved");
    },3000)
});


const promise2=new Promise((resolve)=>{
    setTimeout(()=>{
      resolves("Promise 2 is  resolved"); // console.log("Promise 2 is resolved"); if console.log means it should also print Promise 1 is resolved
    },1000)
},1000)



const results=await Promise.race([promise1,promise2]);

console.log(results);

```


**Output:**

Promise 2 is resolved


```javascript
const promise1=new Promise((resolve)=>{
  setTimeout(()=>{
    resolve("promise 1 is resolved");
  },3000)
});


const promise2=new Promise((resolve,reject)=>{
    setTimeout(()=>{
        reject("Timeout Error ");
    },1000)
});



async function getData(){
    
  try{
    const results=await Promise.race([promise1,promise2]);
    console.log(results);
  }catch(error){
      console.log(error);
  }
}


getData();

```


Output:
Timeout Error 




### Promise.any():
- First fullfilled Promise.
- If all rejects, It shows aggregateError.


### Handle Error in Aync/await:




```javascript

try{
  const result=await getUsers();
  console.log(result);
}catch(error){
  console.log(error);
}
```

### sequential and Parellel Execution:


##### sequential:

```javascript
const user=await getUsers();
const products=await getProducts();
```

##### Parallel:

```javascript

const promise=await Promise.all([getUsers,getProducts]);
```
- Executes concurrenctly.


### Unhanlded Promise rejection:

- It occurs only when promise is rejected and it doesnot handle the Appropriate Error handler.

```javascript

const result=reject(new Error("something went wrong"));


result.catch((error)=>console.log(error));

```

when catch is not handled it is unhandled Promise rejection.



for this scenerio:


```javascript
process.on('unhandledrejection',(reason,promise)=>{
  console.error('Something went wrong',reason);
});
```

### diff between throw() and reject():


| throw() | reject() |
| ------- | -------  |
| throw an error inside the function | reject the promise state |
| handle the error in `catch()` | handle the error in try,catch() and await() |

