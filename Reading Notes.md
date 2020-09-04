## Due 9/4

- Clean Code: Various sources on the internet agree that clean code is easy to understand (for you, other coders, and beginners), and easy to maintain. It has clear meaning. Reusability and modularity are also important.

- Array Methods:

1. array.forEach(item => {code for each array item})
2. array.includes(item) returns true if item is in array
3. array.filter(item => checks for boolean) returns a new array with items where boolean returns true
4. array.map(item => code to run on each item) returns a new array with items modified by code
5. array.reduce((total, value) => {applies a function against the value to reduce it to a single value}, startingValue)
6. array.some(item => boolean check) returns true if any value boolean check is true
7. array.every(item => boolean check) returns true if all values boolean checks are true
8. array.sort((a, b) => function returning -1, 0, 1) sorts in order of function
9. Array.from(arrayLikeThing) converts an arrayLikeThing into an actual array
10. Array.of(1, 2, 3) creates an array of all the arguments passed to it

- Class Syntax: Classes are extensible program code templates for creating objects, providing initial state and implementations of behavior.

1. class MyClass {
   // class methods
   constructor() { ... }
   method1() { ... }
   method2() { ... }
   method3() { ... }
   ...
   }
2. new MyClass() then creates a new object with the listed methods
3. Classes are similar to functions with a few differences

- Functions created by class are labelled by a special internal property
- Classes must be called with new
- A string representation of a class constructor in most JavaScript engines starts with class ...
- Class methods are not enumerable, and we usually dont want its class methods when we for loop over it
- Classes always use strict mode

4. Class names are visible inside the class only
5. We can make classes dynamically
6. Classes use get and set
7. Bracket notation can be used to name classes
8. Classes can lose this when passed around, a function can wrap the event, or bind the method to object to prevent this
9. Another way is to add a click = () => {code using this} and this will stay correct

- MDN - Classes

1. Classes are special functions
2. To declare a class you use the class keyword
3. Class declarations are not hoisted
4. Classes can also be expressions and do not have to be named
5. The constructor method is a special method for creating and initializing class objects
6. Extends is used to create a class as a child of another class
7. Super is used to call corresponding methods of super class

- MVC Architecture Tutorial: Model View Controller is a software design pattern

1. MVC Separates all coding concerns into 3 buckets

- Model stores and manages data
- View is the GUI
- Controller is the brains of the app and connects the model and view

- MVC Explained

1. User request information from the controller
2. controller asks model for data
3. the controller tells the view what data needs to be presented
4. the view sends the presentation back to the controller and back to the user

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