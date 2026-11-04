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



