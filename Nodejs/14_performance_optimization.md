#



### How to improve nodejs application:
- Avoid Blocking Event Loop.
- Caching.
- pagination.
- Use connection Pooling.
- imPlement background jobs.
- Monitor CPU and Memory Usage.
- Use Stream for Larger files.


### Memory leaks:


const user={
    name:"deva",
    age:29
}

Memory:
- Store the data information in the memory.

- garabage collector in nodejs remves the memory when the objecvt is not referenced.

Memory leak:
- When the oject is assigned and it it still referenced it . 
- garabage collector is still not able to remove it.

Common Usage of Memory leaks:
- Unremoved Event Listeners:

```javascript
    const EventEmitter = require('events');
    const event=new EventEmitter();


    function handleEvent(){
        console.log("handle");
    }

    event.on('data',handleEvent);


    event.off('data',handleEvent)
```

- Unbound cache2:

    - Imagine every user data in the array:

- unclosed Connections:
    - creating database connection and didn't properly closed it.


- Accidental Global Variables:
- Long lived references:

### Garbage collecton:
- Process of identifying and reclaming memory occpied by the object that are no referenced.
- v8 engine garbage collector is used in Nodejs.


### heap and Stack Memory:


- Stack Memory:
    - Mange function calls and Execution Contexts and Local Varaibles.

- Heap memory:
    - Stores Object and Dynamic Data.

### How do you monitor the memory usage in Nodejs:
process.memoryUsae();


{
    rss:50000000,
    heapTotal:20000000,
    heapUsed:5000000,
    external:2000000,
    arrayBuffers:10000000
}

rss-> Nodejs application used this memory.
heapTotal -> Total heap Memroy.
heapUsed -> heap memory is used.

### Compression in Nodejs:

const compression=require('compression');

app.use(compression);

- compression is reduced the size of http response bodies,improves network performance.

### Load balancing:
- Load Balancing which sent the request to instance or servers.


### horizantal scaling :
- Adding more application servers or instances to the servers.


### Vertical scaling:
- Increase the sie of the instance such as RAM and CPU.

### 


