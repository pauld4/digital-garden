# js-questions

//===Core JavaScript Basics===//

===Variables & Scope===
Note that I only capitalize the key words such as VAR, LET, etc to help make these words stick out to the reader. When I write these in code, they are all lowercase.

What’s the difference between VAR, LET, and CONST?

VAR
-Function scoped, not block scoped
-Initialized as 'undefined'
-Can be redeclared and reassigned
-Common to cause bugs due to unexpected scope behavior
LET
-Block scoped
-Not initialized
-Can be reassigned, but not redclared in the same scope
-Safer than Var
CONST
-Block scoped
-Must be assinged a value when initialized
-Cannot be redeclared or reassigned, but can still be mutated if used for an object or array
-Preferably used for variables that shouldn't change value

What is block scope vs function scope?

A variable has block scope if it is accessible within the brackets {} it was declared in. Similar with function scope, a variable is only accessible within the function it is declared. For example, a LET or CONST variable in an IF statement is only accessible within that IF statement. Whereas a VAR variable is accessible inside that IF statement and in the function that it is in.

When should you use const?

CONST is helpful to let other developers know that the value of the CONST variable should not be changed. Such as a variable, 'const my_name = "Paul"'. A variable such as 'let counter = 0' should use LET because the counter would be changing often. LET is also used in FOR LOOPS, such as 'for(let i = 0; i < num_max; i++)' or 'for(let u of users)' where 'users' is an array of users. VAR should almost never be used, but is commonly used in older JavaScript code.

What is hoisting behavior?

Hoisting behavior is the way that JavaScript moves variable and function declarations to the top of their scope during compilation. Hoisting VAR variables incorrectly still leads to the code running, which can lead to unforseen bugs. The system won't throw an immediate error since VAR variables are automatically initialized to 'undefined'. It is best practice to declare variables at the top of their scope, and the reassign them below that.

===Data Types===

What are the primitive data types in JavaScript?

JavaScript has seven primitive data types. Primitives are immutable values that are stored directly in memory. The seven types are string("Paul"), numbers such as integers(42) and floating point(30.99), bigint(9007199254740991n), boolean(true/false), undefined, null, and symbol(Symbol("Id")).

Difference between mutable and immutable values

Mutable values can be modified in memory after they are created, while immutable values cannot be changed once created. Objects and arrays are examples of mutable values, and immutable values are the primitive types mentioned above. When reassigning an immutable value, JavaScript just creates a new value, and the old value becomes unreferenced and will eventually be eligible for garbage collection. An example is 'let num = 25' and then later 'num = 50'. The value 25 is still in memory, but num just points to a new value, 50. The value 25 is no longer referenced and will be eligible for garbage collection.

When does garbage collection occur in JavaScript?

Garbage collection occurs automatically when a value is no longer reachable by any reference in the program. The JavaScript engine decides when to reclaim that memory.

What’s the difference between null and undefined?

Both null and undefined represent the absence of a value, but they are used differently. Undefined is the default value a variable is assigned if no other value has been assigned to it. Null is a value that the developer assigns to a variable. Writing 'typeof null' returns an object value. 'Null == undefined' returns true, but 'Null === undefined' returns false. 

What does 'typeof' return for arrays or null?

Writing 'typeof [1,2,3]' and 'typeof null' returns 'object'. 'typeof' should not be used for arrays, and instead use 'Array.isArray([1,2,3])' which will return 'true'. Since 'null == undefined' returns true, we have to use 'variable === null' to check if something is null, whereas 'variable == null' will check if it is undefined. Same with 'typeof variable === undefined' to check if it is 'undefined'. Writing 'variable == null' will check if it is either null or undefined.

===Equality===

What’s the difference between == and ===?

'==' is loose equality, and '===' is strict equality. '===' will check for same type AND value. '5 === "5"' will return 'false', while '5 == "5"' will return 'true', just like 'null == undefined' will return 'true' and 'null === undefined' will return 'false'. Loose equality allows for type coercion, so JavaScript will try to convert values before comparing them. Examples are '0 == false' is 'true', but '0 === false' will be 'false'. 

Why is '0 == false' true but '0 === false' false?

0 is a number type, and false is a boolean type. Using '===' will return false because the types do not match. When using '==', type coercion occurs and 'false' is converted to a number, 0, so '0 == false' returns 'true'.

Type Coercion

Doing '5 == "5"' will return 'true' because JavaScript converts strings to numbers in comparison. JavaScript uses 'Number("5")' to convert the string 5 to an integer for comparison. Doing 'Number("a")' will result in 'NaN'. 'Nan == Nan' and 'NaN === NaN' will return 'false'. 'typeof NaN' will return 'number'.

//===Functions & Execution==///

===Functions===

What’s the difference between a function declaration and a function expression?

A function declaration creates a function using the FUNCTION keyword. Such as 'function printTitle() {}'. Functions that are declared are hoisted and can be called before it is written in the code. Function expressions are functions that are assigned to variables, such as 'let printTitle = function () {}'. These are not hoisted, and therefore cannot be called before it is written.

What are arrow functions, and how are they different?

Arrow functions are function expressions with lexical 'this', no arguments object, and shorter syntax. They cannot be used as constructors.

When would you not want to use an arrow function?

The difference between 'function()' and 'function'?

Writing 'function()' calls the function, and returns the value, if there is a value to be returned. Writing 'function' is the function itself, so 'let x = function' would allow 'x' to reference 'function' so you can write 'x()' to call 'function'. Writing 'let x = myFunction()' would mean that the value returned by 'myFunction' is assigned to 'x', whereas writing 'let x = myFunction' assigns 'myFunction' to 'x' and 'x' can be used to call 'myFunction'.

Difference between 'invoking a function' and 'calling a function'?

Invoking and calling mean the same thing. To call 'myFunction()' means the same as invoking 'myFunction()'.

Difference between 'declaring', 'calling', 'referencing'?

Defining/declaring is when a new function is created, such as 'function myFunction() {}'. Calling is when the function is called and used, such as 'myFunction()'. Referencing is when a variable is used to reference a value or function, such as 'let x = myFunction' or 'let x = 5'. Declaration creates the variable/function, initializing it means giving it a value at declaration, and assigning it means changing the value.

===Closures===

What is a closure?

A closure is created when a function retains access to variables from its lexical scope even after the outer function has finished executing.

Can you give a real-world example of one?

Why are closures useful?

//===Arrays & Objects===//

===Arrays===

What’s the difference between map, forEach, filter, and reduce?

How do you remove duplicates from an array?

How do you check if a variable is an array?

===Objects===

How do you loop over an object’s properties?

What’s the difference between dot notation and bracket notation?

What is object destructuring?

//===Asynchronous JavaScript===//

===Async Concepts===

What is asynchronous programming?

What is the event loop?

What is the call stack?

===Promises & Async/Await===

What is a Promise?

What are the states of a Promise?

What’s the difference between .then() and async/await?

How do you handle errors in async code?

If you fetch data from an API, how do you handle success and failure?

//===DOM & Browser JavaScript===//

How do you select DOM elements?

What’s the difference between querySelector and getElementById?

What is event bubbling and event capturing?

What’s the difference between event.target and event.currentTarget?

How do you prevent default browser behavior?

//===Advanced===//

What is hoisting?

What is the this keyword, and how does it change?

What is prototypal inheritance?

What’s the difference between shallow and deep copying?

How does JavaScript manage memory? (garbage collection)

//===Practical / Scenario===//

How would you debug a JavaScript bug in production?

How do you optimize performance in a JS app?

Have you worked with APIs? How did you handle loading states?

How do you structure JavaScript code in a larger project?

//===Coding-Style Questions===//

Reverse a string

Count occurrences in an array

Toggle a boolean value

Find the largest number in an array

Debounce or throttle an event
