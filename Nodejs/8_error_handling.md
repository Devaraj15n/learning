#


### What is error handling in Nodejs:

- Process of identifying,catching,Logging and responding to application errors.


common approaches:
1. try/catch.
2. Class error handling.
3. Promise.catch().
4. Express error middleware.
5. Centralized Logging.

### Different types of errors:

1. Syntax error. - Made the syntax wron - missing )
2. Runtime Error. - Access property of null -> const user=null,console.log(user.name)
3. Logical Error. - code runs but produce the wrong result
4. Operational Error. - Other errors (database connnection issue)
5. Programming Error. - programmers made this error.


### what is try/catch:
- it handles exception for the promise.
- promise is awaited in try block

```javascript
try{
    const users=await getUsers;
    console.log(users);
}catch(error){
    console.log(error);
}
```
### Custom error class:
- Custom Error class used to define application errors.

```javascript
class AppError extends Error{
    constructor(message,statusCode){
        super(message);

        this.statusCode=statusCode;
        this.isOperational=true;
    }
}


throw new AppError("User not Found",404);
```

### How to debug the nodejs application:

- console logs.
- error logs.
- Vscode debugger.
- database query logs.
- Performance Monitoring.
- nodejs inspector/


### Uncaught Exception:


- is the Error is not handled in the application.


getUser(){
    throw new AppError("user is not found");
}

getUser();

console.log("application is running");


So `user is not found`. not run the `application is running`.


for this: in Nodejs:

process.on("uncaughtException",(error)=>{
    console.log("Something went wrong",error);
    process.exit(1);
});


IN express.js:

app.use(err,req,res,next)=>{
    
}




