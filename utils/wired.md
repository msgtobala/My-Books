#### WITDH, INNER WIDTH, OUTER WIDTH / HEIGHT, INNER HEIGHT, OUTER HEIGHT

![IMAGE](https://i.stack.imgur.com/2sJsn.gif)

* **width/height**  - content
* **innerWidth() / innerHeight()** - content + padding
* **outerWidth() / outerHeight()** - content + padding + border
* **outerWidth(true) / outerHeight(true)** - content + padding + border + margin

#### How NaN Works

The `**isNaN()**` function determines whether a value is [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) or not. Note, coercion inside the `isNaN` function has [interesting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/isNaN#Description) rules; you may alternatively want to use [`Number.isNaN()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN), as defined in ECMAScript 2015.

<iframe class="interactive interactive-js" frameborder="0" height="250" src="https://interactive-examples.mdn.mozilla.net/pages/js/globalprops-isnan.html" title="MDN Web Docs Interactive Example" width="100%" style="margin: 0px; padding: 10px; border: 1px solid rgb(234, 242, 244); max-width: 100%; box-sizing: border-box; background-color: rgb(245, 249, 250); color: rgb(51, 51, 51); height: 490px; width: 1014px;"></iframe>

## Syntax

```
isNaN(value)
```

### Parameters

- `value`

  The value to be tested.

### Return value

**`true`** if the given value is [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN); otherwise, **`false`**.

## Description

### The necessity of an `isNaN` function

Unlike all other possible values in JavaScript, it is not possible to rely on the equality operators (== and ===) to determine whether a value *is* [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN) or not, because both `NaN == NaN` and `NaN === NaN` evaluate to `false`. Hence, the necessity of an `isNaN` function.

### Origin of `NaN` values

`NaN` values are generated when arithmetic operations result in *undefined* or *unrepresentable* values. Such values do not necessarily represent overflow conditions. A `NaN` also results from attempted coercion to numeric values of non-numeric values for which no primitive numeric value is available.

For example, dividing zero by zero results in a `NaN` — but dividing other numbers by zero does not.

### Confusing special-case behavior

Since the very earliest versions of the `isNaN` function specification, its behavior for non-numeric arguments has been confusing. When the argument to the `isNaN` function is not of type [Number](http://es5.github.com/#x8.5), the value is first coerced to a Number. The resulting value is then tested to determine whether it is [`NaN`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/NaN). Thus for non-numbers that when coerced to numeric type result in a valid non-NaN numeric value (notably the empty string and boolean primitives, which when coerced give numeric values zero or one), the "false" returned value may be unexpected; the empty string, for example, is surely "not a number." The confusion stems from the fact that the term, "not a number", has a specific meaning for numbers represented as IEEE-754 floating-point values. The function should be interpreted as answering the question, "is this value, when coerced to a numeric value, an IEEE-754 'Not A Number' value?"

ECMAScript 2015 contains the [`Number.isNaN()`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Number/isNaN) function. `Number.isNaN(x)` is a reliable way to test whether `x` is `NaN` or not. Even with `Number.isNaN`, however, the meaning of `NaN` remains the precise numeric meaning and not simply, "not a number". Alternatively, in the absence of `Number.isNaN`, the expression `(x != x)` is a more reliable way to test whether variable `x` is `NaN` or not, as the result is not subject to the false positives that make `isNaN` unreliable.

A polyfill for `isNaN` would be (the polyfill leverages the unique never-equal-to-itself characteristic of `NaN`):

```js
var isNaN = function(value) {
    var n = Number(value);
    return n !== n;
};
```

## Examples

```js
isNaN(NaN);       // true
isNaN(undefined); // true
isNaN({});        // true

isNaN(true);      // false
isNaN(null);      // false
isNaN(37);        // false

// strings
isNaN('37');      // false: "37" is converted to the number 37 which is not NaN
isNaN('37.37');   // false: "37.37" is converted to the number 37.37 which is not NaN
isNaN("37,5");    // true
isNaN('123ABC');  // true:  parseInt("123ABC") is 123 but Number("123ABC") is NaN
isNaN('');        // false: the empty string is converted to 0 which is not NaN
isNaN(' ');       // false: a string with spaces is converted to 0 which is not NaN

// dates
isNaN(new Date());                // false
isNaN(new Date().toString());     // true

// This is a false positive and the reason why isNaN is not entirely reliable
isNaN('blabla');   // true: "blabla" is converted to a number. 
                   // Parsing this as a number fails and returns NaN
```

### Useful special-case behavior

There is a more usage oriented way to think of `isNaN()`: If `isNaN(x)` returns `false`, you can use `x` in an arithmetic expression not making the expression return `NaN`. If it returns `true`, `x` will make every arithmetic expression return `NaN`. This means that in JavaScript, `isNaN(x) == true` is equivalent to `x - 0` returning `NaN` (though in JavaScript `x - 0 == NaN` always returns false, so you can't test for it). Actually, `isNaN(x)`, `isNaN(x - 0)`, `isNaN(Number(x))`, `Number.isNaN(x - 0)`, and `Number.isNaN(Number(x))` always return the same and in JavaScript `isNaN(x)` is just the shortest possible form to express each of these terms.

You can use this, for example, to test whether an argument to a function is arithmetically processable (usable "like" a number), or if it's not and you have to provide a default value or something else. This way you can have a function that makes use of the full versatility JavaScript provides by implicitly converting values depending on context.

## Examples

```js
function increment(x) {
  if (isNaN(x)) x = 0;
  return x + 1;
}

// The same effect with Number.isNaN():
function increment(x) {
  if (Number.isNaN(Number(x))) x = 0;
  return x + 1;
}

// In the following cases for the function's argument x,
// isNaN(x) is always false, although x is indeed not a
// number, but can be used as such in arithmetical
// expressions
increment('');            // 1: "" is converted to 0
increment(new String());  // 1: String object representing an empty string is converted to 0
increment([]);            // 1: [] is converted to 0
increment(new Array());   // 1: Array object representing an empty array is converted to 0
increment('0');           // 1: "0" is converted to 0
increment('1');           // 2: "1" is converted to 1
increment('0.1');         // 1.1: "0.1" is converted to 0.1
increment('Infinity');    // Infinity: "Infinity" is converted to Infinity
increment(null);          // 1: null is converted to 0
increment(false);         // 1: false is converted to 0
increment(true);          // 2: true is converted to 1
increment(new Date());    // returns current date/time in milliseconds plus 1

// In the following cases for the function's argument x,
// isNaN(x) is always false and x is indeed a number
increment(-1);            // 0
increment(-0.1);          // 0.9
increment(0);             // 1
increment(1);             // 2
increment(2);             // 3
// ... and so on ...
increment(Infinity);      // Infinity

// In the following cases for the function's argument x,
// isNaN(x) is always true and x is really not a number,
// thus the function replaces it by 0 and returns 1
increment(String);            // 1
increment(Array);             // 1
increment('blabla');          // 1
increment('-blabla');         // 1
increment(0 / 0);               // 1
increment('0 / 0');             // 1
increment(Infinity / Infinity); // 1
increment(NaN);               // 1
increment(undefined);         // 1
increment();                  // 1

// isNaN(x) is always the same as isNaN(Number(x)),
// but the presence of x is mandatory here!
isNaN(x) == isNaN(Number(x)); // true for every value of x, including x == undefined,
                              // because isNaN(undefined) == true and Number(undefined) returns NaN,
                              // but ...
isNaN() == isNaN(Number());   // false, because isNaN() == true and Number() == 0
```

#### Best way to check whether a value is NaN or not?

```js
var isNaN = function(value) {
    var n = Number(value);
    return n !== n;
};
```

