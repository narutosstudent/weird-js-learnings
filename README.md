# Weird JS learnings

## void before async functions

When `void` is used before an async function in JavaScript, like `void asyncFunction()`, it serves to:

1. **Run the Async Function Without Waiting:** It starts the async function but does not wait for it to finish (non-blocking).
2. **Ignores the Result:** Any returned value or promise is ignored, and `undefined` is returned instead.
3. **Signals Intent:** It shows that the developer intentionally chose not to handle the promise, making this clear to anyone reading the code.
4. **Avoids Errors:** Prevents potential issues where unhandled promises might lead to warnings or errors.

`void asyncFunction()` is a way to execute an async function where you don't need to handle its result or completion.

It's there purely for the side effects.

## hasOwn vs hasOwnProperty

`hasOwnProperty` is a method of the `Object` prototype. `hasOwn` is a method of the `Object` constructor.

Both check if an object has a property. `hasOwn` is a bit more flexible, as it can check if a property exists on a prototype chain, whereas `hasOwnProperty` only checks if the property exists on the object itself.

The reason `hasOwnProperty` only checks the object itself is because it is a method of the `Object` prototype. So if you have an object that has a property `hasOwnProperty`, it will not be able to call the method, as it will be shadowed by the property.

```ts
const obj = {
  hasOwnProperty: "foo",
};

obj.hasOwnProperty("foo"); // TypeError: obj.hasOwnProperty is not a function
```

`hasOwn` is more recent and stable.
