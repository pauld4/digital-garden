## Core JavaScript Basics

**Variables & Scope**
Note that I only capitalize the key words such as VAR, LET, etc to help make these words stick out to the reader. When I write these in code, they are all lowercase.

### **What’s the difference between VAR, LET, and CONST?**

VAR
-Function scoped, not block scoped
-Initialized as 'undefined'
-Can be redeclared and reassigned
-Common to cause bugs due to unexpected scope behavior
LET
-Block scoped
-Not initialized
-Can be reassigned, but not redeclared in the same scope
-Safer than Var
CONST
-Block scoped
-Must be assinged a value when initialized
-Cannot be redeclared or reassigned, but can still be mutated if used for an object or array
-Preferably used for variables that shouldn't change value

### **What is block scope vs function scope?**

A variable has block scope if it is accessible within the brackets {} it was declared in. Similar with function scope, a variable is only accessible within the function it is declared. For example, a LET or CONST variable in an IF statement is only accessible within that IF statement. Whereas a VAR variable is accessible inside that IF statement and in the function that it is in.

### **When should you use const?**

CONST is helpful to let other developers know that the value of the CONST variable should not be changed. Such as a variable, 'const my_name = "Paul"'. A variable such as 'let counter = 0' should use LET because the counter would be changing often. LET is also used in FOR LOOPS, such as 'for(let i = 0; i < num_max; i++)' or 'for(let u of users)' where 'users' is an array of users. VAR should almost never be used, but is commonly used in older JavaScript code.

### **What is hoisting behavior?**

Hoisting behavior is the way that JavaScript moves variable and function declarations to the top of their scope during compilation. Hoisting VAR variables incorrectly still leads to the code running, which can lead to unforseen bugs. The system won't throw an immediate error since VAR variables are automatically initialized to 'undefined'. It is best practice to declare variables at the top of their scope, and the reassign them below that.

## Data Types

### **What are the primitive data types in JavaScript?**

JavaScript has seven primitive data types. Primitives are immutable values that are stored directly in memory. The seven types are string("Paul"), numbers such as integers(42) and floating point(30.99), bigint(9007199254740991n), boolean(true/false), undefined, null, and symbol(Symbol("Id")).

### **Difference between mutable and immutable values**

Mutable values can be modified in memory after they are created, while immutable values cannot be changed once created. Objects and arrays are examples of mutable values, and immutable values are the primitive types mentioned above. When reassigning an immutable value, JavaScript just creates a new value, and the old value becomes unreferenced and will eventually be eligible for garbage collection. An example is 'let num = 25' and then later 'num = 50'. The value 25 is still in memory, but num just points to a new value, 50. The value 25 is no longer referenced and will be eligible for garbage collection.

### **When does garbage collection occur in JavaScript?**

Garbage collection occurs automatically when a value is no longer reachable by any reference in the program. The JavaScript engine decides when to reclaim that memory.

### **What’s the difference between null and undefined?**

Both null and undefined represent the absence of a value, but they are used differently. Undefined is the default value a variable is assigned if no other value has been assigned to it. Null is a value that the developer assigns to a variable. Writing 'typeof null' returns an object value. 'Null == undefined' returns true, but 'Null === undefined' returns false. 

### **What does 'typeof' return for arrays or null?**

Writing 'typeof [1,2,3]' and 'typeof null' returns 'object'. 'typeof' should not be used for arrays, and instead use 'Array.isArray([1,2,3])' which will return 'true'. Since 'null == undefined' returns true, we have to use 'variable === null' to check if something is null, whereas 'variable == null' will check if it is undefined. Same with 'typeof variable === undefined' to check if it is 'undefined'. Writing 'variable == null' will check if it is either null or undefined.

## Equality

### **What’s the difference between == and ===?**

'==' is loose equality, and '===' is strict equality. '===' will check for same type AND value. '5 === "5"' will return 'false', while '5 == "5"' will return 'true', just like 'null == undefined' will return 'true' and 'null === undefined' will return 'false'. Loose equality allows for type coercion, so JavaScript will try to convert values before comparing them. Examples are '0 == false' is 'true', but '0 === false' will be 'false'. 

### **Why is '0 == false' true but '0 === false' false?**

0 is a number type, and false is a boolean type. Using '===' will return false because the types do not match. When using '==', type coercion occurs and 'false' is converted to a number, 0, so '0 == false' returns 'true'.

### **Type Coercion**

Doing '5 == "5"' will return 'true' because JavaScript converts strings to numbers in comparison. JavaScript uses 'Number("5")' to convert the string 5 to an integer for comparison. Doing 'Number("a")' will result in 'NaN'. 'Nan == Nan' and 'NaN === NaN' will return 'false'. 'typeof NaN' will return 'number'.

## Functions

### **What’s the difference between a function declaration and a function expression?**

A function declaration creates a function using the FUNCTION keyword. Such as 'function printTitle() {}'. Functions that are declared are hoisted and can be called before it is written in the code. Function expressions are functions that are assigned to variables, such as 'let printTitle = function () {}'. These are not hoisted, and therefore cannot be called before it is written.

### **What are arrow functions, and how are they different?**

Arrow functions are function expressions with lexical 'this', no arguments object, and shorter syntax. They cannot be used as constructors.

### **When would you not want to use an arrow function?**

Arrow functions do not have their own THIS keyword, so THIS is inherited from the surrounding scope. Do not use them for object methods. Arrow functions cannot be used with NEW. Arrow functions do not have a prototype, so they cannot be constructors. Arrow functions also do not have an ARGUMENTS object. An arrow function should not be used when using methods that rely on dynamic THIS. THIS is fixed, and arrow functions will ignore functions that use CALL, APPLY, or BIND.

### **The difference between 'function()' and 'function'?**

Writing 'function()' calls the function, and returns the value, if there is a value to be returned. Writing 'function' is the function itself, so 'let x = function' would allow 'x' to reference 'function' so you can write 'x()' to call 'function'. Writing 'let x = myFunction()' would mean that the value returned by 'myFunction' is assigned to 'x', whereas writing 'let x = myFunction' assigns 'myFunction' to 'x' and 'x' can be used to call 'myFunction'.

### **Difference between 'invoking a function' and 'calling a function'?**

Invoking and calling mean the same thing. To call 'myFunction()' means the same as invoking 'myFunction()'.

### **Difference between 'declaring', 'calling', 'referencing'?**

Defining/declaring is when a new function is created, such as 'function myFunction() {}'. Calling is when the function is called and used, such as 'myFunction()'. Referencing is when a variable is used to reference a value or function, such as 'let x = myFunction' or 'let x = 5'. Declaration creates the variable/function, initializing it means giving it a value at declaration, and assigning it means changing the value.

## Closures

### **What is a closure?**

A closure is created when a function retains access to variables from its lexical scope even after the outer function has finished executing.

### **Can you give a real-world example of one?**

### **Why use closures over classes?**

Closures provide true data encapsulation by keeping variables private within a function scope. While classes can also achieve privacy using private fields, closures offer a functional approach without relying on class syntax.

### **Why are closures useful?**

Closures are useful because they allow functions to retain access to variables from their lexical scope, enabling private state, persistent data, and powerful patterns like callbacks, factories, and debouncing. Variables are private and only the returned function can modify the variables inside the function. 

## Arrays

### **What’s the difference between map, forEach, filter, and reduce?**

Map transforms each element into a new value, and returns a new array. Map does not modify the original array. Example is 'const doubled = [1,2,3].map(num => num*2)'. forEach executes a function for each element, and does not return a new array. Example is '[1,2,3].forEach(num => { console.log(num); })'. Filter selects elements from an array based on a condition, and returns a new array. Example is 'const evenNum = [1,2,3,4].filter(num => num % 2 === 0)'. 'evenNum' is now an array that has elements that are even numbers. Filter can be used on the same array so that the new array is assigned to the original array. Reduce reduces an array to a single value, so take a list of numbers and add them together. Such as 'const sum = [1,2,3].reduce((acc,num) => acc + num, 0)'. 'acc' is the accumulator value, and 'num' is the current value. The '0' at the end is the initial value for hte accumulator. So the order would be '0 + 1', '1 + 2', then '3 + 3' which equals '6'. If no intial value is provided then the first array element is the accumulator's initial value.

In short, use map to transform, filter to remove items, reduce to combine items, and forEach to iterate.

### **How do you remove duplicates from an array?**

The best way to remove duplicates from an array is to use Set(). This can be done using 'let newArray = [...new Set([1,2,2,3])]', and 'newArray' will be '[1,2,3]'. Set() converts the array into a Set object, and then that object is converted into an array using the spread syntax, '...'.

### **What is the JavaScript Set() object?**

The Set() is used with an array to return an object of unique values. So writing 'Set([1,2,2,3])' will return a Set object {1,2,3}. Set objects cannot be individually accessed like an array does with indexes, but Sets can still be ready using has(), or iterated over using FOR...OF or forEach. If index access is needed, convert it to an array.

### **How do you check if a variable is an array?**

Use 'Array.isArray(myArray)'. This will return a TRUE or FALSE value. You can convert a SET to an ARRAY using 'mySet = [...mySet]', and then 'console.log(Array.isArray(mySet))' which will return TRUE. You cannot use 'typeof myArray' because that will return 'object'. In JavaScript, ARRAYS are a special type of object, which is why 'Array.isArray()' is used.

## Objects

### **How do you loop over an object’s properties?**

Objects are not arrays, so map() or forEach() cannot be used. Instead, use FOR...IN. Such as 'for(let key in obj) { console.log(key, obj[key]); }'. Another method is to use Object.keys(). If you have 'let obj = { a:1, b:2, c:3 }', then you can iterate over that object using 'Object.keys(obj).forEach(key => { console.log(key, obj[key]); })'. You can also use FOR...OF, such as 'for(let [key,value] of Object.entries(obj)) { console.log(key, value); }'. Another way to use Object.entries is to use 'Object.entries(obj).forEach(([key, value]) => { console.log(key, value); })'.

### **What’s the difference between dot notation and bracket notation?**

Dot notation is using dots to access an object properties, and bracket notation uses brackets to access object properties. Dot notation looks like this 'console.log(obj.name)' and bracket notation would be 'console.log(obj["name"])'. Bracket notation can use variables to access the property, such as 'let key = "name"; console.log(obj[key]);'. Dot notation is used for accessing known, valid property names, while bracket notation allows dynamic property access and supports property names with special characters or spaces. By default, dot notation should be used, and bracket notation should be used when the property name is dynamic such as containing spaces or special characters.

### **What is object destructuring?**

Object destructuring is a syntax that allows you to extract properties from an object and assign them to variables. Instead of 'let user = { name: "Paul", count: 10 }; let name = user.name; let count = user.count;' you can do 'let { name, count } = user'. The variable names must match the property names. Defaults can be used too, so if the object does not have a property, then that property can be added, such as 'let { country = "USA" } = user'.

## Asynchronous JavaScript

### **What is asynchronous programming?**

JavaScript is single threaded, and can only perform one task at a time. Some tasks take time to complete, and JavaScript has to wait for these tasks to complete before it moves to the next. Asynchronous programming in JavaScript is a way to run time-consuming tasks without blocking the rest of your code. 3 main ways to do asynchronous programming in JavaScript is by using Callbacks, Promises, and Async/Await. Async/Await is the most popular today.

### **What is a callback function?**

A callback function is a function that is passed as an argument into another function. For example, 'setTimeout(function() { console.log("Text"); }, 1000)'. The callback part is the 'function() { console.log("Text"); }' function.

### **What is the event loop?**

The event loop is the mechanism in JavaScript that monitors the call stack and the callback queue, and pushes queued callbacks onto the stack when it becomes empty.

### **What is the call stack?**

The call stack is the place where JavaScript keeps track of which functions are currently running. The stack keeps track of the order that functions should be executed and follows a First In Last Out (or Last In First Out) order. Example is the order of these function calls 'console.log("A"); setTimeout(() => { console.log("B"); }, 0); console.log("C"); console.log("D");', which would print ACDB since B is placed in the callback queue and JavaScript finishes executing all synchronous code currently on the call stack before running queued callbacks.

## Promises & Async/Await

### **What is a Promise?**

A promise is an object that represents a value that will be available in the future. It represents the eventual completion, or failure, of an asynchronous operation and its resulting value. Instead of using multiple callbacks within each other, promises can be used.

### **What are the states of a Promise?**

Three states of a promise are pending, fulfilled, and rejected.

### **What’s the difference between .then() and async/await?**

.then() is a method used to handle a Promise, and async/await is a cleaner way of working with Promises.

### **How do you handle errors in async code?**

Errors in async/await requests are handled using try...catch statements.

### **If you fetch data from an API, how do you handle success and failure?**

There are two types of failure to be handled, network failure and HTTP error (404, 500, etc). However, fetch only fails if there is a network error, not an HTTP error. Check for an HTTP error using 'response.ok' with a 'const response = await fetch("myapi/data")', and if no errors occur then run code as usual.

## DOM & Browser JavaScript

### **How do you select DOM elements?**

DOM elements can be selected in multiple ways. Selecting elements by ID, Class, Tag, querySelector, and querySelectorAll. Select elements by ID using 'let element = document.getElementById("myId")' which will return one element with that unique ID. Writing 'let elements = document.getElementsByClassName("myClass")' will select all elements with that class and return an array. To select all 'div' elements, or all 'a' elements, use 'let elements = document.getElementsByTagName("div")', which returns an array as well. querySelector is used to select the first single element with an ID, class, or tag, with 'let element = document.querySelector(".myClass")'. '.myClass' can be substituted for '#myID' or 'div' (or another tag). querySelectorAll does the same thing, but returns an array of every element that matches. Elements returned in an array can be accessed using 'element[1].innerHTML', just as you would with any array.

### **What’s the difference between querySelector and getElementById?**

querySelector requires ID search using '#myID' instead of 'myID' like with getElementById. getElementById is only used for IDs, whereas querySelector can be used for IDs, classes, and tags. getElementById is slightly faster since browsers keep a list of IDs. querySelector and querySelectorAll are mostly used, unless you need an element with a specific ID.

### **What is event bubbling and event capturing?**

Event bubbling is when an element is interacted with and the event in the DOM starts at the element, then 'bubbles' up to the parent element. Such as when clicking a button, the process moves from 'button > body > html > document'. Event capturing is the opposite, where the event starts at the top of the DOM tree and moves to the element, such as 'document > html > body > button'. This is useful for event delegation, so instead of individually assigning a large number of buttons or elements with a click event, event bubbling can be used.

### **What’s the difference between event.target and event.currentTarget?**

event.target is referencing the element that was actually clicked, and event.currentTarget is the element that the event listener is connected to. Clicking a button within a parent element means the target is the button and the parent is the currentTarget. Clicking on the parent means that the parent is both the target and currentTarget.

### **How do you prevent default browser behavior?**

Default behavior means browser performing actions such as navigating to a page after clicking a link, reloading the page after submitting a form, opening the context menu using right click, and scrolling on the page by pressing spacebar. 'e.preventDefault()' prevents that behavior. This is useful in examples such as instead of reloading the page when submitting a form, the data can instead be checked and sent using 'fetch()', and keep the user on the same page. Preventing default behavior is best for overriding the browser's default behavior and instead controlling the behavior yourself using JavaScript.

## Advanced

### **What’s the difference between shallow and deep copying?**

## Practical / Scenario

### **How would you debug a JavaScript bug in production?**

### **How do you optimize performance in a JS app?**

### **Have you worked with APIs? How did you handle loading states?**

### **How do you structure JavaScript code in a larger project?**

## Coding-Style Questions

### **Reverse a string**

You would use a combination of SPLIT, REVERSE, then JOIN, such as "const reversed = str.split('').reverse().join('')". You can also use "const reversed = [...str].reverse().join('')".

### **Count occurrences in an array**

If you need to count one item, you can simply use "const appleCount = fruits.filter(x => x === 'apple').length". This is a simpler approach compared to using REDUCE. However, using REDUCE is standard and preferred.

### **Toggle a boolean value**

Use "val = !val".

### **Find the largest number in an array**

Use "Math.max(...numbers)" in "let numbers = [1,2,3,4]".

### **Debounce or throttle an event**

Debounce is used for events that execute many times, and then pauses for a moment. Throttle is used for events that occur infrequently, and limit the event occuring too often.
