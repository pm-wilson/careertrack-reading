## Due 9/3

- Promise

1. The Promise represents the eventual completion or failure of an asynchronous operation, and its resulting value, and is always in one of these states: pending, fulfilled, rejected.
2. They guarantee the callbacks will not be called before the completion of the current JavaScript event loop, Callbacks added with then() will be called even after success or failure of the asynchronous operation, and multiple callbacks may be added by calling then() several times in their order.
3. Chaining happens when then() is used to link together multiple operations dependent on the previous step.
4. Once a promise is settled, promise.then(), promise.catch(), and promise.finally() can add action.
5. Promises can be nested, and more than one can be nested within.
6. Promise() creates a new Promise object.

- Destructuring

1. Use this to assign values from arrays or properties from objects.

- Spread

1. Allows an iterable (array or string) to be expanded in places where 0 or more arguments/elements are expected, or an object expression to be expanded in places where 0 or more key-value pairs are expected.

- Rest

1. The rest parameter syntax allows us to represent an indefinite number of arguments as an array.

- TDD, Where Did it All Go Wrong

1. Without tests the code is hard to maintain.
2. Customers don't look at the tests.
3. Test behaviors, not implementation details.
4. New tests should be written for new requirements as they are added, not details.
5. Refactoring should not require new tests.
6. Think of test as behavior
7. To write tests, start by writing a test that doesn't work, make the test work by any means necessary, refactor and eliminate all duplication.

- What the heck is the event loop anyway

1. The call stack handles each event one thing at a time. This is JavaScript.
2. The browser gives us api's to add functionality. When they are done, they add events to the task queue. The event loop adds this to the stack when it is empty.
3. setTimeout() will wait and execute the code, but might take longer if it is waiting for something else so it is really a minimum time out.
4. Browser can refresh 16 times a second, but will wait for the stack to clear first.
5. Best to not block the stack with slow code.
