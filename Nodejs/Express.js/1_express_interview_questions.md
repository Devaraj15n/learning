#


### Express.js

- Lightweight Nodejs Framework.
- Used to Build Rest API's and Web Applications.


Simplifies:
- Routing
- Middleware.
- Request Handling
- Response Handling
- Error Handling.


### How do you create Express web Server:

```javascript
const express=require('express');


const app=express();


app.get('/',(req,res)=>{
  res.send("Get Method is called");
    // console.log("Get Method is called");
});

app.listen(5000,()=>{
  console.log("App is listening in",5000);
});

```

### Middleware:
- Is a function that executes during the request and response cycle.

It receives:
- req
- res
- next

```javascript

const logger=(req,res,next)=>{
    console.log(req.method,req.url);
    next();
};

app.use(logger);

```


### types of Middleware:

1. Application Level:

    - Is registered using app.use().
    - It is middlewarw accross application Level.

```javascript
const express=require('express');

const app=express();


app.use((req,res,next)=>{
console.log("Application Middleware");
next();
})


app.get('/',(req,res,next)=>{
// console.log("User list is shown");
res.send("User list is shown");
});


app.listen(5000);

```


2. Router Level Middleware:
    - Attached using the `router.use()`.
    - It is works inbetween the router level.


```javascript
//index.js
const express=require("express");
const middleware=require('./middleware.js');

const app=express();

app.use(middleware);


app.listen(5000);


//middleware.js

const express=require("express");

const router=express.Router();

router.use((req,res,next)=>{
  console.log("Middleware Function");
  next();
});


router.get("/",(req,res,next)=>{
    res.send("GET call is executed!");

});

module.exports=router;

```


3. Build in Middleware:
    - Express provides the build-in Middleware for special operations.

app.use(express.json());

app.use(express.urlencoded({extended:true}));

app.use(express.static(public));


4. Third Party Middleware:
    - Is created by external developers and install using npm.


```javascript
app.use(cors); // Allow cross origin Requests
app.use(helmet);  // Add security related http Requests
app.use(morgan); // Add logging to the Application
app.use(cookie-parser); //Parses cookie
app.use(express-rate-limit); // Limited Repeated request
```

5. Error handling Middleware:

    - Handles the error in Express application.

    ```javascript

    app.use((err, req, res, next) => {
        console.error(err.message);

        res.status(500).json({
            message: "Internal Server Error"
        });
    });


    app.get("/users", (req, res, next) => {
        const error = new Error("Something went wrong");

        next(error);
    });

    ```

### Diff between app.use() and app.get();

|    app.use() | app.get() |
| ------------ | ----------- |
| use for Middlewares | Use get Method Http Calls |


### express.Router():

- Handles the Router in Express.

```javascript
//index.js
const express = require("express");
const router=require('./router.js')
const app = express();


app.use('/api',router);


app.listen(3000, () => {
  console.log("Server listening on port 3000");
});

//router.js
const express=require('express');


const router=express.Router();


router.get('/user',getUsers);
router.get('/products',getProducts);


module.exports=router;
```

### req.params,req.query and req.body:

- Access the incoming request.

```javascript
const express = require("express");
const app = express();


///users/10
app.get('/users/:id',(req,res)=>{
    console.log(req.params);
});

///users?page=10
app.get('/users',(req,res)=>{
    console.log(req.query.params);
});

///users
app.post('/users',(req,res)=>{
    console.log(req.body);
});

app.listen(3000, () => {
  console.log("Server listening on port 3000");
});


```


### Error handling Middleware:
- Handle the error in whole application
```javascript

app.use((err,req,res,next)=>{
    console.log(err);
    res.status(500).json({
        success:false,
        message:err.message
    });
});

```

### Diff Between next() and next(err):

next() -> passes the control to next middleware.
next(err) -> Passes the control to error middleware.


### CORS:
- cross origin Resource Sharing.
- security mechanism controls the webpage can access the resource only allowed origin.


const cors = require('cors');


app.use(cors({
    origin:"http://localhost:5173"
}));

### Body-Parser:


- handles Middleware of incoming requests.

app.use(express.json());
app.use(express.urlencoded({extended:true}));


### How to implement Pagination in Express.js

- Pagination retrives records in smaller groups instead of entire dataset.

```javascript

app.get('/users',(req,res)=>{
    const page=req.query.page;
    const limit=req.query.limit;

    const offset=(page-1) * limit;

    const users=await User.findAll({
        limit,
        offset
    });

    res.json(users);
});

```

### What is REST API's:

- Representatioal State Transfer.
- Architecturial Style for designing the API's from resource.

| METHOD | Purpose |
| ------ | ------- |
| GET | retrieve Data |
| POST | create Data |
| PUT | Replace a Resource |
| patch | Partially Update a Resource |
| Delete | Delete Resource |

### HTTp Status Code:

5 categories:

1xx - Informational - Request received

2xx - Success       - Request Completed Successfully.

3xx - Redirection   - Further Action or Redirection Required.

4xx - Client Erro   - Problem with the client request.

5xx - Server Error  - problem in the Server.


IMportant Satus codes:

**1xx-informational:**

100 - Continue

101 - Switching protocols

**2xx- Success:**

200 - ok - Get Request Successfully

```javascript
app.get('/users',(req,res)=>{
        res.status(200).json({
            message: "Users fetched Successfully"
        });
});

```

201 - created  - new User or request created

```javascript
app.post('/users',(req,res)=>{
        res.status(201).json({
            message: "Users Created Successfully"
        });
});

```
202 - Accepted - Request accepted for processing

204 - No content - Successful request but no response body. 

**3xx - Redirection:** - `starts from 301 not 300`

301 - Moved Permanently - Permanent URL Change.

302 - Found - Temporary Redirection.

304 - Not Modified - Cached Resource is still valid.

307 - Temporary Redirect - Temporary Redirect Preserves Method.

308 - Permanent Redirect - Permanent Redirect Preserves Method.


**4xx - client Error**

400 - Bad Request - Invalid Request Data

res.status(400).json({
    message:"Invalid Request Data"
});

401 - unAuthorized - Authentication required or failed
 
 res.status(401).json({
    message:"Please login first"
 })

403 - Forbidden - Users' deosnot have permission

 res.status(402).json({
    message:"Users doesnot have Permission"
 });

404 - Not found - Resource or API's doesnot Exist

res.status(404).json({
    message:"Users Not Found"
});

405 - Method not Allowed - Http method not supported

409 - Conflict - Duplicate Email or conflict Data

422 - Unprocessable Content - Validation Error

429 - Too many Requests - rate Limit Exceed


**5xx - Server Error:**


500 - Internal Server Error - unexpected Server Error

501 - Not Implemented - Server doesn't support functionality

502 - bad gateway - Invalid response from Upstream  gateway.

503 - Server Unavailable - Server temporarily Unavailble

504 - gateway Timeout - Upstream Server Timeout.





