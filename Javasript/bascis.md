# JAVASCRIPT - THE BASICS



## Where does Javascript run ?

**Javascript** runs on the **browser**. It is very powerful for web development. It can also run on server using **node js** 

## Versions of Javascript / What is ECMAScript

ECMAScript is a superset of Javascript which has all the standardization to be implemented. **Javascript** is a dialect of ES.

* Versions - ES5, ES6....

> Note: **ES5** is supported by all the browsers, **ES6** is not supported yet and we need **polyfills** to be supported.
>
> Polyfills - Used to support browsers for ES6 features as ES6 features are not supported in the browsers.
>
> We can use pre-processors also like **Babel**

## Language Basics

### 1) Script Tag

All the Javascript inside the script will be executed. Browser will start parsing the DOM from the top. So, if you include in the `<head>` , it will execute at the time of parsing only. But the DOM is not loaded yet. Therefore DOM objects cannot be accessed. So keep `<script>` imports at the bottom at the closing of `<body>` tag.

Also, if you have long running javascript that is placed on the `<head>` that can block page rendering eventhough the page is small. Hence, the place always matters.  

#### Sample

```html
<script type='text/javascript'>console.log('hai')</script> // type is optional attr. This is **inline js**
```

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

### 2) Variables

 **Variables** are storages for data.

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

**typeOf** will give the data-type of variables

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

* If the error comes at run time it is **Dynamic typing**
* If the error comes at the compile time it is **Static Typing**

```js
var a = 1;
console.log(a); // 1
a = 'balaji';  
console.log(a); // balaji
```

> **JS is dynamically typed**

**Weakly Typed and Strongly Typed**

* If the variable has strict data-type, then it is **Strongly typed**
* If the variable does not have strict data-type, then it is **Weakly typed**

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

These Functions output are predictable and will same for the same input. Same outputs for same inputs.

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

**Control structures**

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

> ​	Other than 0 all the variables are treated as valid(1)

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

### 3) Types and Scopes

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

* push
* pop
* shift
* unshift
* splice
* slice

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



















































