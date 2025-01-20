# React useEffect Hook Memory Leak

This repository demonstrates a common error in React applications involving the `useEffect` hook: forgetting to include a cleanup function to prevent memory leaks.  The example shows a component with a `setInterval` that increments a counter. If the component unmounts before the interval is cleared, it will continue to run in the background, leading to potential memory issues.  The solution shows how to correctly implement the cleanup function to resolve the leak.

## How to reproduce

1. Clone this repository.
2. Run `npm install` to install the necessary packages.
3. Run `npm start` to start the development server.
4. Observe the counter incrementing in the browser.
5. Navigate away from the component or refresh the page.
6. **The `setInterval` should stop after the component unmounts (in the correct solution); if not, it's a memory leak.**

## Solution

The solution provided addresses the memory leak by adding a return statement within the `useEffect` hook. This return statement provides a cleanup function that is executed when the component is unmounted or before the next effect runs. This cleanup function clears the interval, preventing the memory leak.