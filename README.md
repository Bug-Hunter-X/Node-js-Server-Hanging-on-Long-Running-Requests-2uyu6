# Node.js Server Hanging on Long-Running Requests

This repository demonstrates a common issue in Node.js applications where the server hangs when a request takes a significant amount of time to process.  This often stems from the single-threaded nature of Node.js.

## Bug

The `server.js` file contains a simple HTTP server that simulates a long-running task (a 5-second delay).  Because Node.js is single-threaded, during this delay, the server cannot handle any other incoming requests, effectively causing it to hang.

## Solution

The `server-solution.js` file provides a solution to this problem by using worker threads, which allow for parallel processing. This prevents the main thread from being blocked, enabling it to continue handling other requests.

## Setup and Run

1. Clone this repository
2. Run `npm install`
3. Run `node server.js` to see the hanging behavior.
4. Run `node server-solution.js` to see the corrected behavior using worker threads.  Observe that the server remains responsive during the long-running task.  You can test concurrency by opening multiple browser tabs simultaneously.