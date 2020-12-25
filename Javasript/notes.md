## Converting Number to String

#### 1. Using toString() method

There is a default string method that converts the data to string. The *toString()* method returns the value of a String object.

```js
myNumber = 100
myNumber.toString() // expected result: '100'noNumber = NaN
noNumber.toString() // expected result: 'NaN'decNum = 122.33
decNum.toString() // expected result: "122.33"
```

#### 2. Using String()

The `String()` method creates a primitive String type for the number that is passed to it.

```js
myNumber = 99
String(myNumber) // expected result: '99'fltNumber = 25.54
String(fltNumber) // expected result: '25.54'
```

#### 3. Concatenating the Empty String

Adding empty string to the number value will convert the data to string is one of the simplest way to do the job. It is also considered to be faster than the above two when it comes to performance.

```js
myNumber = 22
myString = '' + myNumber // expected result: '22' fltNumber = 25.54
fltString = '' + fltNumber // expected result: '25.54'
```

#### 4. Template Strings

With the introduction of *template strings* in ES6, injecting a number inside a String is a valid way of parsing an `Integer` or `Float` data type. This is the fastest way to convert the number to string.

```js
myNumber = 22
flt = 50.205;string = `${num}`;      // expected result: '50' 
floatString = `${flt}`; // expected result: '50.205'
```

#### 5. Using toFixed() method

This is the least known method. But it can be little tricky with the decimal numbers.

```js
myNumber = 22
myNumber.toFixed() // expected result: '22'a = 56.9887
a.toFixed() // expected result: '57'
a.toFixed(4) // expected result: '56.9887'
```

## Converting String to Number

#### 1. Using parseInt()

`parseInt()` parses a string and returns a whole number. Spaces are allowed. Only the first number is returned.

```js
myString = '129' 
console.log(parseInt(myString)) // expected result: 129
```

#### 2. Using Number()

`Number()` can be used to convert JavaScript variables to numbers. We can use it to convert the string too number.

If the value cannot be converted to a number, ***NaN\*** is returned.

```js
Number("10");          // returns 10
Number(" 10  ");       // returns 10
Number("10.33");       // returns 10.33
```

#### 3. Using Unary Operator (+)

The unary plus operator (`+`) precedes its operand and evaluates to its operand but attempts to convert it into a number, if it isn't already.

```js
const x ='25';
const y = '-25';
console.log(+x); // expected output: 25
console.log(+y); // expected output: -25
console.log(+''); // expected output: 0
```

#### 4. Using parseFloat()

`parseFloat()` parses a string and returns a number. Spaces are allowed. Only the first number is returned:

```js
parseFloat("10");        // returns 10
parseFloat("10.33");     // returns 10.33
parseFloat("10 20 30");  // returns 10
parseFloat("10 years");  // returns 10
parseFloat("years 10");  // returns NaN
```

#### 5. Using Math.floor()

The `Math.floor()` function returns the largest integer less than or equal to a given number.

```js
str = '1222'
console.log(Math.floor(str)) // returns 1222
```

#### 6. Multiply with number

Multiplying the string value with the **1** which won’t change the value and also it will be converted to number by default.

```js
str = '2344'
console.log(str * 1) // expected result: 2344
```

#### 7. Double tilde (~~) Operator

We can use the double tilde operator to convert the string to number.

```js
str = '1234'
console.log(~~str) // expected result: 1234negStr = '-234'
console.log(~~negStr) // expected result: -234
```

