# Stale Closures in React Native useEffect Hook

This repository demonstrates a common, yet subtle, bug in React Native applications involving the `useEffect` hook and stale closures.  When a function is included in the dependency array of `useEffect`, it's important to understand how closures work.  In this example, the function `myFunc` references the `count` variable from its enclosing scope at the time of its creation, not at the time of its execution. Thus, even though `count` changes, `myFunc` will always use its initial value.

## Steps to Reproduce

1. Clone the repository.
2. Run `npm install` to install dependencies.
3. Run the app on an emulator or physical device.
4. Observe that the console log always shows `myFunc called with count: 0`, even as you increment the counter.  This is because `myFunc` maintains a reference to the initial value of `count`.

## Solution

The solution involves refactoring to avoid relying on the closure by using a functional approach or by creating the function inside the useEffect hook itself. The solution also demonstrates best practices of using functional updates to avoid issues with state updates in React.  

## License

MIT