# JAVASCRIPT - THE BASICS

## What is Javascript ? Where does Javascript run ?

**Javascript** is dynamic weekly typed programming language.It was called as **LiveScript** and renamed to Javascript due to popularity of **Java**.**Javascript** runs on the **browser**. It is very powerful for web development. It can also run on server using **node js** 

**How webpage works**

![alt image](https://raw.githubusercontent.com/msgtobala/My-Books/master/images/how-browser-works.png)

### How JS is executed ?

```flow
st=>start: Code
e=>end: Effect on Webpage
op1=>operation: Javascript Engine(Chrome - V8, Firefox - Spider Monkey, Chakra - IE, Nitro and SquirrelFish - Safari)

st->op1->e
```

**How Javascript Engine is Exceuted?**

```flow
st=>start: Code
e=>end: Effect on Webpage
op1=>operation: Parsed(read, undertsood by browser)
op2=>operation: Compiled to Machine code
op3=>operation: Execute Machine code

st->op1->op2->op3->e
```

Javascript Engine uses **machine code** because this faster. Also **Javascript** is **single-threaded**

### How JS Runs

![HOW JS RUN](https://github.com/msgtobala/My-Books/blob/master/images/JS%20and%20Node%20JS.png?raw=true)

## Versions of Javascript / What is ECMAScript

**ECMAScript** is a superset of Javascript which has all the standardization to be implemented. **Javascript** is a dialect of ES.

* Versions - ES5, ES6....

> Note: **ES5** is supported by all the browsers, **ES6** is not supported yet and we need **polyfills** to be supported.
>
> Polyfills - Used to support browsers for ES6 features as ES6 features are not supported in the browsers.
>
> We can use pre-processors also like **Babel**

### History of JS 

![History of JS](https://github.com/msgtobala/My-Books/blob/master/images/History%20of%20JS.png?raw=true)

### ECMASCRIPT AND JAVASCRIPT

**ECMASCRIPT** is a standardization for JS. It has, 

* Javascript
* ActionScript
* Jscript

**ECMA** - European Computer Manufacturers Assosiation.

> Each browser comes with its own engine. ECMAscript is not used directly.But the browsers use its implementation using JS. Also browsers are able to add their own features. Browsers are also supporting the development of ECMAscript.

* Javascript is the only language for web technolgy. But there are some alternatives where they offer more syntax but in the end **transpiled** to JS

  #### Examples of such languages

  * Coffescript - Used by **ruby** devs
  * Typescript - Developed by **Microsoft**
  * Flow - **Facebook**
  * Dart - **Google**

  Each browser has different implementation of JS. To see the compactability of JS Features, use,

  * [Can I Use](https://caniuse.com)
  * [Kanjax](https://kangax.github.io/compat-table)

## Language Basics

### 1) Script Tag

All the Javascript inside the script will be executed. Browser will start parsing the DOM from the top. So, if you include in the `<head>` , it will execute at the time of parsing only. But the DOM is not loaded yet. Therefore DOM objects cannot be accessed. So keep `<script>` imports at the bottom at the closing of `<body>` tag.

Also, if you have long running javascript that is placed on the `<head>` that can block page rendering eventhough the page is small. Hence, the place always matters.

#### Sample

```html
<script type='text/javascript'>console.log('hai')</script> // type is optional attr. This is **inline js**
```

**Types of adding JS**

* Internal
* External

### Enabling Javascript

```html
<noscript>Please Enable Javascrip</noscript>
```

This will display the message in the browser, if the js is **disabled**.

### Including Javascript - External

```html
<script type='text/javascript' src='./<file>.js'></script> // This is External js
```

This is **Recommended**. This is for cleaner code and re-usability.

As a rule, only the simplest scripts are put into HTML. More complex ones reside in separate files.

The benefit of a separate file is that the browser will download it and store it in its [cache](https://en.wikipedia.org/wiki/Web_cache).

Other pages that reference the same script will take it from the cache instead of downloading it, so the file is actually downloaded only once.

That reduces traffic and makes pages faster.

> Note: `script` Tag is not a self-closing tag

```html
<script type='text/javascript' src='./<file>.js'>console.log('hai');</script> // o/p: hello
```

```js
// file.js
console.log('hello');
```

This is because is we use **External imports**, then inline js is not executed.i.e., the code in between `<script>` tag.

```html
<script type='text/javascript' src='./<file>.js'></script>
<script type='text/javascript' src='./<file2>.js'></script>
```

This is Possible, and it will be executed as we include in the code**(in-order)**

> Note: Usually, third-party library `script` tags should be included first

 ```html
<script type='text/javascript' src='./<file>.js' defer></script>
<script type='text/javascript' src='./<file2>.js'></script>
 ```

**defer** is used for changing the execution order of Javascripts. JS without defer will be executed first and then `defer scripts` will be executed. 

> Note: **script** tag is not self-closing tag

### 2) Variables

 **Variables** are storages for data.Variables are data containers.

**Naming Convention**

* Should be camelCase
* Should point purpose
* JS Variables are case sensitive
* Should not start with special characters (except _ , $), Number
* Should not use `user_name`(Snake case) instaed use userName
* Should not have special characters any-where in the variable name ex: `user-name`
* Should not use reserved words
* Should use semi-colons after each statements

> Note all uninitalized variables have **undefined** stored inside

```js
var numVariable = 1;
var stringVarible = 'test';
var boolVariable = true;
var arrayVariable = [1, 2, 3];
var objVariable = {
  name: 'test'
};
var floatVariable = 6.6;
```

>Variables should not have reserved key word and should not start with number or special characters

**typeof** will give the data-type of variables

```js
var a = 1;
typeof a; // number  
var a = 1.7;
typeof a ; // number
typeof ''; // string
typeof true; // boolean
```

<table> <caption>Data Types</caption> <tr> <th colspan="2">Data types</th><tr> <th>Primitive</th><th>Reference</th><tr><td>Number</td><td>Array</td></tr><tr><td>Boolean</td><td>Objects</td></tr>
<tr><td>String</td><td></td></tr><tr><td>undefined</td><td></td></tr><tr><td>null</td><td></td></tr><tr><td>Function</td><td></td></tr></table>

**Arrays** is collection of mixed data-types

#### Example

```js
var a = [1, 2, 3];
console.log(a, a[2]); // [1, 2, 3], 3
console.log(a[3]); // undefined
```

>Prefer **null** than **undefined** always (when initializing variables it holds **undefined** and it will break sometime)
>
>null and undefined has the same values

```js
console.log(null === undefined); // false
console.log(null == undefined); // true
```

**NaN** is a number. But it will occur when mathematical opeations can be calculated 

#### Example

```js
console.log(12 * 'test'); // NaN
```

> **typeof** NaN - **number**

```js
typeof null; // object
typeof undefined; // undefined
typeof NaN; // number
```

**Objects** is a key value pair data structure.

#### Example

```js
var a = {
  name: 'test',
  greet: function () {
    console.log('hai');
  }
};
var b = 'test';
console.log(a.name); // test
console.log(a['name']); // test;
console.log(a[b]); // test
```

> In Objects we can initialise the properties and methods

```js
var a = {
  name: 'test',
  greet: function () {
    console.log('hai');
  }
}; 
typeof a; // oject
```

* Dont initiate variables with undefined `var a = undefined`

 **Strict mode**

* Ensures the **semi-colons** at the line end
* Ensures all the varibales are declared with **var / let / const**

This is for increasing performance and cleaner code.

```js
"use strict"
a = 1;  // gives error (no keyword) as we are in strict mode
console.log(a) // gives error (no semi-colon)
```

 **Types of Error**

* Reference Error
* Syntax Error
* Type Error - calling and passing args to number variable

```js
var a;
console.log(a); // undefined
```

**Static Typing and Dynamic Typing**

* If the error comes at run time it is **Dynamic typing** ( It is not pre-compiled and compiled on the fly )

  > The code is evaluated at the run time

  

* If the error comes at the compile time it is **Static Typing**

> The code is evaluated at the compile time  

```js
var a = 1;
console.log(a); // 1
a = 'balaji';  
console.log(a); // balaji
```

> **JS is dynamically typed**

**Weakly Typed and Strongly Typed**

* If the variable has strict data-type, then it is **Strongly typed**

> The data-types must be informed before using it

* If the variable does not have strict data-type, then it is **Weakly typed**

> The data-types are decided automatically

```js
console.log(4 * '7'); // 28 (js is weakly typed)
console.log(4 + '7'); // '47'
console.log(2 + true); // 3
console.log(false - 3); // -2
```

**Hoisting**

```js
a = 1;
console.log(a); // 1
var a;
```

```js
a = 1;
console.log(a); // 1
```

In JS all the **variable declaration and function declarations**  are brought to the top.But initialization has to be done first 

```js
console.log(a); // undefined
var a;
a = 1;
```

```js
console.log(a); // undefined
var a = 1;
```

```js
console.log(a); // Reference error a is undefined
a = 1;
```

* Intialization should occur first and declaration may / may not happen at the last

**Functions**

```js
function calc() {
  console.log(2 + 3); // 5
}
calc();
```

```js
var calc = function () {
  console.log(2 + 3); // 5
}
calc();
console.log(typeof calc); // function
```

```js
var calc = function () {
  console.log(2 + 3); // 5
}
var a = calc();
a(); // 5 reference error a is not a function
console.log(a); // undefined
```

```js
var calc = function () {
 return 2 + 3;
}
var a = calc(); 
console.log(a); // 5 
```

> undefined + undefined - NaN

```js
var calc = function (a, b) {
 return a + b;
}
var c = calc; 
console.log(c(1, 2)); // 3
```

> ​	Note: **Functions** are used for re-usability of the code.

**Deterministic Functions**

These Functions output are predictable and will same output for the same input. Same outputs for same inputs.

```js
const square () {
  let a = 0;
  return true;
}
square();
```

**Non-Deterministic Functions**

These Functions output are non-predictable and will they depend on others

```js
Math.random();
```

```js
const square (a) {
  let a = 0;
  return a*a;
}
square(1);
```

**Pure Functions**

The Functions without side effects. It will not change any of its outside world code.They does not depend on time 

```js
const square () {
  let a = 0;
  return a*a;
}
```

#### Example

```js
const SurfaceAreaCalculator = radius => {
  return 4 * 3.14 * radius;
}; 
```

**Impure Functions**

The Functions with side effects

```js
let a = 0;
square(a);
const square (a) {
  return a*a;
}
```

**Closures**

Closures means that a function can access variables, methods from the outer function.( Function inside a function)

#### Example

```js
function generator(input) {
  var number = input;
  return function () {
    return number * 2;
  }
}
var calc = generator(2);
console.log(calc);
console.log(calc());
// ƒ () {
//   return number * 2;
// }
// 4
```

**IIFE**(immediately invoked function executions)

It is used for **encapsulation** (data hiding). Used for making private variables and methods.

#### Example

```js
(function() {
  console.log('hai');
})();
```

We need **IIFE ** because,

* **encapsulation**
* Using local scope
* Avoid polluting global scopes

```js
(function(inpu) {
  console.log(inp);
})(10);
// 10
```

**IIFE with closures**

```js
var obj = {};
(function() {
  obj.name = 'balaji';
})(obj);
console.log(obj);
```

**Built In Methods**

```js
function message(msg) {
  console.log(msg);
  console.log(arguments);
};
message('hai', 10);
console.log(message.name);
console.log(message.length);
// hai
// Arguments(2) ["hai", 10, callee: ƒ, Symbol(Symbol.iterator): ƒ]
// message
// 1
```

* **arguments** - returns all the parameters passed to a function. It is an **Array**. 

* functionName.name - returns **function name**

  ```js
  function message() {
    console.log('hai');
  }
  var msg = message;
  console.log(msg.name);
  // message
  ```

  

*   functionName.length - returns the number of arguments that a function expects.

**!!! Wired**

```js
 const test = function() {
  console.log('hai');
}
console.log(test.name);
// test
```

**setTimeout**

It will execute a function after an delay.

 ```js
setTimeout(function() {
  console.log('finished');
}, 2000);
//finished (after 2 secs)
 ```

**setInterval**

It will keep on executing the function after the given interval

```js
setInterval(function() {
  console.log('ping');
}, 1000);
//finished (after 2 secs)
```

**clearInterval / clearTimeout**

This is used to reset the timers

```js
var timer  = setInterval(function() {
  console.log('ping');
}, 1000);
setTimeout(function(){
  clearInterval(timer);
}, 2500);
```

**parseInt**

Used to convert into number

```js
var a = '2';
console.log(parseInt(a)); // 2
var  n  = 'kjc';
console.log(parseInt(a)); // NaN
```

This will always try to convert the string into number with base 10 by default. 

#### Syntax

```js
var a = 'FFBB123';
console.log(parseInt(a, 16)); // convert into number from base 16
```

**toString**

Used to convert into **string**

```js
var a = 10;
console.log(a.toString());
// "10"
```

**toFixed**

Used to slice floating numbers upto specified value

```js
var a = 10.223234234;
console.log(a.toFixed(2));
// "10.22 "
console.log(a.toFixed());
// 10
```

**Strings**

 ```js
var a = 'This is a test string';
console.log(a);
console.log(a.length);
console.log(a[2]);
console.log(a.charAt(2));
console.log(a.concat('another text'));
console.log(a.toUpperCase());
console.log(a.toLowerCase());
console.log(a.split(' '));
// This is a test string
// 21
// i
// i
// This is a test stringanother text
// THIS IS A TEST STRING
// this is a test string
// ['This', 'is', 'a', 'test', 'string']

 ```

```js
var b = '    This is a test string              ';
console.log(b.trim());
// This is a test string. 
```

> **trim()** will temove only the leading and trialing white spaces

**Control Structures**

```js
var a = true;
if (a) {
  console.log('works'); 
} else {
  console.log('not works');
}
```

```js
var a = true;
var b = true;
if (a) {
   console.log('works'); 
} else if(b) {
  console.log('this also works');
} else {
  console.log('not works');
}
```

> Other than 0 all the variables are treated as valid(1)

```js
null == undefined  - true;
null === undefined - false; // null and undefined has same value but not same types
NaN - typeof NaN - number
typeof null - object
typeof undefined - undefined
typeof function - function
1 == true - true
1 === true -  false
2 == true - false
0 == false - true
0 === false - false
null is treated as false in conditions
other than 0 all are treated as true
console.log(2 + '2'); // "22"
console.log(2 * "2"); // 4
console.log(1 + true); // 2
console.log(1 - true); // 0
console.log("1" + true); // "1true"
console.log(true + true); // 2
console.log(null + 12); // 12
console.log(undefined + 12); // NaN
console.log(NaN + 1); NaN
console.log("split" - 'us'); // NaN
console.log(12 - "1");  // 11
console.log(12 * "2"); // 24
console.log(1.3 * 2.2); // 2.8600000000000003
if(1.3 * 2.2 == 2.86) { // false
  console.log("true") 
}else {
  console.log("false")
}
if((1.3 * 2.2).toFixed(2) == 2.86) {  // true
  console.log("true");        
}else {
  console.log("false");
}
console.log("a" * "b"); // NaN
console.log(12 * null); // 0
console.log(1 * Infinity); // Infinity
console.log(1/Infinity); // 0
console.log(0/Infinity); // 0
console.log(1/0); // Infinity
console.log(0/0); // Infinity
console.log(2/"2"); // 1
console.log(3.3/2.3); // 1.434782608695652
console.log((3.3/2.3).toFixed(2)); // 1.43
console.log(10 % 3); // 1
console.log(typeof Infinity); // number
console.log(Infinity / 0); // Infinity
console.log(1 === 1); // true
console.log(1 == "1"); // true
console.log(1 === "1"); //false
console.log(null === null); // true
console.log(undefined === undefined); // true
console.log(NaN === NaN); // false
console.log(1 !== 2); // true
console.log(1 != '2'); // true
console.log(1 == '2'); // false
console.log(1 >= '1'); // true
console.log(null == 0); // we cant compare anything to null except undefined
console.log(null == undefined); // true
console.log(null === undefined); // false
console.log(0 == undefined); // undefined can be compared with anything 
                             // and gives false except to null in == 
console.log(null == 0); // false
console.log(1 > 1); // false
console.log(1 >= 1); // true
console.log(1 == "1"); // true
console.log(1 > "1"); // false
console.log(1 >= "1"); // true
console.log(1 >== "1"); // types cannot be compared with > // error
console.log(1 >== 1); // types cannot be compared with > // error
```

- **null** cannot be compared with anything except **undefined** and gives true when == 
- **undefined** can be compared with anything and gives false except with null when == 

**Switch Statements**

```js
var a = 8;
switch(a) {
  case 1;
    ...
    break;
  case 8:
    ...
    break;
  default:
    ...
    break;
}
```

### Loops

**For Loops**

```js
for (var i = 0;i < n;i++) {
  console.log(i);
}
```

**Nested Loops**

```js
for (var i = 0;i < n;i++) {
  for (var j = 0;j < n;j++) {
    console.log(i*j);
  }
}
```

**break and continue**

```js
for(var i = 0;i < 5;i++) {
  if (i === 1) {
      break;
   }
  console.log(i);
}
// 0 
```

```js
for(var i = 0;i < 5;i++) {
  if (i === 1) {
      continue;
   }
  console.log(i);
}
// 0 2 3 4 
```

* **break** keyword break the immediate loop
* **continue** will skip executing the statements below that are scoped within the loop

**Looping through Arrays**

```js
var a = [1, 2, 3];
for(var i = 0;i<a.length;i++) {
  console.log(a[i]);
}
```

**while loops**

```js
var a = 0;
while(a < 5) {
  console.log(a);
  a++;
}
```

**Do while loops**

```js
var condition = false;
do {
  console.log('Executed ');
} while(condition)
```

* do-while loop will be executed once always and in the second iteration, the conditions are checked

**Operators**

Operators in JS is used to maipulate the values.

Some are Listed,

* +
* -
* *
* /
* %
* **
* =, > , <, >=, <=, !=

> Operators follow **BODMAS rule**

```js
var a = 5;
var b = 10;

a += b; // a = a + b (shorthand syntax)
console.log(a); // 15
```

**Javascript** always tries to create **strings**

```js
var a = 3;
var b = '3';
console.log(a + b); // 33
```

```js
var a = true;
var b = 'join';
console.log(a + b); // truejoin
```

```js
var a = [1, 2 ,3];
var b = '3';
console.log(a + b); // 1,2,33
```

```js
var a = [1, 2 ,3];
var b = ' join';
console.log(a + b); // 1,2,3 join
```

Performing operations with undefined always gives undefined

```js
1 + undefined // undefined
1 + NaN // NaN 
```

JS has bug on multiplication and divison of **floating numbers**

```js
1.3 * 2.2 // 2.8600000000000003
3.3 / 2.3 // 1.434782608695652
```

This will be fixed with **toFixed(2)**

* == - compares the **value**
* === - compares value and the data type also

**Ternary Operators**

```js
var a = 5;
var b = 6;
a === b ? console.log('Eqaul') : console.log('Not Equal'); or
console.log(a===b ? 'Equal' : 'Not Equal');
```

**Precedence**

[Refer here for Precedence](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Operator_Precedence)

**String to Number in JS**

```js
var a = '52';
console.log(+a); // 52
console.log(Number(a)); // 52
console.log(parseInt(a)); // 52
```

### 3) Types and Scopes

**Data types**

* Numbers
* Strings
* NaN
* undefined
* null
* Objects
* Arrays

**Types**

* Primitive Type
* Reference Type

**Primitive Types**

```js
var a = 1;
var b = a;
console.log(a, b); // 1, 1
b = 2;
console.log(a, b); // 2, 1
```

So, In Primitive data types the values are copied

**Reference Types**

```js
var a = {
  'test': 5
};
var b = a; 
console.log(a, b); { 'test': 5}, { 'test': 6 }
b.test = 6;
console.log(a, b); { 'test': 6 }, { 'test': 6 }
```

In Reference types the value are not stored inside of variables but the variables are pointed to the values in the memory.In-order to prevent  polluting the memory, a and b are pointed to same memory as they have the same values

```js
var a = [1, 2, 3];
var b = a;
b.push(4);
console.log(a, b); [1, 2, 3, 4], [1, 2, 3, 4]
```

```js
var a = [1, 2, 3];
var b = a;
b = ['a', 'b', 'c']
console.log(a, b); [1, 2, 3, 4], ['a', 'b', 'c']
```

* For **Primitive types** the values are copied
* For **Refernce Types** the values are not copied but pointed to the same location(this is made not pollute the memory)

**Scope**

> It is the Registry where the variables are stored

ES5 scope,

* Global Scope(window)
* Local Scope(Nested in global scope)i.e inside function - independent from the global scope

> Note: Function can access local and global scope variables through Closures 

```js
var test = 'Global Scope';
console.log(this); // window object
console.log(this.a);  // Global. Scope
```

All the global variables are attached to window object as Global scope.

 ```js
var test = 'Global Scope';
function localScope() {
  console.log(test); // Global Scope 
}
localScope();
// This is called as closure
 ```

**Closures**

The inner function has the access to outer **variables and function**

```js
var test = 'Global Scope';
function localScope() {
  var test = 'Local Scope'
  console.log(test); // Local Scope 
}
localScope();
```

```js
var test = 'Global Scope';
function localScope() {
  var test = 'Local Scope'; 
  console.log(test);
}
localScope();
console.log(test);  
// o/p: Local Scope, Global Scope
```

```js
function test() {
  var a = 'Local scope';
  console.log(a); // Local Scope
}
test(); 
console.log(a); // a is not defined
```

```js
function test() {
  a = 'Local scope';
  console.log(a); // Local Scope
}
test(); 
console.log(a); // Local Scope
```

Now, **a** is global variable now. So it is accessed everywhere. This is not possible in **strict mode**. This is **not Recommended**

 ### 4) Arrays

 Collection of same of different data type elements

`var a = [1, 2, ,3]`

```js
var a = [1, 2, 3];
console.log(a);
console.log(a.length);
console.log(a[1]);
a[1] = 100;
console.log(a);
a[3] = 100;
console.log(a);
a[5] = 6;
console.log(a);
// [1, 2, 3], 3, 100, [1, 2, ,3 ,100], [1, 2, 3, 100, undefined, 6]
```

**forEach Loop**

### Syntax

```js
array.forEach(fucntion() {});
```

#### Example

```js
var array = [1, 2, 3];
array.forEach(function(element, index, actualArray) { 
	console.log(element, index, actualArray);
});
// 1 0 [1, 2, 3]
// 2 1 [1, 2, 3]
// 3 2 [1, 2, 3]
```

**Array Methods**

All the Array methods are available in **Array.prototype**

* push
* pop
* shift
* unshift
* indexOf
* lastIndexOf
* splice
* slice
* length
* map
* filter
* Reduce 
* join
* reverse
* concat
* join
* split
* findIndex
* Find

 **push**

```js
var a = [1, 2, 3];
a.push(4);
console.log(a);
// [1, 2, 3, 4]
```

```js
var a = [1,2,3,,];
console.log(a);
a[4] = 5;
console.log(a);
// [1, 2, 3, undefined], [1, 2, 3, undefined, 5]
```

**pop**

This array method removes the last element and returns the pop element. 

```js
var a = [1, 2, 3];
console.log(a.pop());
console.log(a);
// 3, [1, 2]
```

**unshift**

This array method pushes the element at the first

```js
var a = [1, 2, 3];
a.unshift(4);
console.log(a);
// [4, 1, 2, 3]
```

**shift**

This removes the element at the first

```js
var a = [1, 2, 3];
a.shift();
console.log(a);
// [2, 3]
```

**indexOf**

This Array method gives the current index of the passed element

#### Syntax

```js
array.indexOf(element, starting_index);
```

```js
var a = [1, 2, 3];
var index = a.indexOf('3');
console.log(index);
// 2
```

> Returns -1 if the item is not found.

**lastIndexOf**

This Array method gives the current index of the passed element. But it searches from the last

#### Syntax

```js
array.lastIndex(element, starting_index);
```

```js
var a = [1, 2, 3];
var index = a.lastIndexOf(3);
console.log(index);
```

> Returns -1 if the item is not found.

**splice**

This Array method is used to extract the part of array. This is mutable. It  does not return new array changes the same array

#### Syntax

```js
array.splice(start_index, no_of_elements);
```

```js
var a = [1, 2, 3, 4, 5];
var newArray = a.splice(2 , 2);
console.log(newArray); // [3, 4]
console.log(a); [1, 2, 5 ]
```

**slice**

This Array method  is used to extract the part of array. This is immutable. Will return new array after slicing

```js
 array.slice(start_index, end_index + 1);
```

```js
var a = [1, 2, 3, 4, 5];
var newArray = a.slice(2 , 4);
console.log(newArray); // [3, 4]
console.log(a); [1, 2, 3, 4, 5  ]
```

`array.slice()` will create a new Array

**filter**

This Array method will loop through and filter the array elements.

* return true - allows element in array
* return false - removes element from array

This is also immutable

```js
var a = [1, 2, 3, 4, 5];
var b = a.filter(fuction(ele){
   return ele >= 3;      
});
console.log(b);
console.log(a);
// [3, 4, 5], [1, 2, 3, 4, 5]
```

**map**

This Array method will loop through and applies the logic on each of the array elements.This is also immutable

```js
var a = [1, 2, 3, 4, 5];
var b = a.map(fuction(ele){
   return ele * 2;      
});
console.log(b);
console.log(a);
// [1, 4, 9, 16, 25], [1, 2, 3, 4, 5]
```

**reduce**

This is used to create a single value from the array

```js
var a = [1, 2, 3, 4, 5];
var sum = a.reduce(function(total, value) {
  return total + value;
});
console.log(sum);
// 10 start = 1
```

```js
var a = [1, 2, 3, 4, 5];
var sum = a.reduce(function(total, value) {
  return total + value;
}, 0);
console.log(sum);
// 10  start = 0
```

**reverse**

This array method reverses the array elements. This is mutable

```js
var a = [1, 2, 3, 4, 5];
a.reverse();
console.log(a); // [5, 4, 3, 2, 1 ]
```

**concat**

This array method will merges two arrays.  This is immutable

```js
var a = [1, 2, 3];
var b = [4, 5];
var res = a.concat(b);
console.log(res);
console.log(a, b)
// [1, 2, 3, 4, 5]
// [1, 2, 3] [4, 5]
```

**join**

This array method will generate a string based on the seprator passes

`array.join(seprator_array)`

```js
var a = ['old', 1, 2, 3, 4];
var b = ['join', 'me'];
console.log(a.join(b));
// 'oldjoin,me1join,me2join,me3join,me4'
```

This is used to construct a string

```js
var a = [1, 2, 3, 4];
console.log(a.join(''));
// '1234'
```

**split**

This array method is used too create an array from a string based on a seperator

`string.split(sepeartor)`

```js
var str = 'old, 1, 2, 3, 4';
console.log(str.split(', '));
// ["old", "1", "2", "3", "4"]
```

**findIndex**

This array method will give index of the element that meets the given condition

```js
var a = [1, 2, 4, 18, 20 ,30];
var ind = a.findIndex(function(ele) {
  return ele >= 18
});
console.log(ind); // 3
```

**find**

This array method will give first exact the element that meets the given condition

```js
var a = [1, 2, 4, 18, 20 ,30];
var ele = a.find(function(ele) {
  return ele >= 18
});
console.log(ele); // 18
```

### 5) Objects

Objects in javascript are map(dictionary). Object have property. **Property** is an entry in the object. It has key and value pairs

#### *3 kinds of Properties

- **Properties**: These are normal properties in an object, that is mapping from string keys to values. & 1 more is included call as `named data properties` which include `methods`
- **Accessors**: Special methods whose invocations look like reading or writing properties.(normal properties are storage locations for property values, accessors allow us to compute the values of properties).
- **Internal Properties**: These are not directly accessible from JavaScript, but there might be some indirect ways of accessing them :
  **Example** : `[[Prototype]]`holds the prototype of an object and is readable via `Object.getPrototypeof()`.

#### 2 Types of Accessors in JS

* Getter(reading a property)
* Setter(Writing a property)

#### Example

```js
// Getter
const fullName = {
  first: 'Akash',
  last: 'Rajvanshi',
  get full() {
    return `${this.first} ${this.last}`
  }
};
console.log(fullName.full) // Akash Rajvanshi
// Setter
const fullName = {
  first: 'Akash',
  last: 'Rajvanshi',
  set full(name) {
    const parts = name.split(' ')
    this.first = parts[0]
    this.last = parts[1]
  }
};

fullName.full = 'Aakash Rajvanshi';
console.log(fullName.first) // Aakash
console.log(fullName.last) // Rajvanshi 
```

#### *2 Roles of objects in JS

- Object as Records
- Object as Dictionaries

**Object as Records**

It is a type of Object, created using object literals.It have fixed number of properties, whose keys are known during run time.

> Objects-as-records have a fixed number of properties, whose keys are known at development time. Their values can have different types.

```js
const obj = {
	num: 5832
};

console.log(obj.num) // 5832
```

**Object as Dictonaries**

Objects-as-dictionaries have a variable number of properties, whose keys are not known at development time. All of their values have the same type.

```js
const obj = {
	'Can be any Number!': 5832
};

console.log(obj['Can be any Number!']) // 5832
```

```js
const anotherObj = {
  '6': 'bar'
};
console.log(anotherObj[3 + 3]) // bar (key: the string '6')
```



#### Example

```js
let name = {
  firstName: 'balaji',
  lastName: 'Venkatraman'
}; 
// This is called as object literals
```

**Object Creation**

```js
var person = {
  name: 'balaji',
  age: 22
};
console.log(person); // { name: 'balaji', age: 22}
console.log(person.name); // balaji
console.log(person['name']); // balaji
var age = 'age';
console.log(person[age]); // 22
```

Objects are datastructres with key value pairs

```js
var person = {
  name: 'balaji',
  age: 22,
  details: {
    location: 'Bangalore'
  },
  greet: function() {
    console.log('Hello')
  }
};
console.log(person.details.location); // Bangalore
person.greet(); // Hello
```

> Objects are reference types

```js
typeof person; // object
typeof person.name; // string
```

```js
var person = {
  'first-name': 'balaji',
  age: 22,
  details: {
    location: 'Bangalore'
  },
  greet: function() {
    console.log('Hello')
  }
};
console.log(person['first-name']); // balaji
```

**Changing objects values**

After the creation of objects we can also change the values of keys in objects

```js
var person = {
  name: 'balaji',
  age: 22,
  details: {
    location: 'Bangalore'
  },
  greet: function() {
    console.log('Hello')
  }
};
peron.name = 'bala';
console.log(person.name); // bala 
```

**Using this in objects**

```js
var person = {
  name: 'balaji',
  age: 22,
  details: {
    location: 'Bangalore'
  },
  greet: function() {
    console.log(this);
    console.log('Hello ' + this.name);
    console.log(age);
  }
};
person.greet();
// person object, 
// Hello balaji
// age is not defined - error   
```

**this** in the object is pointing to the object not the global window object. **this** will be always pointing to the **caller**(here person obj)

>  Note: whenever a variable is created(not in function), it is attached to window object

* If the function is an arrow function in a object then, it will be always the **window object**

```js
var person = {
  name: 'balaji',
  age: 22,
  details: {
    location: 'Bangalore'
  },
  greet: () => {
    console.log(this);
    console.log('Hello ' + this.age); 
  }
};
person.greet();
// window object, Hello undefined
```

In ES5 object always access the properties with the **this** keyword

**Alternative ways of creating Objects**

**1) Using new Object** 

```js
var newObj = new Object();
console.log(newObj); // {}
newObj.name = 'bala';
newObj.age = 22;
console.log(newObj); // { name: 'bala', age: 22}
```

**2) Using obj structure(Object literals)**

```js
var person = {
  name: 'balaji',
  age: 22
}; 
```

**Objects are Reference Types**

Two objects with same key, value pair  are always not equal, even-though, they have same key and value

```js
var person = {
  name: 'balaji',
  age: 22
}; 
var person1 = {
  name: 'balaji',
  age: 22
};
console.log(person === person1);
// false 
```

This is because **reference types** have **different memory** and **different pointers**. i.e, for reference type only pointers are stored in variables not the exact value

 **3) Using Object.create()**

```js
var obj = Object.create(null); // Object.create(<prototype>)
obj.name = 'balaji';
console.log(obj); // { name: 'balaji'}
```

Object.create(null)  does not inherit anything even **Object.prototype**

```js
var obj = Object.create(null);
console.log(obj instanceof Object);
// false
```

This will not have Object as fall back mechanism 

* **Prototypes are kind of javascript inheritance**

> All the object have a prototype. This is called as **default prototype** / **root prototype**. This will look like **Object.proptotype**

> Note: All the objects have prototypes but those objects created with **Object.create(null)** will have the configuration as null so it will not have **prototype**

**Inheritance using Object.create()**

```js
var person = {
  name: 'balaji',
  age: 22
};
var anotherPerson = Object.create(person); // This will act as a inheritance
anotherPerson.locality = 'Bangalore';
console.log(anotherPerson.locality, anotherPerson.name);
// Bangalore, balaji
```

**Prototypes**

By default all the objects have a default prototype, **Object.prototype**(typeof Object.prototype is **object**). But this is hidden for the users

```js
var person = {
  name: 'balaji',
  age: 22
};
console.log(person.prototype); // undefined
```

But some browsers implemented custom property to access the prototype of objects. This is unsafe to access and modify. **!!! DON'T USE IT !!!**. This custom property is called as  **dunder prototype** `__proto__`. All the **methods** are available in `__proto__` only

#### Example

```js
var person = {
  name: 'balaji',
  age: 22
};
console.log(person.__proto__); // Object object
```

```js
var person = {
  name: 'balaji',
  age: 22
};
console.log(person.toString()); // [Object object]
```

* This means that the person has toString method which is not defined inside but it is inheriting from the **parent** which is **Object.prototype**

```js
var person = {
  name: 'balaji',
  age: 22
};
Object.prototype.greet = function () {
  console.log('Hello');
}
person.greet(); // Hello
```

* This is happening because person( **all objects** ) is / are inheriting the from Object.prototype and we are adding greet function to it. So, with the help of **Prototype chain** this accessible.

**Prototype chain**

When we refer some property / method it will look in the **object**, if it is not there then it will look for **prototype of object**, if it is not there then it will look for **prototype of prototype of obj** and so on until **Object.prototype**.

#### Example

```js
Object.prototype.name = 'balaji';
var person = {
  age: 21,
};
const anotherPerson = Object.create(person);
anotherPerson.city = 'Bangalore';
const anotherAnotherPerson = Object.create(anotherPerson);
anotherAnotherPerson.color = 'white';
console.log(anotherAnotherPerson.color);
console.log(anotherAnotherPerson.city);
console.log(anotherAnotherPerson.age);
console.log(anotherAnotherPerson.name);
// "white"
// "Bangalore"
// 21
// "balaji" 
```

```js
var age = 30;
var me = {
  name: 'balaji',
  age: 22
}
Object.prototype.greet = function() {
  console.log('Hai '+this.name);
}
var alsoMe = Object.create(me);
alsoMe.name = 'Bala';
var thatsAlsoMe = Object.create(me);
thatsAlsoMe.name = 'Ji';
me.greet();
alsoMe.greet();
thatsAlsoMe.greet();
```

**!!! IMPORTANT !!! - IN JS this always points to the caller**

From the above example,

```js
console.log(thatsAlsoMe.__proto__ == me); // true
console.log(thatsAlsoMe.__proto__.__proto__ === Object.prototype); // true 
```

But this is **unsafe** to compare.Since `__proto__` is unsafe to compare.

**The Safe way of accessing the prototype**

```js
console.log(Object.getPrototypeOf(alsoMe) == me); // true
```

**4) Constructor Functions**

```js
function Person() {
  
}
var person = new Person();
person.name = 'balaji';
console.log(person);
console.log(person.__proto__ == Person.prototype);
console.log(person.__proto__ == Object.prototype);
// { name: 'balaji' }
// true
// false
```

```js
function Person() {
  
}
Person.prototype.greet = function() {
  console.log('Hello');
}
var person = new Person();
person.name = 'balaji';
person.greet();
```

```js
function Person() {
  this.name = 'default';
}
Person.prototype.greet = function() {
  console.log('Hello ' + this.name);
}
var person = new Person();
person.name = 'balaji';
person.greet();
// "Hello balaji"
```

```js
function Person() {
  this.name = 'default name'
}
Person.prototype.greet = function() {
  console.log('Hello ' + this.name);
}
var person = new Person();
person.greet();
// "Hello default name"
```

```js
function Person() {
  this.name = 'Default';
  this.greet = function() {
    console.log('Hai ' + this.name);
  }
}
Person.prototype.greet = function() {
  console.log('Hello ' + this.name);
}
Person.prototype.name = 'Test';

var person = new Person(); 
person.name = 'balaji';
person.greet();
// Hai balaji
```

It will try to get the values from instances `var person = new Person()`. If not found it will search for `Person()` constructor function, if not found it will search in `Person() prototype`. **Basically these are Constructor functions** 

>**Constructor Functions** allows us create Object with some default values

**instanceof**

To check whether is instance is inherting a particular Constructor function / Class

```js
function Person(){
  this.name = 'Balaji';
} 
function AnotherPerson() {
  this.name = 'Bala';
}
var person = new Person();
console.log(person instanceof Person);
console.log(person instanceof AnotherPerson);
// true
// false 
```

**Constructor functions as Setter**

```js
function Person(name, age) {
  this.name = name;
  this.age = age;
}
var person = new Person('Balaji', 21);
var anotherPerson = new Person('Bala', 22);
console.log(person); 
console.log(anotherPerson);
// { name: 'Balaji', age: 21 }
// { name: 'Bala', age: 22 } 
```

This will acts as blue print now

**Summary**

 ```js
// type 1
var person = {
  name: 'balaji'
}
// console.log(person instanceof Object); // true 

// type 2 
var person = new Object();
person.name = 'balaji'; 

// type 3 
var person = Object.create(null);
person.name = 'balaji';
// console.log(person.toString()); // error
// console.log(person instanceof Object); // false
// This is inheriting null so it will not have any instance inherited and it will not have Object as fall back mechanism

// type 4
function Person(name) {
  this.name = name
}
var person = new Person(); 
 ```

**this in Javascript**

 **`this`** in javascript always refers to the caller. `this` is not a compile time binding it is a run time binding. which dynamically refers to different things in different contexts.It depends on **call-site**. When a function is invoked, an **activation record **(otherwise known as an **execution context**) is created. This record contains information about where the function was called from(call-site), how the function was invoked, what parameters were passed, etc.. one of the properties of this record is the `this reference` , which will be used for duration of function's execution.

It can refer,

1. **window**
2. **The object**
3. **The `this` value in its immediate context.**
4. **The listening element.**

**1) Window Object**

* By default `this` refers to global object
* The meaning of `global` object is the default state for the execution context for an execution is `global`, which means if a code is being executed as part of a simple function call then `this` refers to `global` object.
  1. In Browser Environment = `window` object is a global object .
  2. In Node.js Environment = Special object `global` will be the value of this.
* `this` in global scope/simple_function/IIFE === Points to the window object
* In Strict mode, it refers to undefined

```js
console.log(this);
// window Object
```

```js
function foo (firstName, lastName) {
   console.log(this); //window
   console.log(`${firstName} ${lastName}`); //Akash Rajvanshi
}

foo("Akash", "Rajvanshi");
```

```js
(function () {
  console.log('Anonymous function'); // Anonymous Function
  console.log(this); // window object
})();
```

```js
function foo () {
   'use strict'
   console.log("Simple Function Call"); //Simple Function Call
   console.log(this); //undefined
}
foo();
```

**2) The Object**

* `this` in **constructor functions** 

  `this` in Constructor Function === Points to Newly Created Instance.

  ```js
  function Person(firstName, lastName) {
    this.first_name = firstName
    this.last_name = lastName
  
    this.displayName = function () {
      console.log(`Name: ${this.first_name} ${this.last_name}`) // Name: Akash Rajvanshi
    }
  }
  
  let person = new Person("Akash", "Rajvanshi")
  person.displayName();
  ```

* `this` in **Object's method**

  `this` in Object's Method === Points to invoker object (Parent object)

  ```js
  const Person = {
    firstName: 'Akash',
    lastName: 'Rajvanshi',
    profession () {
      console.log(this) //{ firstName: "Akash", LastName: "Rajvasnhi", profession: f{} }
    }
  }
  
  Person.profession();
  ```

  **!!!!!!!! Wired**

  ```js
  const Person = {
    name () {
      const firstName = function () {
        console.log('Akash', this);
      } // window
      firstName();
       console.log('Rajvanshi', this); // Rajvanshi {name: f}
    }
  }
  
  Person.name();
  ```

  > When it is being called as a simple function call then `this` refers to `global object` and when the same definition is invoked as an object’s method then `this` refers to the `parent object`. So the value of `this` depends on how a method is being invoked as well.

  **3) this in immediate context**

  `this` in arrow function always refers to the surrounding scope.

  * `this` in arrow function

    `this` in an arrow function always points to the same `this` value in the surrounding scope.

    ```js
    const Person = {
      name() {
        const firstName = _ => console.log('Akash', this); //Akash {name: f}
        firstName()
        console.log('Rajvanshi', this); //Rajvanshi {name: f}
      }
    }
    
    Person.name();
    ```

    ```js
    const firstName = _ => console.log('Akash', this) //Akash -> window
    firstName();
    ```

**4) The Listening element**

`this` in listing element === Points to the listening element

* `this` in listening element

  When `this` is used in an event listener, this points back to the button

  ```js
  const button = document.querySelector('button');
  
  button.addEventListener('click', function () {
    console.log(this); // button
  });
  ```

  But in arrow function

  ```js
  const button = document.querySelector('button');
  button.addEventListener('click', e => {
    console.log(this); // window
    console.log(e.currentTarget); // button
  });
  ```

 #### Example 

```js
function fn() {
  console.log(this);
}
fn();
var obj = {
  func: fn
}
obj.func();
// window object
// Object{ func: fn  }
```

Here the `this` in first console is **window object**, but in the second console it is Object. This is because the caller is obj. To get the window object in the `obj.func()` also we need to use bind

#### Example

```js
function fn() {
  console.log(this);
}
var obj = {
  func: fn
}
obj.func.bind(this)();
// window object
```

Now we are bind `this` (window object) to the function `funct`. This is will override `this` in function. With the help of this `bind` we control the what  `this`should refer to.

#### Example

```js
function fn() {
  console.log(this);
}
var obj = {
  fn: fn
}
var person = {
  name: 'balaji',
}
obj.fn.bind(person)();
// Object { name: 'balaji' }
```

```js
function test() {
  var obj = {
    name: 'balaji',
    fn: function () {
      console.log(this);
    }
  }
  obj.fn();
}
test();
// Object { name: 'balaji', fn: fn}
```

```js
var obj = {
  name: 'balaji',
  test: function() {
    console.log(this);
  }
}
obj.test();
// Object { name: 'balaji', fn: fn} 
```

```js
var video = {
  title: 'a',
  play() {
    console.log(this);
  }
}
video.play();
video.stop = function () {
  console.log(this);
}
video.stop();
// Object { title: 'a', play: fn}
// Object { title: 'a', play: fn, stop: fn}
```

```js
function playVideo () {
  console.log(this);
}
playVideo();
// window object
```

> Note: If you are in **strict mode** then this will be **undefined**

**this constructor functions**

```js
function Video (name) {
  this.name = name;
  console.log(this);
}

var video = new Video('b');
//Video {name: "b"}
```

**Rules**

* In Regular function - **window object**
* In constructor function - **Instance / caller**
* In Function which is in object - **Instance / caller**

**Wired this**

```js
var video = {
  title: 'This is',
  tags: ['a', 'b', 'c'],
  showTags() {
    this.tags.forEach(function(tag){
      console.log(this.title+' ' tag);
    })
  }
}
video.showTags();
// undefined a
// undefined b
// undefined c
```

This is because we are in callback function.This can be solved with **forEach** second parameter `forEach(callback, thisArgs)`

#### Example

```js
var video = {
  title: 'This is',
  tags: ['a', 'b', 'c'],
  showTags() {
    this.tags.forEach(function(tag){
      console.log(this.title + ' ' + tag);
    }, this);
  }
}
video.showTags();
// "This is a"
// "This is b"
// "This is c"
```

**Another Way**

```js
var video = {
  title: 'This is',
  tags: ['a', 'b', 'c'],
  showTags() {
    var _this = this;
    this.tags.forEach(function(tag){
      console.log(_this.title+' ' + tag);
    });
  }
}
video.showTags();
// "This is a"
// "This is b"
// "This is c"
```

**Factory Functions**

**Factory  ** are used to create object. It is same like Constructor functions

#### Example

```js
function createCircle(radius) {
  return {
    radius: radius,
    draw() {
      console.log('draw');
    }
  }
}
var circle = createCircle(1);
console.log(circle);
// {radius: 1, draw: ƒ}
```

**Binding Rules in JS**

- Default Binding
- Implicit Binding
- Explicit Binding
- `new` Binding
- Lexical binding
- `window` binding

**1) Default Binding**

Default binding is nothing but a normal calling method of function.

```js
function foo () {
  console.log(this.a); // 3
}
var a = 3; // because this reference the global object and here our var 'a' is global variable.
foo();
```

**2) Implicit Binding**

In Implicit binding, `this` keyword will bind with the object which stands before the dot operator. Implicit binding occurs when dot notation is used to invoke function. In Implicit binding, we use the object to call the functions with the dot operator.

```js
function foo() {
  console.log(this.a); // 2
}
const obj = {
  a: 2,
  foo // ES6 syntax of foo: foo
}
obj.foo();

```

**3) Explicit Binding**

In Explicit Binding, we can force a function call to use a particular object for `this` binding, without putting a property function reference on the object. So we can explicitly say to a function what object it should use for `this` — using functions such as `call()`, `apply()` and `bind()`.

* bind
* call
* apply

**bind, call, apply**

They are used to control the invocation of functions.They are used to borrow method from another function.It is also a kind of inheritance. 

**call(), apply()** are introduced in ES3. **bind()** is introduced in ES5. You can use `call() `  / `apply()` to invoke the function immediately. `bind()` returns a bound function that, when executed later, will have the correct context (**"this"**) for calling the original function. So `bind()` can be used when the function needs to be called later in certain events when it's useful.

* bind

`bind` allows you to change the `this` context as well. However, instead of invoking the function immediately, `bind` returns a function with the parameters you have provided.

```js
function Person(firstName, lastName) {
  this.first_name = firstName
  this.last_name = lastName

  this.showDetails = function () {
    console.log(`Name: ${this.first_name} ${this.last_name}`) // Name: Akash Rajvanshi
  }
}

const person = new Person('Akash', 'Rajvanshi')
person.showDetails.bind(person)() // This is immediately invoked
const showDetailsOfPerson = person.showDetails.bind(person) // We can invoke this function later
showDetailsOfPerson()
```



#### Example

```js
function sayName (firstName, lastName) {
	console.log(`${firstName} ${lastName}`)
}

const sayMyName = sayName.bind(null, 'Akash', 'Rajvanshi')
sayMyName() // Akash Rajvanshi
```

```js
function fn(message) {
  console.log(message + this.name);
}

var obj = {
  fn: fn,
  name: 'balaji'
}

obj.fn.bind(obj, 'Hello ')();
// Hello balaji
```

**bind** always takes multiple arguments, first arg will be always that what **this** should be bound. And rest will be function args.

* call

`call` is a function that allows us to call/invoke/activate another function. When we use `call` to call a function, we   can change the `this` context.

#### Example

```js
function sayName(firstName, lastName) {
  console.log(`${firstName} ${lastName}`)
}

sayName('Akash', 'Rajvanshi') // Akash Rajvanshi

// We can also call the function through call.
// first Parameter passed into the function call replaces the this context.
// Other values passed into the functions behave as  normal agrguments 
sayName.call(null, 'Akash', 'Rajvanshi') // Akash Rajvanshi
```

`call` is used to borrow methods from another function (or method).

#### Example

```js
const numbers = [1, 2, 3]  // Array

// Normal Method
const newArray = numbers.slice()
console.log(newArray) // [1, 2, 3]

// Another Method
const anotherNewArray = Array.prototype.slice.call(numbers)
console.log(anotherNewArray) // [1, 2, 3]
```

> People use `call` with array methods because most array methods (like `slice`, `forEach`, `filter`, and `map`) work with both arrays and array-like object.

```js
function fn(message) {
  console.log(message + this.name);
}

var obj = {
  fn: fn,
  name: 'balaji'
}

obj.fn.call(obj, 'Hello ');
// Hello balaji
```

```js
var obj = {name:"Niladri"};

var greeting = function(a,b,c){
    return "welcome "+this.name+" to "+a+" "+b+" in "+c;
};

console.log(greeting.call(obj,"Newtown","KOLKATA","WB"));
// returns output as welcome Niladri to Newtown KOLKATA in WB
```

The difference between **call** and **bind** is that call will be called automatically but for bind we should call it.

* **apply**

```js
function fn(message) {
  console.log(message + this.name);
}

var obj = {
  fn: fn,
  name: 'balaji'
}

obj.fn.apply(obj, ['Hello ']);
// Hello balaji
```

The difference between call and apply is that apply will accept arguments as an array.

```js
var myMethod = function () { 
  console.log(this.a);
};

var obj1 = {
  a: 2,
  myMethod: myMethod
};

var obj2 = {
  a: 3,
  myMethod: myMethod
};

obj1.myMethod(); // 2
obj2.myMethod(); // 3

obj1.myMethod.call( obj2 ); // 3
obj2.myMethod.call( obj1 ); // 2
```

Rather than implicit binding,  explicit binding will take precedence. 

**Hard binding**

Hard Binding: When binding is both explicit and strong.Always bind() (**Hard binding**) will take precedence that implicit and explicit bindings

#### Example

```js
function showDetails() {
  console.log(this) // { firstName: 'Akash', lastName: 'Rajvanshi' } X 3
  console.log(this.firstName, this.lastName) // Akash Rajvanshi x 3
}

var fullName = {
  firstName: 'Akash',
  lastName: 'Rajvanshi'
}

var exampleOfHardBinding = function () {
  showDetails.call(fullName)
} // Hard bounded

exampleOfHardBinding() // 1st Call
setTimeout(exampleOfHardBinding, 100) // 2nd call
// hard bound 'exampleOfHardBinding' can no longer have its 'this' overridden
exampleOfHardBinding.call(window) // 3rd Call
```

our `showDetails.call(fullname)` is an explicit binding and when we put this statement in a function then it is called as strong binding and after the strong binding the value of `this` is not overridden.

#### Example

```js
var myMethod = function () { 
  console.log(this.a);
};

var obj1 = {
  a: 2
};

var obj2 = {
  a: 3
};

myMethod = myMethod.bind(obj1); // 2
myMethod.call( obj2 ); // 2
```

```js
var myMethod = function () { 
  console.log(this.a);
};

var obj1 = {
  a: 2
};

var obj2 = {
  a: 3
};

myMethod.bind(obj1)(); // 2
myMethod.call(obj2); // 3
```

```js
var myMethod = function () { 
  console.log(this.a);
};

var obj1 = {
  a: 2
};

var obj2 = {
  a: 3
};

myMethod.bind(obj1);
myMethod.call(obj2); 
// 3
// This is because we are hard binding but not executing so call getting fired
```

```js
var myMethod = function () { 
  console.log(this.a);
};

var obj1 = {
  a: 2
};

var obj2 = {
  a: 3
};

myMethod = myMethod.bind(obj1)();
myMethod.call(obj2); 
// 2
// "error"
// "TypeError: Cannot read property 'call' of undefined
   // at gefebizuha.js:14:10
   //  at https://static.jsbin.com/js/prod/runner-4.1.7.min.js:1:13924
   // at https://static.jsbin.com/js/prod/runner-4.1.7.min.js:1:10866"


// This is happening because once myMethod.bind(obj1)() is executed it will return undefined as we are not returning anything from the myMethod function and we are trying to call so, there is error
```

**4) new binding**

```js
function foo(a) {
  this.a = a;
}

var bar = new foo( 2 );
console.log( bar.a ); // 2
```

```js
function foo(something) {
  this.a = something;
}

var obj1 = {};

var bar = foo.bind( obj1 );
bar(2);

var baz = new bar( 3 );
console.log( obj1.a ); // 2
console.log( baz.a ); // 3
```

**5) Lexical Binding**

We use Arrow function to demonstrate lexical binding, as arrow function don't have its own `this` so Instead `this` is determined lexically.

lexical binding of an arrow function cannot be overridden.

```js
// Example with Normal Function
// Value of "this" in this method is overridden to 3

function foo() {
  return function (value) {
    console.log(this.value) // 3
  }
}

var obj1 = {
  value: 2
}

var obj2 = {
  value: 3
}

var bar = foo.call(obj1)
bar.call(obj2)

// But if we use arrow function then value of "this" will not overide
// Example with arrow function

function foo() {
  return (value) => {
    console.log(this.value) //2
  }
}

var obj1 = {
  value: 2
}

var obj2 = {
  value: 3
}

var bar = foo.call(obj1)
bar.call(obj2)
```

**6) window binding**

```js
function showDetails() {
  console.log(`My Name is ${this.fullName}`); // My Name is undefined
}
const User = {
  fullName: 'Akash Rajvanshi'
};
//call without any .call()/ .apply()/ .bind()
showDetails();

//As we know in simple function "this" refer to the window object

window.fullname = 'Alash Rajavashi';

function showDetails() {
  console.log(`My Name is ${this.fullName}`); // My Name is Akash Rajvanshi
}

showDetails();
```

## Summary

### Short overview of values that `this` will be working on:

1. `this` in constructor functions and `this` directly in a method point to the object itself.
2. `this` in a global context and `this` in a simple function point to `window`.
3. `this` in an arrow function always takes up the value of `this` in its surrounding scope.
4. `this` in an event listener points to the listening element.

### Short overview of binding rules that are used with 'this' :

1. Look where the function was invoked.
2. If there is an object on left side of dot operator, then `this` refer to this object (Implicit Binding)
3. If the function invoked with `call`, `apply`, or `bind`? then `this` explicitly refer to an object.(explicit Binding)
4. If the function invoked using the `new` keyword? then the `this` keyword is refer to a newly created object that was created by JavaScript interpreter. (`new` Binding)
5. If `this` inside of an arrow function? then it is refer lexically in the enclosing (parent) scope. (lexical Binding)
6. If we are in strict mode? then `this` keyword is `undefined`.
7. if we are in global scope or in simple function scope? then `this` keyword is refer to a `window` object.

**Object.defineProperty**

It is used to create a property in an object

```js
 var account = {
	cash: 120000,
    withdraw: function(amount) {
       this.cash -= amount;
       console.log(this.cash);
    }
}
Object.defineProperty(account, 'deposit', {
  value: function(amount) {
    this.cash += amount;
    console.log(this.cash);
  }
})
account.withdraw(1000);
Object.defineProperty(account, 'name', {
  value: '01'
});
console.log(account.name);
account.name = '02';
console.log(account.name);
// 119000
// "01"
// "01"
```

This is because whenever a property is created using **defineProperty** it is **read-only**. To Change this use,

**writable in defineProperty**

```js
 var account = {
	cash: 120000,
    withdraw: function(amount) {
       this.cash -= amount;
       console.log(this.cash);
    }
}
Object.defineProperty(account, 'deposit', {
  value: function(amount) {
    this.cash += amount;
    console.log(this.cash);
  }
})
account.withdraw(1000);
Object.defineProperty(account, 'name', {
  value: '01',
  writable: true
});
console.log(account.name);
account.name = '02';
console.log(account.name);
// 119000
// "01"
// "02"
```

**enumerable in defineProperty**

```js
var person = {
  name: 'Balaji',
  age: 22,
  id: '01'
}
for(var i in person) {
  console.log(i);
}
// "name"
// "age"
// "id"
```

```js
var account = {
  name: 'Balaji',
  age: 22
};
Object.defineProperty(account, 'id', {
  value: '01'
});
for(var i in account) {
  console.log(i);
}
// "name"
// "age"
```

This is because when a property is created using **defineProperty**, then it will not appear in loop iterations, so we need use **enumerable**

#### Example

```js
var account = {
  name: 'Balaji',
  age: 22
};
Object.defineProperty(account, 'id', {
  value: '01',
  enumerable: true
});
for(var i in account) {
  console.log(i);
}
// "name"
// "age"
// "id"
```

**Getters and Setters**

```js
var account = {
	 cash: 120000,
    _name: 'Default',
    withdraw: function(amount) {
       this.cash -= amount;
       console.log(this.cash);
    }
}
Object.defineProperty(account, 'name', {
  get: function () {
    return this._name;
  },
  set: function(name) {
   this._name = name;
  }
});
console.log(account.name);
account.name = 'Test';
console.log(account.name);
```

```JS
const user = {
  _firstName: 'Akash',
  _lastName: 'Rajvanshi'
};

Object.defineProperty(user, 'name', {
  get: function() {
      return `I am ${this._firstName} ${this._lastName}`;
  },
  set: function(value) {
      console.log('Setting Name To : %s', value); // When setting another value to _firstName -> "Setting Name To : Abha"
      this._firstName = value;
  },
  enumerable: false,
  configurable: false
});

// Enumerable 
console.log('name' in user) // true
console.log(user.propertyIsEnumerable('name')) // false

// Configurable 
delete user.name
console.log('name' in user) // true

// Getter function
console.log(user.name) // I am Akash Rajvanshi

// Setter function
user.name = 'Abha'
console.log(user.name) // I am Abha Rajvanshi
const user = {
  _firstName: 'Akash',
  _lastName: 'Rajvanshi'
};

Object.defineProperty(user, 'name', {
  get: function() {
      return `I am ${this._firstName} ${this._lastName}`;
  },
  set: function(value) {
      console.log('Setting Name To : %s', value); // When setting another value to _firstName -> "Setting Name To : Abha"
      this._firstName = value;
  },
  enumerable: false,
  configurable: false
});

// Enumerable 
console.log('name' in user) // true
console.log(user.propertyIsEnumerable('name')) // false

// Configurable 
delete user.name
console.log('name' in user) // true

// Getter function
console.log(user.name) // I am Akash Rajvanshi

// Setter function
user.name = 'Abha'
console.log(user.name) // I am Abha Rajvanshi
```

* **account.name** will call **getter** 
* **account.name = 'Test'** will call setter
* **getter** will get the value from **_name**
* **setter** will set the value to **_name**

**configurable in defineProperty**

This will allows the property from the object to be deleted

* If **true**, the property can be deleted
* If **false**, the property cannot be deleted

**args of defineProperty**

* value- the value added with the property
* writable- default false-defines the over writting of property
* configurable- default **false** - defines the **delete** property of the property - if **true** property can be **deleted**, if **false** cannot be **deleted**
* set - set value
* get - gets value
* enumerable - defines whether the property should appear on iteration of object

> The enumerable property attribute defines whether the property is picked by [Object.assign()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/assign) or [spread](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)[ ](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Spread_syntax)operator. For non-[Symbols](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Symbols) properties it also defines whether it shows up in a [for...in](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in) loop and [Object.keys()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object/keys) or not.

#### Two type property attributes

* Data property - **value, writable**
* Common Properties - **enumerable, configurable**
* Accessor property - **Get, Set**

**Delete Properties from Object**

* Use **delete <property-name>**

Used to delete property from Object. `delete` returns `false` , if the property is an **own property** which cannot be deleted. otherwise returns `true` in all other case

#### Example

```js
var person = {
  name: 'Balaji',
  age: 22
}
console.log(person);
delete person.name;
console.log(person);
console.log(person.name);
// Object { name: 'Balaji', age: 22}
// Object { age: 22 }
// undefined
```

**Object.defineProperties()**

```js
const user = {}

Object.defineProperties(user, {
  // Data Property
  _name: {
  value: 'Akash',
  enumerable: false,
  configurable: false,
  writable: false
  },

  // Accessor Property
  name: {
  get: function() {
      return `I am ${this._firstName} ${this._lastName}`
  },
  set: function(value) {
      console.log('Setting Name To : %s', value) 
      this._firstName = value
  },
  enumerable: false,
  configurable: false
  }
});

// Example 
console.log('name' in user) // true
console.log('_name' in user) // true
```

**Retrive property attributies**

f you want to fetch property attributes, you can easily do with using `**Object.getOwnPropertyDescriptor().**`

- `Object.getOwnPropertyDescriptor(<object>, <propertyName>)` : Returns an object with enumerable, configurable, writable, value

#### Example

```js
const user = {
  firstName: 'Akash'
};

const descriptor = Object.getOwnPropertyDescriptor(user, 'firstName')
console.log(descriptor) // { value: 'Akash', writable: true, enumerable: true, configurable: true }
```

**Preventing Object Modification**

As we know that objects are by default mutable means we can add new properties to it but to prevent these additions we have attribute called `[[Extensible]]`, which is Boolean in nature.

if `[[Extensible]]` is `false` then we can prevent new properties from being added to an object.

By default, `[[Extensible]]` is set to be a `true` on every object

**To check the value of Extensible**

`Object.isExtensible()` - return true / false

* if true - properties can be added
* if false - properties cannot be added

1. **Preventing Extensions**

   In this method, we can use `Object.preventExtensions()` method. After this we'll never be able to add any new properties to it again.

   ```js
   const user = {
     firstName: 'Akash'
   };
   
   // Currently it is Extensible 
   console.log(Object.isExtensible(user)) // true
   
   Object.preventExtensions(user)
   console.log(Object.isExtensible(user)) // false
   
   // Trying to adding something 
   user.lastName = 'Rajvanshi'
   console.log('lastName' in user) // false ( We can't make additions to the 'user' object)
   ```

2. **Sealing Objects**

   In this method, we can use `Object.seal()` method and this function `seal` the object which means that we neither only add properties nor can remove or change their types.

   ```js
   const user = {
     firstName: 'Akash'
   }
   
   // Sealing Object
   Object.seal(user)
   console.log(Object.isSealed(user)) // true
   
   // Configurable == false ( we can't add or delete properties )
   const descriptor = Object.getOwnPropertyDescriptor(user, 'firstName')
   console.log(descriptor.configurable) // false 
   console.log(Object.isExtensible(user)) // false
   
   user.lastName = 'Rajvanshi'
   console.log('lastName' in user) // false
   
   delete user.firstName
   console.log('firstName' in user) // true
   
   // Only we can do is write existing properties 
   user.firstName = 'Abha';
   console.log(user.firstName) // Abha
   ```

3. **Freezing Objects**

   In this method we can use `Object.freeze()` method and this function `freezes` the object. which is similar to sealing function but in this method we can't also write the existing properties.

   > **Note** : frozen object can’t become unfrozen. Data properties in this method are read only.

   

   ```js
   const user = {
     firstName: 'Akash'
   }
   
   // Freezing Object
   Object.freeze(user)
   
   console.log(Object.isFrozen(user)) // true
   console.log(Object.isSealed(user)) // true
   console.log(Object.isExtensible(user)) // false
   
   // Try to update content
   user.lastName = 'Rajvanshi'
   console.log('lastName' in user) // false
   
   delete user.firstName
   console.log('firstName' in user) // true
   
   user.firstName = 'Abha'
   console.log(user.firstName) // Akash
   
   const descriptor = Object.getOwnPropertyDescriptor(user, 'firstName')
   console.log(descriptor) // { value: 'Akash', writable: false, enumerable: true, configurable: false }
   ```

   | Prevent Property                | Add Property | Delete. Property | Update Property |
   | ------------------------------- | ------------ | ---------------- | --------------- |
   | Object.preventExtensions(<obj>) | NO           | YES              | YES             |
   | Object.seal(<obj>)              | NO           | NO               | YES             |
   | Object.freeze(<obj>)            | NO           | NO               | NO              |

**Detecting Properties**

We will use the `in` operator to detect the properties because `in` operator checks if the given key exists in the hash table and it considered as the best way to determine whether the property exists in an object. Also, for performance wise it won't delay.

In some cases, we might want to check for the existence of a property only if it is an own property. `in` operator checks for both own properties and prototype properties. So we will need to take a different approach `hasOwnProperty()` function, if returns `true` when the property owns by the object, and returns `false` for prototype property.

* `in` - checks for both own property and prototype properties
* `hasOwnProperty()` - checks only the own property

#### Example

```js
const user = {
  name: 'Akash',
  age: 22,
  fullname: function () {
    console.log(this.name)
  }
};

console.log("name" in user) // true
console.log("lastName" in user) // false
console.log("fullname" in user) // true
console.log("toString" in user) // true // Also show Inherited Properties 
console.log(user.hasOwnProperty("toString")) // false
```

**To Find the property is exsisting or not**

* Use **<property-name>** in **Object**

#### Examples

```js
var person = {
  name: 'Balaji',
  age: 22
}
console.log('name' in person);
// true
```

**For in loop and For of loop**

**In Array**

```js
var a = [1, 2, 3, 4];
for(var i in a) {
   console.log(i);
}

for(var i of a) {
  console.log(i)
}
// "0"
// "1"
// "2"
// "3"
// 1
// 2
// 3
// 4
```

**In Object**

```js
var a = {
  name: 'Balaji',
  age: 22,
  id: '01'
}

for(var i in a) {
  console.log(i);
}

for(var i of a) {
  console.log(i);
}
//"name"
// "age"
// "id"
// "error"
// "TypeError: a is not iterable
   // at gefebizuha.js:13:80
   // at https://static.jsbin.com/js/prod/runner-4.1.7.min.js:1:13924
   // at https://static.jsbin.com/js/prod/runner-4.1.7.min.js:1:10866"
```

**Object.assign()**

The **`Object.assign()`** method is used to copy the values of all enumerable own properties from one or more source objects to a target object. It will return the target object.

```js
const target = { a: 1, b: 2 };
const source = { b: 4, c: 5 };

const returnedTarget = Object.assign(target, source);

console.log(target);
// expected output: Object { a: 1, b: 4, c: 5 }

console.log(returnedTarget);
// expected output: Object { a: 1, b: 4, c: 5 }

```

**cloning object using Object.assign() immutably**

```js
var obj = { a: 1 };
var copy = Object.assign({}, obj);
console.log(copy); // { a: 1 }
```

This will not work for **deep clone**.Only use this for **shallow clone**

**Deep Clone in js**

```js
var obj1 = { a: 0 , b: { c: 0 }};
var obj3 = JSON.parse(JSON.stringify(obj1));
obj1.a = 4;
obj1.b.c = 4;
console.log(JSON.stringify(obj3)); // { "a": 0, "b": { "c": 0}}
```

### Special And Advanced Methods in JS

All these special methods are made available from `Object.prototype()`

* `toString()`

  Configures how objects are converted to strings : Mainly it can be useful for debugging purposes

  ```js
  function User(firstName, lastName, age) {
    this.firstName = firstName,
      this.lastName = lastName,
      this.age = age
  }
  
  const Akash = new User('Akash', 'Rajvanshi', 22);
  
  User.prototype.toString = function getDetails() {
    return `I am ${this.firstName} ${this.lastName} (${this.age})`
  }
  console.log(Akash.toString()) // I am Akash Rajvanshi (22)
  ```

* `valueOf()`

  Configures how objects are converted to numbers

  ```js
  function Salary(grossSalary, incomeTax, employeePF, profTax) {
      this.grossSalary = grossSalary,
      this.incomeTax = incomeTax,
      this.employeePF = employeePF,
      this.profTax = profTax
  }
  
  const emp1_Salary = new Salary(478000.00, 6750.75, 15000.00, 2400.78)
  
  Salary.prototype.valueOf = function takeHomeSalary() {
    return this.grossSalary - this.incomeTax - this.employeePF - this.profTax;
  };
  
  // takeHomeSalary = 478000.00 - 6750.75 - 15000.00 - 2400.78 
  console.log(emp1_Salary.valueOf()) // 453848.47
  ```

**Other Methods**

* `Object.keys()` - retrives an array of enumerable properties.

* `propertyIsEnumerable()` - checks whether the property is enumerable.

  ​		`Object`propertyIsEnumerable('<propertyName>')

  > Note: All the enumerable properties will be present in Object.keys()

  

  ```js
  const user = {
    firstName: 'Akash',
    showDetails: function () {
      return `I am ${this.firstName} `
    }
  };
  const properties = Object.keys(user);
  
  // length = len
  let i, len;
  for (i=0, len=properties.length; i<len; i++) {
    console.log("Name: " + properties[i]); // Name: firstName,  Name: showDetails
    console.log("Value: " + user[properties[i]]); // Value: Akash,  Value: function ()
  }
  
  console.log(properties) // [ 'firstName', 'showDetails' ]
  
  // Custom Property in user
  console.log("firstName" in user); // true 
  console.log(user.propertyIsEnumerable("firstName")) // true (because it is listed in Object.keys())
  
  // Inherited Property
  console.log("length" in properties); // true 
  console.log(user.propertyIsEnumerable("length")) // false
  console.log(properties.propertyIsEnumerable("length")) // false
  ```

**Math object**

```js
console.log(Math.PI);
// 3.141592653589793
console.log(Math.E);
// 2.718281828459045
var a = -2;
console.log(Math.abs(a)); // 2
var b = 1.27;
console.log(Math.round(b)); // 1
console.log(Math.ceil(b)); // 2
console.log(Math.floor(b)); // 1 
var  c = 2;
console.log(Math.exp(c)); // e^2 // 7.38905609893065
console.log(Math.log(Math.E)); // This will do natural log // 1
console.log(Math.max(1, 10, 100)); // 100
console.log(Math.min(1, 10, 100)); // 1
console.log(Math.random()); // returns a random number from 0 to 1
```

**Date Object**

```js
var today = new Date();
console.log(today);
// To Construct a specific date
var date = new Date(YYYY, M, DD);
```

> **M** is month in the **Date object**.
>
> It starts from 0 to 11. i.e., **0 - JAN, 1 - FEB, 2 - MAR**....

**Valid Formats to be passed as Parameter**

```js
var today = new Date();
console.log(today);
// To Construct a specific date
var date = new Date(YYYY, M, DD); // M - starts from 0 to 11
var anotherDate = new Date('2019/05/01'); // MM starts from 0 to 12
```

**To get the milliseconds**

```js
var d = Date.parse('2016/02/22');
console.log(d);
// 1456079400000
```

**To construct a date string**

```js
var date = new Date();
console.log(date.getDay());  // gives the number from 0 to 6 i.e, 0 - Sun,...6 - Sat
console.log(date.getDate() + '/' + date.getMonth() + '/' + date.getFullYear());
```

> Note: JS **DATE** will take the system time.

**Regex**

**Regex** is used for validation

```js
var string = 'abc';
var pattern = /ab/;
console.log(pattern.test(string)); // true
console.log(pattern.exec(string)); // ['ab']
console.log(string.match(pattern)); // ['ab']
```

### 4) Debugging in JS

* use **try catch**

```js
try { // executed on success
  
} catch(err) { // executed on fail

} finally { // executed all the time even on success and failure
  
}
```

Usually **JS** errors break the code and stop execution. If use **try catch** this will allow JS to run without crahsing or stopping

### 5) DOM IN JS

* window - The whole browser tab
* document - The rendered/visible HTML

DOM - DOCUMENT OBJECT MODEL

**Global scope** - window Object

**Inbuilt methods in window object**

```js
window.innerWidth; // gives the inner width
window.outerWidth; // gives the outer width
window.innerHeight; // gives the inner height
window.outerHeight; // gives the outer height
window.setInterval(function() {
  console.log('hai')
}, 1000);
window.localStorage.setItem('testKey', 1000);
window.localStorage.getItem('testKey');
window.sessionStorage.setItem('testKey', 1000);
window.sessionStorage.getItem('testKey');
window.open('https://www.google.com', '_blank'); // opens a new google tab
```

**Difference between Local Storage and session storage**

localStorage - This will persist the data stored even the browser tabs are closed

sessionStorage - This will not persist the data stored when the browser is closed.

**window.location**

```js
window.location; // gives location object
window.location.protocol; // gives http: or https:
window.location.port; // gives the port that the page is loaded
window.location.pathname; // gives the pathname of the page
// Ex: https://test.com/testing - pathname = /testing. 
window.location.href; // gives the entire url of the page
location.hostname; // give the hostname
window.reload(); // reloads the page
window.replace('http://www.google.com'); // replace the loaded page with the given current url
```

**window.document**

```js
window.document; or document; // gives the entire document
document.URL; // gives the document url
document.title; // gives the document title
document.body; // gives the body HTML
document.body.children; // gives the HTMLCollection of children of the body
document.body.children[0]; // gives the first children
document.body.children[0].textContent; // gives the first children text content
document.body.children[0].textContent = 'test'; // changes the first children text content 
document.body.style.backgroundColor = 'red'; // sets the body's background into red
```

**Traversing the DOM**

```js
firstChild; // gives the first child but this includes spaces 
firstElementChild; // gives exactly the first child
lastChild; // gives the last child but this includes spaces 
lastElementChild; // gives exactly the last child
nextElementSibling; // gives the next sibling of the current child
previousElementSibiling; // gives the previous sibiling of the current child 
parentElement; // gives the parent element of the child 
```

**Accessing the DOM elements**

```js
.getElementsByTagName(<TagName/>); // returns HTMLCollection of li tags
.getElementsByClassName(<ClassName>); // returns HTMLCollection of elements with classname 
.getElementById(<ID>); // return an element with the matching ID
.getElementByName(<Name>); // return an element with the matching name
.querySelector(<TagName / className / ID / attribute>); // returns an element with matcing tag name, classname, id (gives only the first match)
.querySelectorAll(<TagName / className / ID / attribute>); // returns a node list with the matching tag name, class name, id
```

**Create Element**

```js
var newElement = document.createElement('P');
newElement.textContent = 'Test Content';
```

**Delete Element**

> Deleting an element cannot be done directly.So we will access the parent and we will delete it

#### Example ( Cross browser)

```js
var deleteElement = document.querySelectorAll(a);
deleteElement.parentElement.removeChild(deleteElement);
```

#### Example (new broswer)

```js
var deleteElement = document.querySelectorAll(a);
deleteElement.remove();
```

**Misc**

```js
appendChild();
prependChild();
insertBefore();
insertAfter();
```

**Dialogs**

```js
alert('hello');
confirm('Are you sure'); // returns true or false
var test = prompt('Enter Name'); // prompts the user to enter the name
console.log(test);
```

**Consoles and types**

**console.log**

> This will gives the output

```js
console.log('test'); // prints test to the output
```

### 6) Events

**onLoad event**

```js
window.onload = function() {
  console.lgo('window is loaded');
}
```

* Use this handler to safely access the DOM elements

**Event Listeners**

```js
elem.onclick() = function() {
  console.log('clicked');
}; // type 1
elem.addEventListener('click', function() {
  console.log('click');
}); // type 2
```

**Syntax**

```js
elem.addEventListener('event', function() {
  //logic
});
```

**Adding multiple functions for a single event**

```js
elem.onclick = function() {
  console.log('i will be executed');
};
elem.onclick = function() {
  console.log('i am also executed');
}
// here when the element is clicked only " i am also executed will be printed into the console"
```

#### Solution

> This is solved with the help of event listeners

```js
elem.addEventListener('click', function(){
  console.log('i am executed');
});

elem.addEventListener('click', function() {
  console.log('i am also executed');
})
// here when the elem is clicked both "i am executed" and "i am also executed" will be printed
```

```js
function listener1(){
  console.log('i am executed');
}
function listener2() {
  console.log('i am also executed');
}
elem.addEventListener('click', listener1);
elem.addEventListener('click', listener2);
// here when the elem is clicked both "i am executed" and "i am also executed" will be printed
```

**remove event listener**

```js
elem.removeEventListener('click', listener1);
```

**Syntax**

```js
elem.removeEventListener(event, function);
```

**Event object**

> **Javascript** by default will pass the event object on every event. This will contain the information about the event

#### Example

```js
ele.addEventListener('click', listener);
function listener(event){
  console.log(event.target);
}
```

**Bubbling and Capturing**

```html
<html>
  <body>
    <div id='outer' style='width: 100px;height: 100px; background-color: green'>
      <div id='inner' style='width: 100px;height: 100px; background-color: yellow'></div>
    </div>
  </body>
</html>
```

```js
var inner = document.getElementById('inner');
var outer = document.getElementById('outer');

inner.addEventListener('click', innerListener);
outer.addEventListener('click', outerListener);

function innerListener() {
  console.log('inner');
}

function outerListener() {
  console.log('outer');
}
// when the yellow div is clicked both 'inner and outer' will be printed(child => parent)
// when the green div is clicked 'outer' will be printed
```

* This is called as **Bubbling**. To Stop this bubbling

```js
var inner = document.getElementById('inner');
var outer = document.getElementById('outer');

inner.addEventListener('click', innerListener);
outer.addEventListener('click', outerListener);

function innerListener() {
  event.stopPropagation();
  console.log('inner');
}

function outerListener() {
  console.log('outer');
}
// when the yellow div is clicked both 'inner and outer' will be printed(child => parent)
// when the green div is clicked 'outer' will be printed 
```



**Mixins in javascript**

As defined in Wikipedia, a [mixin](https://en.wikipedia.org/wiki/Mixin) is a class containing methods that can be used by other classes without a need to inherit from it. This is used to achieve multiple inheritance in js

```js
// mixin
let sayHiMixin = {
  sayHi() {
    alert(`Hello ${this.name}`);
  },
  sayBye() {
    alert(`Bye ${this.name}`);
  }
};

// usage:
class User {
  constructor(name) {
    this.name = name;
  }
}

// copy the methods
Object.assign(User.prototype, sayHiMixin);

// now User can say hi
new User("Dude").sayHi(); // Hello Dude!
```

* Mixins can make use of inheritance inside themselves.

```js
let sayMixin = {
  say: function(phrase) {
    console.log(phrase);
  }
};

let sayHiMixin = {
  __proto__: sayMixin, // (or we could use Object.create to set the prototype here)

  sayHi() {
    // call parent method
    super.say(`Hello ${this.name}`); // (*)
  },
  sayBye() {
    super.say(`Bye ${this.name}`); // (*)
  }
};

class User {
  constructor(name) {
    this.name = name;
  }
}
// copy the methods
Object.assign(User.prototype, sayHiMixin);

// now User can say hi
new User("Dude").sayHi(); // Hello Dude!
```

**Event Mixins**

```javascript
let eventMixin = {
  /**
   * Subscribe to event, usage:
   *  menu.on('select', function(item) { ... }
  */
  on(eventName, handler) {
    if (!this._eventHandlers) this._eventHandlers = {};
    if (!this._eventHandlers[eventName]) {
      this._eventHandlers[eventName] = [];
    }
    this._eventHandlers[eventName].push(handler);
  },

  /**
   * Cancel the subscription, usage:
   *  menu.off('select', handler)
   */
  off(eventName, handler) {
    let handlers = this._eventHandlers && this._eventHandlers[eventName];
    if (!handlers) return;
    for (let i = 0; i < handlers.length; i++) {
      if (handlers[i] === handler) {
        handlers.splice(i--, 1);
      }
    }
  },

  /**
   * Generate an event with the given name and data
   *  this.trigger('select', data1, data2);
   */
  trigger(eventName, ...args) {
    if (!this._eventHandlers || !this._eventHandlers[eventName]) {
      return; // no handlers for that event name
    }

    // call the handlers
    this._eventHandlers[eventName].forEach(handler => handler.apply(this, args));
  }
};


// Make a class
class Menu {
  choose(value) {
    this.trigger("select", value);
  }
}
// Add the mixin with event-related methods
Object.assign(Menu.prototype, eventMixin);

let menu = new Menu();

// add a handler, to be called on selection:
menu.on("select", value => alert(`Value selected: ${value}`));

// triggers the event => the handler above runs and shows:
// Value selected: 123
menu.choose("123"); 
```

**Sorting in JS**

```js
var a = [1, 3, 5, 4, 2];
console.log(a.sort());
console.log(a.reverse());
// [1, 2, 3, 4, 5]
// [5, 4, 3, 2, 1]
```

**JS** has its inbuilt sorting methods.But it has back side also

```js
var a = [1, 4, 10, 20, 6, 30];
console.log(a.sort());
// [1,10,20,30,4,6]
```

**This is not the expected behaviour**

#### Reason

JS default sort always compare the elements in alphabetical order, so numerical sort will not work as expected.It always compare the elements with the **UNICODE**. Find the below table of comparision.

**Sort Table**

![img](https://miro.medium.com/max/2120/1*fnL3ZqfzmI7-J3xprPhdVw.png)

#### Solution to the Problem

```js
// asc
var a = [1, 4, 10, 20, 6, 30];
console.log(a.sort(numberComparator));
function numberComparator(firstNumber, secondNumber) {
  if(firstNumber < secondNumber) return -1;
  else if(firstNumber > secondNumber) return 1;
  else return 0;
}
// [1, 4, 6, 10, 20, 30]
```

```js
// desc
var a = [1, 4, 10, 20, 6, 30];
console.log(a.sort(numberComparator));
function numberComparator(firstNumber, secondNumber) {
  if(firstNumber < secondNumber) return -1;
  else if(firstNumber > secondNumber) return 1;
  else return 0;
}
// [30, 20, 10, 6, 4, 1]
```

**Shorthand**

```js
// asc
var a = [1, 4, 10, 20, 6, 30];
function numberComparator(firstNumber, secondNumber) {
  return firstNumber - secondNumber;
}
console.log(a.sort(numberComparator));
// [1, 4, 6, 10, 20, 30]
```

```js
// desc
var a = [1, 4, 10, 20, 6, 30];
function numberComparator(firstNumber, secondNumber) {
  return secondNumber - firstNumber;
}
console.log(a.sort(numberComparator));
// [30, 20, 10, 6, 4, 1]
```

**ES6**

```js
let myWillWorkExpectedlyArray = [3, 10, 1, 20];
myWillNotWorkExpectedlyArray.sort(() => firstNumber - secondNumber)); 
// output is [1, 3, 10, 20]
myWillNotWorkExpectedlyArray.reverse(() => firstNumber - secondNumber)); 
// output is [20, 10, 3, 1]
```

**IIFE - Immediately invokded Functions**

**Module Pattern**

**Modular Pattern** uses IIFE. This is used for **encapsulation**. 

**IIFE**

```js
(function() {
  'use strict';
  // Your code here
  // All function and variables are scoped to this function
}());
```

**Exporting Module**

```js
var myModule = (function() {
  'use strict';

  return {
    publicMethod: function() {
      console.log('Hello World!');
    }
  };
}());
     
myModule.publicMethod();  // outputs 'Hello World'
```

**Private Properties and Methods**

```js
var myModule = (function() {
  'use strict';

  var _privateProperty = 'Hello World';
    
  function _privateMethod() {
    console.log(_privateProperty);
  }
    
  return {
    publicMethod: function() {
      _privateMethod();
    }
  };
}());
  
myModule.publicMethod();                    // outputs 'Hello World'   
console.log(myModule._privateProperty);     // is undefined protected by the module closure
myModule._privateMethod();                  // is TypeError protected by the module closure
```

```js
var myModule = (function() {
  'use strict';

  var _privateProperty = 'Hello World';
  var publicProperty = 'I am a public property';

  function _privateMethod() {
    console.log(_privateProperty);
  }

  function publicMethod() {
    _privateMethod();
  }
    
  return {
    publicMethod: publicMethod,
    publicProperty: publicProperty
  };
}());
  
myModule.publicMethod();    		        // outputs 'Hello World'   
console.log(myModule.publicProperty);       // outputs 'I am a public property'
console.log(myModule._privateProperty);     // is undefined protected by the module closure
myModule._privateMethod();                  // is TypeError protected by the module closure
```

**Static keyword in JS**

**Static** keyword is used to access the **methods** of a class without initiating

#### Example( static methods)

```js
class MathUtils {
  static add(num, num2) {
    return num + num2;
  }

  static subtract(num, num2) {
    return num - num2;
  }
}

// Static Methods
console.log(MathUtils.add(1, 2)); // 3

// Cannot access static values on instance
const instance = new MathUtils();
instance.add() // error undefined
```

> **Static** methods are useful for utility methods that do not contain any state.

#### Example (Static property)

```js
class MathUtils {
  static value = '';
}

// Static Properties
MathUtils.value = 'Hello from static property';
console.log(MathUtils.value);
```

When using `static` properties, you can access them and set them any time, but they exist only on the Class itself and are not accessible to any instance of the Class.

#### Example(Static getters)

```js
class MathUtils {
  static get random() {
    return Math.random();
  }
}

// Static Getter
console.log(MathUtils.random, MathUtils.random); // two different values
```

```js
// Import stylesheets
import './style.css';

class MathUtils {
  static value = '';

  static get random() {
    return Math.random();
  }

  static add(num, num2) {
    return num + num2;
  }

  static substract(num, num2) {
    return num - num2;
  }
}

// Static Methods
console.log(MathUtils.add(1, 2));
console.log(MathUtils.substract(3, 2));

// Static Properties
MathUtils.value = 'Hello from static property';
console.log(MathUtils.value);

// Static Getter
console.log(MathUtils.random, MathUtils.random);

// Cannot access static values on instance
const instance = new MathUtils();
instance.value // error/undefined
```













































