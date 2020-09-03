## 01 JS Fundamentals Due 9/3

- Initializing Objects on MDN:

1. Basics: Within an object x:x === x, this works with multiple variables, and methods. Functions can be called with obj.functionName().

2. Computed Properties: Property names can be dynamic using [], they can have functions assigned, the key can be built with a function call, or constructed as a string.

- Inheritance and Classes:

1. Creation: Classes are created with **class className {constructor, methods (not separated with comma)}** Classes are block scoped.

2. Statics: Static methods has the prefix 'static', it is dynamic, getter names can also be static and is dynamic. They are not called by this.

3. Extends: Classes are instances of an object, an extended object is an instance of what it extended. A class can extend null and is not an instance of object (I am still a little confused on this), but it sounds like null can be passed with an extension. Extend works through multiple levels.

- Destructuring on MDN:

1. Array Destructuring: Destructuring works be allowing the array brackets on both sides when declaring a variable. leading commas can be used to ignore previous values.

2. String Destructuring: Strings destructure just like arrays, missing characters from the definition results in undefined.

3. Object Destructuring: Objects can be destructured using curly braces on the left side of the =, like with arrays and square brackets. Multiple objects can be destructured at once and objects can mix with arrays.

4. Destructuring with Defaults: Defaults can be provided when destructuring, they can make up for missing values, in objects without references, and if the value is undefined.

5. Destructuring Function Parameters: Paramaters can be given default values. Multiple values can be mixed with arrays and objects this way. Or for missing array values.

- Destructuring with Alias: Object property values can be assigned to new variables with different names. They can also be given default values at the same time or as a parameter with a new name or default value.

- Rest on MDN:

1. Rest as a Parameter: Rest ... must be the last parameter, can get all other parameters and eliminates arguments.

2. Rest while Destructuring: Rest can be used to assign a variable or to concat an array.

- Spread on MDN:

1. Array Spread: Works kind of like saying all, expands an array with a ... prefix. A spread of an empty array is nothing. Spread can be used anywhere and can be used as function parameters, but not with using apply.

- Default Parameters on MDN:

1. Function Defaults: Default parameters can be added for values that might be missing. They are used when undefined is passed, but not when a value is given, evaluated at runtime and can also be a function.
