# JAVASCRIPT - THE BASICS

## What is Javascript ? Where does Javascript run ?

**Javascript** is dynamic weekly typed programming language.It was called as **LiveScript** and renamed to Javascript due to popularity of **Java**.**Javascript** runs on the **browser**. It is very powerful for web development. It can also run on server using **node js** 

**How webpage works**

![alt image](https://raw.githubusercontent.com/msgtobala/My-Books/master/images/how-browser-works.png)

### How JS is executed ?

```flow
st=>start: Code
e=>end: Effect on Webpage
op1=>operation: Javascript Engine(Chrome - V8, Firefox - Spider Monkey)

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
    console.log(name);
  }
};
person.greet();
// person object, Hello balaji, age is not defined - error   
```

**this** in the object is pointing to the object not the global window object. **this** will be always pointing to the **caller**(here person obj)

>  Note: whenever a variable is created, it is attached to window object

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
// window object, Hello undefine
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

**2) Using obj structure**

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

Object.create(null)  does inherit anything even Object.prototype

```js
var obj = Object.create(null);
console.log(obj instanceof Object);
// false
```

This will not have Object as fall back mechanism 

* **Prototypes are kind of javascript inheritance**

> All the object have a prototype. This is called as **default prototype** / **root prototype**. This will look like **Object.proptotype**

> Note: All the objects have prototypes but those objects created with **Object.create(null)** will have the configuration as null so it will not have prototype

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
// { name: 'balaji' }, true
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
  this.name = 'default'
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

 **`this`** in javascript always refers to the caller

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

**Wiered this**

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

**Factory Functions** are used to create object. It is same like Constructor functions

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

**bind, call, apply**

They are used to control the invocation of functions.

**call(), apply()** are introduced in ES3. **bind()** is introduced in ES5. You can use `call() `  / `apply()` to invoke the function immediately. `bind()` returns a bound function that, when executed later, will have the correct context (**"this"**) for calling the original function. So `bind()` can be used when the function needs to be called later in certain events when it's useful.

* bind

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

**Hard binding** is the binding done with bind(). Always bind() (**Hard binding**) will take precedence that implicit and explicit bindings

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

**new binding**

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

**Delete Properties from Object**

* Use **delete <property-name>**

Used to delete property from Object

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

















































