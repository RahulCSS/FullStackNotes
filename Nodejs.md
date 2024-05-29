## Introduction to Node.js

Node.js is an open-source and cross-platform JavaScript runtime environment. Node.js runs the V8 JavaScript engine, the core of Google Chrome, outside of the browser.

A Node.js app runs in a single process, without creating a new thread for every request.When Node.js performs an I/O operation, instead of blocking the thread and wasting CPU cycles waiting, Node.js will resume the operations when the response comes back.This allows Node.js to handle thousands of concurrent connections with a single server without introducing the burden of managing thread concurrency.

## Why Nodejs for wev server
1. Non-Blocking I/O model
2. Scalability
3. Low Overhead
4. Rich Ecosystem

## MERN (MongoDB, Express.js, REeact, Node.js)
1. Basic JavaScript knowledge
2. Node.js Fundamentals
3. Module and Package Managenement (npm)
4. Server Concepts wiht Node.js
5. Web Server with Express.js
6. RESTful API with Express.js
7. MVC Architechture
8. Mongo DB
9. Moongoose
10. JWT Authentication
11. React Integration
12. Integration of MERN App
13. Error handlind, deployment and performance optimazation
14. Build Projects

## Fs Module
The fs module in Node.js stands for "File System," and it provides a way to work with the file system on your computer or server.

**Synchronous vs. Asynchronous Operations**  
Most fs module functions come in both synchronous and asynchronous versions.
- fs.readFile()) allow non-blocking file operations, while  
- fs.readFileSync()) block the Node.js event loop until the operation is complete.

**Working wit Directories**
- fs.mkdir() -> to create a directory
- fs.rmdir() -> to reaname a directory
- fs.readdir() -> to list a directory
- fs.stat() -> to get information about directory
- fs.watch(), fs.watchFile() ->  to watch for changes to files and directories
- fs.exists() -> to check if a directory exists
- fs.existsSync() is a synchronous method, so it can block the Node.js event loop. For asynchronous approach, use fs.access().

1. **Reading files**
```javascript
const fs = require('fs');
let content = fs.readFileSync('path/to/file');
console.log(content);
console.log(content.toString());
console.log(content+"");
```
2. **Writing files**  
Writing files creates or overwrites the contents.   
```javascript
const fs = require('fs');
fs.writeFileSync('path/to/file','content to write');
```

3. **Updating files**
```javascript
const fs = require('fs');
fs.appendFileSync('path/to/file','content to add to existing file');
```
4. **Renaming and Deleting files**
```javascript
const fs = require('fs');
fs.rename('path/to/oldfile','path/to/newfile');
fs.unlink('path/to/file);
```

## Path Module
1. **path.join([...paths])**
```javascript
const path = require('path');
const fullPath = path.join('folder', 'subfolder', 'file.txt');
```
2. **path.resolve([...paths])**
```javascript
const path = require('path');
const absolutePath = path.resolve('folder', 'subfolder', 'file.txt');
```
3. **path.basename(path)**
```javascript
const path = require('path');
const fileName = path.basename('/path/to/file.txt');
```
4. **path.dirname(path)**
```javascript
const path = require('path');
const dirName = path.dirname('/path/to/file.txt');
```
5. **path.extname(path)**
```javascript
const path = require('path');
const extension = path.extname('/path/to/file.txt');
```
6. **path.parse(path)**
```javascript
const path = require('path');
const pathInfo = path.parse('/path/to/file.txt');
```
7. **path.normalize(path)**
```javascript
const path = require('path');
const normalizedPath = path.normalize('/path/to/../file.txt');
```
7. **path.isAbsolute(path)**
```javascript
const path = require('path');
const isAbsolute = path.isAbsolute('/path/to/file.txt');
```
7. **path.relative(path from,to)**
```javascript
const path = require('path');
const relativePath = path.relative('/path/from', '/path/to');
```

### Excercise
**Copy a file from one folder to another using Node.js**
```javascript
const fs = require('fs');
const path = require('path');

// Define the source and destination file paths
const sourceFilePath = '/path/to/source-folder/source-file.txt';
const destinationFilePath = '/path/to/destination-folder/destination-file.txt';

// Create a readable stream from the source file
const readStream = fs.createReadStream(sourceFilePath);

// Create a writable stream to the destination file
const writeStream = fs.createWriteStream(destinationFilePath);

// Pipe the data from the source file to the destination file
readStream.pipe(writeStream);

// Handle any errors that may occur during the copy process
readStream.on('error', (err) => {
  console.error(`Error reading the source file: ${err}`);
});

writeStream.on('error', (err) => {
  console.error(`Error writing to the destination file: ${err}`);
});

// When the copy is complete, log a success message
writeStream.on('finish', () => {
  console.log('File copied successfully.');
});
```

## Server Side Development
1. **Server-Side Development**
    - Server
    - Server-Side Technologies
    - Server Logic
    - Security
2. **Client-Side Development**
    - Client
    - Client-Side Technologies
    - Front-End Frameworks
    - User Experience
    - Performance
3. **Database Client**
    - Database Management System(DBMS)
    - Database Client Libraries
    - ORM (Object-Relational Mapping)
    - Data Access

## Server Side Development using http module
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  // Set response header
  res.setHeader('Content-Type', 'text/plain');
  
  // Write response content
  res.write('Hello, World!');
  
  // End the response
  res.end();
});

const port = 3000;
const host = 'localhost';

server.listen(port, host, () => {
  console.log(`Server is listening on http://${host}:${port}`);
});
```
**Json in the resposnse**
```javascript
const http = require('http');

const server = http.createServer((req, res) => {
  // Set response header with Content-Type as application/json
  res.setHeader('Content-Type', 'application/json');
  
  // Define JSON data
  const jsonData = {
    message: 'Hello, World!',
    date: new Date(),
  };

  // Convert JSON object to a JSON string
  const jsonResponse = JSON.stringify(jsonData);

  // Write JSON response
  res.write(jsonResponse);
  
  // End the response
  res.end();
});

const port = 3000;
const host = 'localhost';

server.listen(port, host, () => {
  console.log(`Server is listening on http://${host}:${port}`);
});
```
We use JSON.stringify() to convert the JSON object into a JSON string.

## Nodemon
Nodemon is a tool that helps you develop Node.js applications by automatically restarting the Node.js process whenever changes are detected in your project's files.
1. **Installation**
```
npm install -g nodemon
```
```
npm install --save-dev nodemon
```
2. **Basic Usaage**
```
nodemon your-app.js
```