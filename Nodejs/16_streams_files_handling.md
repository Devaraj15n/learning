#


### Streams in Nodejs:
- Process data incrementaly without loading the entire data.

- large files,video streaming and network communication

### four types of streams:
1. readable. - (read Data)
    const fs=require(fs);

    const readfile= fs.createReadStream('input.txt');

    readable.on('data',(chunk)=>{
        console.log(chunk);
    });

2. Writable. - (Write Data):

    const fs=require('fs');
    const writable=fs.createWriteStream("output.tx');
    writable.write("Hello from Nodejs");
    writable.end();

3. Duplex. - (read and write) eg: Sockets.

    const net=require(net);

    net.createServer((socket)=>{
        socket.on('data',(data)=>{
            console.log("message is received",data);
        });

        socket.write("Hello from server");
    })

4. transform. - (Read, write and update)

    const { Transform } = require("stream");

    const upperCase = new Transform({

        transform(chunk, encoding, callback) {

            const result = chunk.toString().toUpperCase();

            callback(null, result);
        }
    });

    upperCase.on("data", (data) => {
        console.log(data.toString());
    });

    upperCase.write("hello nodejs");
    upperCase.end();


### pipe:
- Pipe connects readable to writable.

const fs=require('fs');

const readable =fs.createReadStream('input.txt');

const writable= fs.writeReadStream('output.txt');


readable.pipe(writable);


