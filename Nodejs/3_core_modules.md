#


### Modules in Node.js
- Reusable block of code to Organise an application
- Commonjs and ESModules.


### CommonJS:

- Module System traditionally used in Nodejs.

//add.js

```javascript
function add(a,b){
  return a + b;
}

module.exports=add;

```

```javascript

const add =require('./add');
console.log(add(1,2));
```

Output:
3


### ES Modules:
- ES Modules uses the Import and Export syntax.

```javascript

//add.js
export function add(a,b){
  return a + b;
}


//index.js
import {add} from './add.js'; //.js is must or it is shown error

console.log(add(1,2)); //Output:3


```

### Diff between require() and import():

require() | import()
---- | ----
Commonjs    | ES Modules
Uses module.exports | use export
Can be called dynamically | Static imports are resolved before execution

### FS Modules:
- Provides filesystem operations


Allows us to 

- read file
- Write File
- Delete File
- Update File
- File Information
- Create Directories.

```javascript


const fs=require('fs');


fs.readFile("test.txt",'utf8',(err,data)=>{

  if(err){
    console.log(err);
    return;
  }
    console.log(data);
});

```


### diff between FileSync() and File():


readFileSync() | readFile()
---- | ----
Synchronous | Asynchronous
Block the Javascript thread | Non Blocking I/O operations
Use callbacks,Promise API | return the API Directly

### Path Module:

- Works with File and Directory Paths.

```javascript

const path = require('path');
console.log(path.join(__dirname,"uploads",'test.txt'));

```

output:
/uploads/test.txt

### Buffer Module:
- Handles the binary data in Nodejs.

Used for:
- process the Imgages.
- process the Videos.


```javascript
const buffer_string=Buffer.from('hello');
console.log(buffer_string); // <Buffer 68 65 6c 6c 6f>
console.log(buffer_string.toString()); // hello

```

### Streams In Nodejs:

- Allows to process large data into the smaller chunks.


Fout types:
1. Readable
2. Writable.
3. Duplex.
4. transform.

```javascript

const fs=require('fs');

const stream=fs.createReadStream("uploads/test.txt");

stream.on('data', (chunk)=>{
  console.log(chunk); // <Buffer 61 61 61 62 62 62 62>
  console.log(chunk.toString()) // aaabbbb

});


```



### Event Emitter:

- Built in Nodejs Modules.
- Can create and handle Custom Events.

```javascript

const EventEmitter=require('events');

const event=new EventEmitter();


event.on('message',(data)=>{
    console.log(data);
});



event.emit("message","Hello Devaraj");

```

### diff between on() and once():

on() -> Executes Mulitple times.
once() -> Executes only Once.


```javascript
const EventEmitter=require('events');

const event=new EventEmitter();


event.on('message',(data)=>{
    console.log(data);
});

event.once("login",(data)=>{
      console.log("Login Successful");
});

event.emit("login");
event.emit("login");
event.emit("login");

event.emit("message","Hello Devaraj");
event.emit("message","Welcome");
event.emit("message","How Are you");

```

Output:
Login Successful
Hello Devaraj
Welcome
How Are you

### Global Object in Nodejs:
- Availble throughout the application without explicitely import them

Some Example:

global
Buffer
console
setTimeout()
setInterval()


### process Object:
- provides the information and control over the current Nodejs Process.

process.env.NODE_ENV
process.pid
process.version







