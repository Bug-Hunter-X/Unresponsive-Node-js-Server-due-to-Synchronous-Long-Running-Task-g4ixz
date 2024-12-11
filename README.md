# Unresponsive Node.js Server

This repository demonstrates a common issue in Node.js where a long-running synchronous operation within the request handler blocks the event loop, making the server unresponsive.  The example uses a simple `while` loop to simulate a time-consuming task, but this could be any CPU-bound operation.

## How to Reproduce

1. Clone this repository.
2. Run `node server.js`.
3. Attempt to make multiple requests to `http://localhost:3000`. You'll observe that subsequent requests will be delayed or won't be processed until the initial request completes its long operation.

## Solution

The solution involves refactoring the long-running task to use asynchronous operations (e.g., `setTimeout`, promises, async/await) or offloading the task to a worker thread using the `worker_threads` module.