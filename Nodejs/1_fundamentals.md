#

### Nodejs:

- Nodejs is a runtime environment which run javascript in the server.
- V8 Engine.


Example:
- real time applications
- backend
- Microservices.
- Chat applications



console.log("Hello Nodejs"):

### Main features of Nodejs:


- Asysnchronous.
- Event Dirven Architecture.
- Non blocking I/O operations.


### diff between Javascript  and Nodejs

Javascript  | Nodejs
--- | ---
Programming Language |   Runtime Environment
Used in Browser | Used in Server
Used to Manipulate the Dom | Used to Call the API and backend works


### Javascript Engine:

- V8 engine is open source Engine
- Developed by Google.


### NPM:

- Node Package manager.
- Used to install ,manage and share Packages.


```javascript
npm init -y // install package.json
npm install // install packages
npm uninstall // uninstall packages
npm update // update packages
npm run dev // run custom scripts


```


### Package.json

- contains project information,scripts and dependencies.

```node
{
    name:"node-app",
    version:1.0,
    main:"script.js",
    script:{
        start: "node server.js",
        dev:"nodemon server.js"
    },
    dependencies:{
        "express":"^5.0.0"
    }
}

```



### package-lock.json

- It have Exact dependencies version and installed in project.



### Dependencies and DevDependencies

Dependencies:
    - Packages required to run the application.

    npm install express

DevDependencies:
    - Packages required in development and testing.

    npm install nodemon --save-dev


### Diff between nodejs and express.js


Nodejs | Express.js
---- | ----
Javascript runtime | Web framework
Provides HTTP and web API's | existing routes and middleware
create server using build-in modules | Built on top of modules

### Limitations of Nodejs

- CPU intensive operations can block the Main Javascript thread.
- Aysnchronous operations need to proper handle and if not it would affect the performance.
- Memory leaks can affect the Application performance


Node js is used for I/O intensive application.


    





 