## Due 9/15

- Redis (https://aws.amazon.com/redis/)

1. Remote Ditionary Server is an open source key-value data store
2. It keeps information in memory rather than on the hard drive to speed up response times
3. Memcached is a similar open source data store, but doesn't offer the same features
4. Redis data types include strings, lists, sets, sorted sets, hashes, bitmaps, hyperloglogs
5. Redis is good for caching with its low latency, chat/messaging with its variety of data structures, gaming leaderboards with sorted sets, session storage with low latency and high scalability, media streaming with its ability to manifest files, geospacial tasks with data structures, Machine learning with its ability to process live data, and real time analytics by using it with Apache Kafka and Amazon Kinesis.
6. It works well with JavaScript, Node, and many other languages
7. AWS can fully manage it

- Queue

1. A data structure that handles elements in sequence like a stack
2. Enqueue adds an item to the end of the line
3. Dequeue takes an item away from the front of the line
4. isEmpty() returns a boolean
5. Top() returns the next in line

- Task Queue Overview

1. One kind of queue handles tasks one at a time until finished
2. Another kind has the ability to schedule tasks for a specific time in the future

- Task Queue - FIFO

1. First in first out handles items in a queue in the order they were added, always doing the oldest item next
2. Sometimes certain tasks have a higher priority and we would want those to skip to the front of the line
3. Having three priority levels would let the highest priority items get handled first and the least priority messages sent when all others have been handled
4. Sometimes it is good to reevaluate the queues, especially if one priority level tends to get more volume

- Bull QUick Start

1. Bull is a node library that uses a fast queue system with redis.
2. Bull can be installed with (npm install bull --save)
3. It needs a redis server running and can be installed using Docker
4. a queue is created with (const myFirstQueue = new Bull('my-first-queue'))
5. A producer is a node program that adds jobs to a queue
6. A consumer or worker is a node program that defines a process
7. Listeners listen to events that happen in the queue
8. Job lifecycles are job added, wait/delayed, active, completed/failed, finished
9. Jobs can be handled FIFO (default), LIFO, Delayed for an amount of time, Prioritized, Repeatable

## Due 9/14

- Web Scraping JavaScript (https://www.scrapingbee.com/blog/web-scraping-javascript/)
1. Request, Axios, and Superagent are examples of HTTP clients that work with node and JS
2. You will need something to interpret the results of the data you scrape, and doing it manually can be tough. An HTML parser can help if you use regular expressions to look for a match. 
3. Cheerio is a light weight and efficient library that uses JQuery on the server. It will not run css, javascript or render any dom elements.
4. You might use Cheerio to fetch the dom element, then use text() to get the text
5. JSDOM (npm install jsdom axios) can be used to interact with websites automatically and do things like click and manipulate the DOM, this can create a bot that goes around interacting with web sites.
6. Puppeteer (npm install puppeteer) is a hight level API that controls a headless version of chrome. It can take screenshots or generate pdfs of pages, generate pre-rendered content, or automate user interactions (keyboard inputs, form submissions, navigation, etc)
7. Nightmare (install nightmare) is another option for a high level browser automation
8. To scrape and not get blocked you need to look more like a user to the target and less like a robot.
9. The first thing to watch out for is the headers on your request.
10. One option is to use a headless version of chrome, this will behave exactly like the browser. Selenium and Puppeteer are the two most common drivers for Headless Chrome
11. Transport Layer Security (TLS) can give you away, you need to copy variables that are used typically in a given combination
12. You also need to emulate human behaviour with proxy servers making multiple fast requests to come from different locations. The TOR network hides traffic well, but is often blocked or slow due to the rerouting it does. 
13. Captchas might need to be solved with something like 2Captchas or DeathByCaptchas
14. Requesting certain patterns or at certain rates can raise automated suspicion to your scraping

- MDN - QuerySelector
1. querySelector() returns the first element that matches the specified selector.
2. Syntax: element = document.querySelector(selectors);
3. The selectors must be a valid CSS selector string
4. The match returns as an object

- MDN - QuerySelectorAll
1. querySelectorAll() returns an static array of all the elements that match the specific selector.
2. Syntax: elementList = parentNode.querySelectorAll(selectors);
3. The selectors must be a valid CSS selector string
4. The matches can be accessed like an array

## Due 9/9

- PostgreSQL Joins

1. Inner Join creates a table with rows that match the joined column values
2. Left  Join adds the second table values if the column matches and includes all the first table values
3. Right Join is the opposite of Left Join
4. Full Outer Join adds a row if either table has a matching value

- one to one

1. A one to one relationship is when a row can be linked with only one row in another table and vice versa. 

- one to many

1. A one to many relationship is when a row in a table can be linked with many rows in another table, but that row is linked to other tables, like an author can have many books, but each book has only one author

- many to many

1. A many to many relationship is when multiple rows in a table can be linked with multiple rows in another table, like people who build lego sets. Each lego set can be built by different people, and different people can each build different lego sets.

## Due 9/8

- Computer Basics

1. CPU is the brain of a computer
2. RAM is the short term memory
3. Hard drive is long term storage
4. The motherboard is where everything in the computer connect to
5. The OS is used to control the computer

- Introduction to PostgreSQL Insert

1. INSERT lets you add a new row onto a table
2. PostgreSQL will get an error if any colum data is missing.
3. If you need a single quote in a string, use two single quotes
4. Dates are added as YYY-MM-DD

- PostgreSQL SELECT

1. SELECT queries data from a table
2. You can select data from specific or all columns
3. You can format the data using || to concat

- PostgreSQL UPDATE

1. Update modifies data on a table
2. If WHERE is not included, update will modify all rows

- PostgreSQL DELETE

1. DELETE deletes one or more rows from a table
2. RETURNING will show the deleted rows
3. Delete only changes the data, ALTER TABLE is used to change the structure of the table
4. Multiple rows can be deleted at a time if selected

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
