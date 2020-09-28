## Due 9/28
- Why you should use bcrypt (https://medium.com/@danboterhoven/why-you-should-use-bcrypt-to-hash-passwords-af330100b861)
1. Plain text passwords use only letters and often times users use the same password on multiple sites. If someone were to see the list they would see these passwords.
2. One way hash passwords use a hashing algorithm to authenticate users. This is a far better password, but hackers can continue guessing.
3. Salting the password is the next best things. It involves adding bits to the end of the password to make it harder to guess. If a hacker gets into your source code, they could get the salt data.
4. Salting each user randomly is better, each user can get a new salt string when they create an account, it still has similar problems as above, but does take longer to break into multiple accounts.
5. BCrypt is a cryptomatic algorithm that is like an adaptive hash function. Using a Key Factor, BCrypt can adjust the cost of hashing to remain resilient to hacks and scales up with ever faster and faster computers.

- Understanding bcrypt (https://auth0.com/blog/hashing-in-action-understanding-bcrypt/)
1. The bcrypt hashing function scales with computation power and hashes every password with a salt.
2. Modern computers can compute millions to billions of hashes per second, instead of a fast function, we need a slow function. One that gets slower over time.
3. The blowfish cypher that bcrypt is built on is a fast block cipher except when changing keys. In those cases it is slower than most hashing methods. This slows down brute force attacks
4. This can be combined with a variable number of iterations to increase workload and duration of hash calculations. Over time this iteration count can be increased to make it even slower to diminish benefits of fast hardware.
5. Phase 1: A function is set up using the desired cost, the salt, and the password.
6. Phase 2: The magic value is the 192-bit value, which is encrypted 64 times in ECB mode with the sate from the previous phase. The output of this phase is the cost and the 128-bit salt value concatenated with the result of the encryption loop.
7. If the accepted wait time for your app for registration and authentication is 1 second, tune bcrypt to run for 1 second on your hardware, then check with security team to see if that is enough to mitigate and slow down attacks.
8. A typical computer would take 513 days to calculate a cost factor of 30 and it increases exponentially. 
9.  Another layer of security is two factor, or multi factor authentication.
10. npm i bcrypt

- Where to store JWT (https://auth0.com/docs/tokens/token-storage)
1. Securing SPAs that make API calls come with their own set of concerns. You'll need to ensure that tokens and other sensitive data are not vulnerable to cross-site scripting (XSS) and can't be read by malicious JavaScript
2. Auth might be needed when you access a page, api route, when your app calls and an api hosted outside your app on behalf of the user
3. When not using API calls, an id token can be sufficient. If making API calls on behalf of the user, access tokens and refresh tokens are needed and can be stored server side, or on cookies.
4. KeyStore or KeyChain can make good places to store a token
5. AuthO recommends storing tokens in browser memory as teh most secure option. Javascript closures can emulate private methods.

## Due 9/23
- User Modeling
1. Web developers have a duty to safely handle information
2. Cryptography is the science of encoding messages
3. A Cryptographic Hash Algorithm takes a piece of data and produces a hash that is deliberately difficult to reverse, if identical data is passed to it the same hash will always be returned.
4. It takes a piece of data and a key to produce encrypted data. Later the data can be reversed into the original data by decrypting it using the same key.
5. User tokens can be created by associating a random unique string (tokenSeed) with a user account and encrypting the tokenSeed with a secret key that only the server knows, then the encrypted token gets sent to a client application. The app then uses the token to make requests.
6. Basic authorization is a common method used to send passwords and usernames on HTTP requests
7. The username and password is joined and then base64 encoded using atob and btoa.
8. let encoded = window.btoa('someUserName:Password')
9. let decoded = window.atob('jksfjksdfjsldfjksd-passwordhash-skdfjksdlf')

- Securing Passwords (unable to locate ip address)

- Basic Access Authentication
1. Basic Authentication doesn't provide any confidentiality protection, they are only encoded in base64 in transit. It must be used with HTTPS to provide confidentiality. 

- JSON Web Token
1. JWT is an open standard (RFC 7519) that defines a compact and self-contained way for securely transmitting information between parties as a JSON object. It can be verified and trusted because it is digitally signed using a secret (HMAC algorithm) or public/private key pair using RSA or ECDSA.
2. These should be used for authorization or information exchange
3. They consist of three parts header.payload.signature

- Authentication Cheat Sheet (https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
1. User ID's should be case-insensitive so Mike and mike are the same. They should also be unique and secret if it is high sensitivity
2. Implement proper password strength controls
3. Have a secure password recovery mechanism
4. Store passwords in a secure fashion
5. Use safe functions to compare hashes
6. Transport passwords only over TLS or other strong transports
7. Re-Authenticate for sensitive features

- bcrypt docs
1. npm install bcrypt
2. hashes a password
3. async mode is recommended

## Due 9/22

- Using Express Routing (https://expressjs.com/en/guide/routing.html)
1. Routing refers to how an applications endpoints (URI's) respond to client requests
2. You can define routs using methods of the Express app object that corresponds to HTTP methods (get, post, delete, etc)
3. These methods specify a callback/handler function
4. Routing methods can have more than one callback function and are called with next()
5. app.all() is used to load middleware functions for all HTTP methods
6. Route paths can be strings, string patterns, or regular expressions
7. Route parameters are named URL segments that target a specific route

- Supertest (https://github.com/visionmedia/supertest)
1. npm i supertest --save-dev
2. called with require('supertest')

- Using Express Middleware (https://expressjs.com/en/guide/using-middleware.html)
1. Middleware functions have access to the request object (req), response object (res), and the next middleware function in the application's request-response cycle
2. They can execute any code, make changes to the req/res objects, end the req/res cycle, or call the next middleware function in the stack
3. If the middleware function doesnt call next or end the req/res cycle the request will be left hanging
4. An Express application can use these types of middleware: Application-level, Router-level, Error-handling, Built-in, or Third-party

- Express Middleware (https://www.tutorialspoint.com/expressjs/expressjs_middleware.htm)
1. Middleware is called in order
2. body-parser can be used to parse the body of requests that have payloads
3. cookie-parser parses cookie header and populates req.cookies with an object keyed by cookie names
4. express-session creates a session middleware with given options

- Express Middleware List (https://expressjs.com/en/resources/middleware.html)
1. Express middleware modules list that are maintained by the Expressjs team

## Due 9/21

- http Basics (https://code.tutsplus.com/tutorials/http-the-protocol-every-web-developer-must-know-part-1--net-31177)
1. Hyper Text Transfer Protocol
2. HTTP is a stateless protocol
3. HTTP Verbs include the most popular: GET, POST, PUT, DELETE
4. There are different error codes for various types of common errors.
5. A request is sent with header information, request and response messages can also have a body
6. Chrome with Webkit inspector is a favorite too to monitor HTTP communication

- How DNS works (https://howdns.works/ep1/)
1. Turns words into ip addresses
2. When a pages is searched for, the browser and os check their cache to see if they know
3. If not, it goes to a resolver online, it checks its cache, if not it checks the Top Level Domain Server
4. If the TLD Server doesn't know, it checks one of 13 root name servers that exist today, labled a - m.root-servers.net
5. The .com root server is one of the largest and created in 1985
6. Other types have country codes, generic like .net .org .edu
7. Today many new generic ones are being created
8. If the root server doesn't know, it will give the authoritative name server for that site name
9. When a domain is created the registrar creates the name and communicates to the TLD
10. The authoritative name servers can be searched with a WHOIS query

- http and rest
1. API: Application Program Interface
2. Structured request and response (the Messenger)
3. REST: Representational State Transfer
4. Architecture style for designing networked applications
5. Almost always relies on HTTP
6. Treats server objects as resources that can be created or destroyed
7. Can be almost any language (format to send message)
8. Endpoints are the URI/URL where api can be accessed by a client or app

- http reference (https://code-maze.com/the-http-reference/)
1. CONNECT: to use with a proxy that can dynamically switch to being a tunnel
2. DELETE: requests a resource to be deleted
3. GET: retrieves information
4. HEAD: just like HEAD except the server MUST NOT return a message body in response
5. OPTIONS: requesting communications options available
6. POST: requests that the server accept the information as new information (creates)
7. PUT: requests the information be stored (updates)
8. TRACE: invokes a remote, application layer loop back of the request message

- rest reference (https://www.restapitutorial.com/lessons/httpmethods.html)
1. Post is used to create new resources

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
