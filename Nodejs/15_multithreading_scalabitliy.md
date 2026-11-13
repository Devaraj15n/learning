# Multi Threading and Scalability:


### Worker threads:
- Allow the javascript code to execute parallel in separate threads.
- It is useful in CPU-intensive Operations.



```javascript
const {worker}=require('worker_threads');

const worker=new worker('./worker.js');
worker.on('message',(result)=>{
    console.log(result);
})
```

### Clustering:
- build in Modules that handles the nodejs Processes.
- Server has 4 core CPU's , nodejs running on single Cpu. sO Clustering use 4 cpus too.

each worker:
- has its Own thread.
- has its own memory.
- can handle incoming requests.


```javascript
const cluster = require("node:cluster");
const http = require("node:http");
const os = require("node:os");

const numCPUs = os.availableParallelism();

if (cluster.isPrimary) {

    console.log(`Primary process: ${process.pid}`);

    // Create worker processes
    for (let i = 0; i < numCPUs; i++) {

        cluster.fork();

    }

} else {

    // Each worker creates an HTTP server
    http.createServer((req, res) => {

        res.writeHead(200);

        res.end(
            `Hello from worker ${process.pid}`
        );

    }).listen(5000);

    console.log(`Worker started: ${process.pid}`);
}

```

### Diff bewteen Clustering and worker threads

| Worker threads | clustering |
|  ------------- | ---------- |
| creates the mutiple threads | creates the multiple processes |
| share memory through SharedArrybuffer | Process have spearate memory |
| Good for CPU intensive Javascript | Used for Http request }



### Child Process:


Spawn():
- process a large file and returns the stream outputs

```javascript
const express = require("express");
const {spawn} =require('child_process');

const app = express();


const child=spawn('node',['worker.js']);

child.stdout.on('data',(data)=>{
    console.log(data.toString()); // which gives Buffer
});

app.listen(3000, () => {
  console.log("Server listening on port 3000");
});


```
worker.js

```javascript
console.log("Hello from worker.js");
console.log("child is processed");


```

exec():
- runs the command inside the shell and collects its output.
const {exec,execFile} =require('child_process');

- 

```javascript
exec('node --version',(error,stdout,stderr)=>{
      if(error){
        return console.log(error);
      }

      console.log(stdout);
});

```

execFile():
- executes a program directly without starting the shell by default.

```javascript
const {exec,execFile} =require('child_process');


execFile('node',['--version'],(error,stdout)=>{
    console.log(stdout);
});

```

fork():
- create another process and communicate through messages.


```javascript
//index.js
const {fork} =require('child_process');
const child=fork('worker.js');
child.send("Sending Message");

child.on("message",(message)=>[
    console.log(message)
]);

//worker.js

process.on('message',(message)=>{
      console.log(message);


      process.send("Task completed");
});

```


### Diff between spawn() and exec():

spawn() | exec() |
| ----- | ------ |
| Start a process and stream it output | Run the shell comments and buffers it output |
| suitable for large files | Suitable for small commands |


### What happens Nodejs receives 10000 requests:

