# Node.js Web Development
 Node.js training

 # Begin -- ls.js:

## Overview

The given JavaScript code uses the built-in `fs` (File System) module in Node.js and demonstrates how to read and list files in a directory asynchronously. It employs the `async/await` syntax for handling promises.

## Code Breakdown

### Module Import

```javascript
const fs = require('fs').promises;
```

Here, the `fs` (File System) module is being imported using Node.js's `require` function. Specifically, it's importing the `promises` API of `fs`, which provides promise-based versions of the callback-based functions in `fs`.

### Asynchronous Function

```javascript
async function listFiles() {
    try {
        const files = await fs.readdir('.');
        for (const file of files) {
            console.log(file);
        }
    } catch (err) {
        console.log(err);
    }
}
```

This code defines an asynchronous function named `listFiles`. The function is declared with the `async` keyword, which means it will return a promise and allows the usage of the `await` keyword inside it.

- In the `try` block, `await fs.readdir('.')` is used to read the directory contents of the current directory (`'.'` represents the current directory). The `await` keyword pauses execution of the function until the promise is either fulfilled or rejected, and then resumes execution and returns the resolved value. The result (an array of filenames) is stored in the `files` constant.

- Next, a `for...of` loop is used to iterate over the `files` array and each filename is logged to the console using `console.log(file)`.

- The `catch` block captures any errors that occur while reading the directory or iterating over the files. If an error occurs, it's logged to the console using `console.log(err)`.

### Function Invocation

```javascript
listFiles();
```

This line calls the `listFiles` function, which triggers the file reading and logging operation.

## Usage

This code snippet is a useful starting point for scripts that need to list files in a directory. It can be modified to specify different directories or to perform more complex operations on the listed files. Note that this script requires Node.js and its File System module to run.

# End -- ls.js.

# Begin -- ls2.js:
## Overview

The given JavaScript code uses Node.js's built-in `fs` (File System) module and demonstrates how to read and list files in a directory. This version of the code allows for optional command-line input to specify a different directory. The script employs the `async/await` syntax for handling promises.

## Code Breakdown

### Module Import

```javascript
const fs = require('fs').promises;
```

Here, the `fs` (File System) module is being imported using Node.js's `require` function. Specifically, it's importing the `promises` API of `fs`, which provides promise-based versions of the callback-based functions in `fs`.

### Asynchronous Function

```javascript
async function listFiles() {
    try {
        var dir = '.';
        if (process.argv[2]) dir = process.argv[2];
        const files = await fs.readdir(dir);
        for (let fn of files) {
            console.log(fn);
        }
    } catch (err) {
        console.error(err);
    }
}
```

This code defines an asynchronous function named `listFiles`.

- The `dir` variable is initially set to `'.'`, which represents the current directory.

- The `if (process.argv[2]) dir = process.argv[2];` line checks whether a command-line argument was provided (Node.js command-line arguments are accessible via the `process.argv` array; `process.argv[2]` would be the first user-provided argument, as `process.argv[0]` is the path to the Node.js executable and `process.argv[1]` is the path to the executing script). If an argument is provided, it's assigned to `dir`, changing the directory that will be read.

- The `await fs.readdir(dir)` expression is used to read the directory contents of the specified directory. The `await` keyword pauses the function execution until the promise is either fulfilled or rejected, and then resumes the execution and returns the resolved value. The result (an array of filenames) is stored in the `files` constant.

- A `for...of` loop is used to iterate over the `files` array and each filename is logged to the console using `console.log(fn)`.

- The `catch` block captures any errors that occur while reading the directory or iterating over the files. If an error occurs, it's logged to the console using `console.error(err)`.

### Function Invocation

```javascript
listFiles();
```

This line calls the `listFiles` function, triggering the file reading and logging operation.

## Usage

This script is a practical example of how to list files in a directory using Node.js, and it allows the directory to be specified via command-line argument. The code can be modified to work with different directories or to perform more complex operations on the listed files. Note that this script requires Node.js and its File System module to run.

# End -- ls2.js

# Begin -- app.js

## Overview

The given JavaScript code uses Node.js's built-in `http` module to create a simple HTTP server. When accessed, the server responds with a plain text message "Hello, World!".

## Code Breakdown

### Module Import

```javascript
const http = require('http');
```

The `http` module is imported using Node.js's `require` function. This module includes functions for creating HTTP clients and servers.

### HTTP Server Creation

```javascript
http.createServer(function (req, res) {
    res.writeHead(200, {"Content-Type": 'text/plain'});
    res.end('Hello, World!\n');
}).listen(8124, '127.0.0.1');
```

- `http.createServer()` is a method that creates an HTTP server. It takes a request listener function as a parameter. This function is automatically added to the `'request'` event and is invoked each time the server gets a request.

- The request listener function has two parameters: `req` (the request object) and `res` (the response object).

- `res.writeHead(200, {"Content-Type": 'text/plain'});` sends a response header to the request. `200` is the HTTP status code for "OK", and the `Content-Type` of `text/plain` indicates the data being sent back to the client is plain text.

- `res.end('Hello, World!\n');` ends the response process, and optionally, sends a data string. Here, it sends a "Hello, World!" message.

- The `listen()` method makes the server listen at the specified IP address and port. In this case, it's `127.0.0.1` (localhost) and port `8124`.

### Server Status Message

```javascript
console.log("Server running at http://127.0.0.1:8124");
```

This line prints a message to the console indicating that the server is running and listening for incoming requests at the provided address and port.

## Usage

This is a simple example of how to create a basic HTTP server using Node.js. It can be a starting point for more complex servers, where you might handle different types of requests, serve different content types, or interact with a database. Please note that you'll need to have Node.js installed to run this script.
