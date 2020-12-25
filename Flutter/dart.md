# Dart Programming

Dart has the best of all other programming languages.Dart code runs inside of isolates. Each isolate has its own **memory heap**, ensuring that no isolate’s state is accessible from any other isolate.

Dart is a programming language optimized for building user interfaces with features for expanding collections, and for customizing the UI for each platform.

> **HOT RELOAD IN FLUTTER**
>
> Hot reload works by injecting updated source code files into the running Dart Virtual Machine (VM). After the VM updates classes with the new versions of fields and functions, the Flutter framework automatically rebuilds the widget tree, allowing you to quickly view the effects of your changes.

Dart has an AOT (Ahead of Time) compiler, which compiles to fast, predictable, native code that allows almost all of Flutter to be written in Dart. This not only makes Flutter fast but ensures that virtually everything (including all the widgets) can be customized.

Dart starting point

```dart
void main(){
  // code here
}
```

```dart
main() {
  // Printing the text 'Hello World'
  print("Hello World");
}
```

Dart is a **Imperative programming**

The code that appears inside of the `main()` function gets executed in order of appearance.

```dart
main() {
  print("Hello World");
  print("From Dart");
}
```

When you run the code above, the print statement on **line 2** will execute first and then the second print statement on **line 3** will execute.

This style of programming is called **imperative programming**. It is essentially a programming paradigm wherein you write a set of instructions that execute in sequential order. Imperative programming doesn’t necessarily describe *what* the program should accomplish, rather it shows *how* the program should accomplish it. So, in this case, we have created a program that goes first and prints out the text *Hello World* and then moves on to the next line and prints the text *From Dart*.

```dart
import 'dart:io';

main() {
    print("Hello " + stdin.readLineSync());
}
```

Dart is Object oriented programming language.

### What is an Object

Every object has *characteristics* and *behaviors*. For instance, a person has characteristics such as their name, age, and height. A person can also perform behaviors such as walking, eating, and sleeping. These characteristics and behaviors combined define who the person is.

![img](https://www.educative.io/api/collection/10370001/6069685319630848/page/4936411792801792/image/4803451651358720)

In the same way, everything in Dart is an object. Objects in a programming language also have characteristics known as **properties** and they can also perform behaviors known as **methods**. Properties represent what the object knows, and methods represent what the object can do.

### Variables

Variables are used for storing information which can then be used by the computer program.

![img](../images/variables.png)

```dart
main() {
  int myFirstDartVariable = 5;
}
```

![img](../images/numbers.svg)

### Data types

- Numbers
- Strings
- Booleans
- Lists
- Sets
- Maps
- Runes
- Symbols

## Values and References [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/xVvQvDQ920P#values-and-references)

1. **Reference type**
2. **Value type**

In most languages, primitive data types are value types, but in Dart, **all** data types are objects. This means that even primitive data types are reference types. Therefore, we can say that in Dart, variables specifically store references and are referring to objects.

### Default Value [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/xVvQvDQ920P#default-value)

Uninitialized variables have an initial value of `null`. Even variables with numeric types are initially `null` because numbers—like everything else in Dart—are objects. `null` simply means that the variable is not referencing an object; it’s not referencing anything.

In the code snippet below, we are creating a variable `notInitialized` without initializing it. When we try to print the value of `notInitialized`, we get `null` as the output.

```dart
main() {
    int notInitialized;
    print(notInitialized);
} 
// null
```

```dart
main() {
  num firstNumber = 5;
  num secondNumber = 5.1;
  num thirdNumber = firstNumber;

  // Driver Code
  print(firstNumber);
  print(secondNumber);
  print(thirdNumber);
}
```

 **Dart numbers are further divided into two subtypes:**

integers (int)
doubles (double)
Both int and double are subtypes of num.

### Strings

A Dart string is a sequence of **UTF-16** code units. **UTF** stands for *Unicode Transformation Format*. [Unicode](https://unicode-table.com/en/#0041) is a set of characters in which each character is a unique code unit.

## String Concatenation

To concatenate two strings means to join them together. Concatenation of two or more strings is done using the `+` operator.

```dart
main() {
  String s1 = "First half of the string. ";
  String s2 = "Second half of the string";
  print(s1 + s2);
}
```

![img](../images/template_literals.png)

![img](../images/expressions.png)

```dart
main() {
  String country = "Japan";

  print("I want to visit $country");
}
```

```dart
main() {
  print("The sum of 5 and 3 equals ${5+3}.");
}
```

```dart
main() {
  var s1 = 'String ''test';
  print(s1);
}
// Stringtest
```

```dart
main() {
  var s1 = 'String '
    'concatenation'
    " works even over line breaks.";
    
  print(s1);
}
```

```dart
main() {
  var multilineString = """This is a 
multiline string
consisting of 
multiple lines""";

  print(multilineString);
}
```

## Booleans

```dart
main() {
  bool b1 = true;
  print(b1);
}
```

```dart
void main() {
  var a = 1;
  var b = 2; // not null
  print(b ??= a); // -> prints b as 2
}

void main() {
  var a = 1;
  var b; // null
  print(b ??= a); // -> prints b as 1, since b is null a will be assigned to b 
}
```

## Null-aware operators

Dart offers some handy operators for dealing with values that might be null. One is the `??=` assignment operator, which assigns a value to a variable only if that variable is currently null:

```dart
int a; // The initial value of a is null.
a ??= 3;
print(a); // <-- Prints 3.

a ??= 5;
print(a); // <-- Still prints 3.
```

```dart
print(1 ?? 3); // <-- Prints 1.
print(null ?? 12); // <-- Prints 12.
```

## Conditional property access

To guard access to a property or method of an object that might be null, put a question mark (`?`) before the dot (`.`):

```dart
myObject?.someProperty
```

The preceding code is equivalent to the following:

```dart
(myObject != null) ? myObject.someProperty : null
```

You can chain multiple uses of `?.` together in a single expression:

```dart
myObject?.someProperty?.someMethod()
```

```dart
var a = 1;
var b = 2;
print(a?.b); // It will check if a is null, here a is not null then a.b = 1.2 = 2;
 

var a;
var b = 2;
print(a?.b); // a is null, hence a.b cannot be performed hence null
```

## Cascades

To perform a sequence of operations on the same object, use cascades (`..`). We’ve all seen an expression like this:

```dart
myObject.someMethod()
```

It invokes `someMethod()` on `myObject`, and the result of the expression is the return value of `someMethod()`.

Here’s the same expression with a cascade:

```dart
myObject..someMethod()
```

Although it still invokes `someMethod()` on `myObject`, the result of the expression **isn’t** the return value — it’s a reference to `myObject`! Using cascades, you can chain together operations that would otherwise require separate statements. For example, consider this code:

```dart
var button = querySelector('#confirm');
button.text = 'Confirm';
button.classes.add('important');
button.onClick.listen((e) => window.alert('Confirmed!'));
```

With cascades, the code becomes much shorter, and you don’t need the `button` variable:

```dart
querySelector('#confirm')
..text = 'Confirm'
..classes.add('important')
..onClick.listen((e) => window.alert('Confirmed!'));
```

## Getters and setters

You can define getters and setters whenever you need more control over a property than a simple field allows.

For example, you can make sure a property’s value is valid:

```dart
class MyClass {
  int _aProperty = 0;

  int get aProperty => _aProperty;

  set aProperty(int value) {
    if (value >= 0) {
      _aProperty = value;
    }
  }
}
```

You can also use a getter to define a computed property:

```dart
class MyClass {
  List<int> _values = [];

  void addValue(int value) {
    _values.add(value);
  }

  // A computed property.
  int get count {
    return _values.length;
  }
}
```

## Use raw string

A raw string can be used to avoid escaping only backslashes and dollars.

```dart
//Don't
var s = 'This is demo string \\ and \$';


//Do
var s = r'This is demo string \ and $';
```

```dart
try {
  breedMoreLlamas();
} on OutOfLlamasException {
  // A specific exception
  buyMoreLlamas();
} on Exception catch (e) {
  // Anything else that is an exception
  print('Unknown exception: $e');
} catch (e) {
  // No specified type, handles all
  print('Something really unknown: $e');
}
```

**Multi constructors**

```dart
void main() {
  print(Point.fromJson({'x': 1, 'y': 2}).x);
}

class Point {
  final x;
  final y;
  
  Point(this.x, this.y);
//   factory Point.fromJson(Map<String, num> json)
//     {
//         return Point(json['x'],json['y']);
//       }
  
  Point.fromJson(Map<String, num> json)
    : x = json['x'],
      y = json['y'] { Point(x, y); }
}
```

## Named constructors

To allow classes to have multiple constructors, Dart supports named constructors:

```dart
class Point {
  double x, y;

  Point(this.x, this.y);

  Point.origin() {
    x = 0;
    y = 0;
  }
}
```

To use a named constructor, invoke it using its full name:

```dart
final myPoint = Point.origin();
```

## Factory constructors

Dart supports factory constructors, which can return subtypes or even null. To create a factory constructor, use the `factory` keyword:

```dart
class Square extends Shape {}

class Circle extends Shape {}

class Shape {
  Shape();

  factory Shape.fromTypeName(String typeName) {
    if (typeName == 'square') return Square();
    if (typeName == 'circle') return Circle();

    print('I don\'t recognize $typeName');
    return null;
  }
}
```

## Redirecting constructors

Sometimes a constructor’s only purpose is to redirect to another constructor in the same class. A redirecting constructor’s body is empty, with the constructor call appearing after a colon (`:`).

```dart
class Automobile {
  String make;
  String model;
  int mpg;

  // The main constructor for this class.
  Automobile(this.make, this.model, this.mpg);

  // Delegates to the main constructor.
  Automobile.hybrid(String make, String model) : this(make, model, 60);

  // Delegates to a named constructor
  Automobile.fancyHybrid() : this.hybrid('Futurecar', 'Mark 2');
}
```

## Type Inference and Annotation

Dart is strongly typed. Strongly typed languages take extra precaution and have rules and restrictions to ensure that a variable’s value always matches the variable’s static type.Also dart has type interference.

Although types are mandatory in Dart, **type annotations** are optional because of **type inference**

```dart
main() {
  var bookTitle = "Lord of the Rings: The Fellowship of the Ring";
  var bookAuthor = "J. R. R. Tolkien";
  var bookNoOfPages = 423;

  // Driving Code
  print(bookTitle);
  print(bookAuthor);
  print(bookNoOfPages);
}
```

### To know the datatype of a variable

```dart
main() {
  var bookTitle = "Lord of the Rings: The Fellowship of the Ring";

  print(bookTitle.runtimeType);
}
```

#### Using Type Annotations [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/NE03Lr5M5pD#using-type-annotations)

Remember when we said that variable types are inferred from their initial value? It’s also important to mention that subsequent assignments are not considered. This means that too precise a type may be inferred. If that is not desired, you can add type annotation.

In the example below, we are declaring a variable, `number`, using the `var` keyword. We want the variable to hold any type of number, i.e., `int` and `double`.

```dart
main() {
  var number = 3;
  print(number);

  number = 3.2;
  print(number);
}
```

When you run the code snippet above, you will get an error. When we initialized `number` with an integer, the compiler inferred that `number` is of type `int`. Hence, when we reassigned it a value of type `double`, the compiler displays an error.

Here, we can use type annotation and declare the `number` variable using the `num` data type. Remember that type `num` is generic enough to hold both `int` and `double`.

```dart
main() {
  num number = 3;
  print(number);

  number = 3.2;
  print(number);
}
```

### Dynamic Types [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/NE03Lr5M5pD#dynamic-types)

```dart
main() {
  dynamic dynamicVariable = 'A string'; // type String
  print(dynamicVariable);

  dynamicVariable = 5; // type int
  print(dynamicVariable);

  dynamicVariable = true; // type bool
  print(dynamicVariable);
}
```



![img](https://www.educative.io/api/collection/10370001/6069685319630848/page/4506757625806848/image/5302076584230912)

## Compile-Time and Run-Time [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/myGvnDxnKR0#compile-time-and-run-time)

Compile-time and runtime are programming terms that refer to different stages in a program’s lifetime. In order to create a program, you first write some source code. The source code defines how the program will function.

Now that we know what compilation is, let’s take that as our base and learn about compile-time through an example.

We have been defining some `int` and `double` variables in our programs with initial values. These variables will always have the same initial value whenever we run the program. These values are *fixed* at the time of *compilation*. Such things are said to be fixed at **compile-time**.

### Run and Run-Time [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/myGvnDxnKR0#run-and-run-time)

After a program is compiled, we can **run** it.

Remember when we took user input from the user in one of the previous [lessons](https://www.educative.io/collection/page/10370001/6069685319630848/4706459042447360)? We could point out that the value displayed by the print statement could change every time we run the program, depending on what the user types. Things that can’t be determined until the program is actually run are said to be fixed at **run-time**.

### Using `final` [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/myGvnDxnKR0#using-final)

A final variable (a variable created using the `final` keyword) is initialized the first time it is used and can only be set once. In other words, the final value will be known at *runtime*.

```dart
import 'dart:io';
 
main() {
  final name = stdin.readLineSync();
  print("Hello " + name);
}
```

### Using `const` [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/myGvnDxnKR0#using-const)

A constant variable (a variable created using the `const` keyword) should be created when you know the value at *compile-time*. Like a final variable, a constant variable can also only be set once

```dart
main() {
  const name = "Bob";

  // Driver Code
  print(name);
}
```

## Types of Operators

Operators are symbols that perform *operations* used for modifying or manipulating data. Manipulating data is an essential part of any programming language, and Dart is no different, providing a rich set of operators for its basic types.

- Arithmetic Operators
- Equality and Relational Operators
- Type Test Operators
- Assignment Operators
- Logical Operators
- Bitwise and Shift Operators

Expressions are composed of two things; *operands* and *operators*.

![Operators](../images/operators.svg)

### Arithmetic Operators

| **Operator** | **Use**                                                      |
| ------------ | ------------------------------------------------------------ |
| `+`          | Adds two operands                                            |
| `-`          | Subtracts the second operand from the first                  |
| `-`expr      | Reverses the sign of the expression (unary minus)            |
| `*`          | Multiplies both operands                                     |
| `/`          | Divides the first operand by the second operand.(Gives the exact value of division ). |
| `~/`         | Divides the first operand by the second operand and returns an integer value(Divides and gives only the integer value) |
| `%`          | Gets the remainder after division of one number by another   |

```dart
main() {
  var operand1 = 10;
  var operand2 = 7;

  print(operand1 + operand2);
  print(operand1 - operand2);
  print(- operand1);
  print(operand1 * operand2);
  print(operand1 / operand2);
  print(operand1 ~/ operand2);
  print(operand1 % operand2);
}

// 17
// 3
// -10
// 70
// 1.4285714285714286
// 1
// 3
```

| **Operator** | **Use**       |
| ------------ | ------------- |
| `++`var      | var = var + 1 |
| var`++`      | var = var + 1 |
| `--`var      | var = var - 1 |
| var`--`      | var = var - 1 |

### ++var [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/gxq6pGZ414G#var)

The expression value of `++var` is `var+1`. When we insert the expression in a print statement, the compiler first increments the variable by **1** and then prints the value of the variable.

```dart
main() {
  var prefixIncrement = 5;

  print(++prefixIncrement);
}

// 6
```

### var++ [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/gxq6pGZ414G#var-2)

The expression value of `var++` is `var`. When we insert the expression in a print statement, the compiler first prints the value of the variable and then increments it by **1**.

```dart
main() {
  var postfixIncrement = 5;

  print(postfixIncrement++);
  print(postfixIncrement);
}

// 5
// 6
```

### - -var [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/gxq6pGZ414G#-var)

The expression value of `--var` is `var-1`. When we insert the expression in a print statement, the compiler first decrements the variable by **1** and then prints the value of the variable.

```dart
main() {
  var prefixDecrement = 5;

  print(--prefixDecrement);
}

// 4
```

### var- - [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/gxq6pGZ414G#var-)

The expression value of `var--` is `var`. When we insert the expression in a print statement, the compiler first prints the value of the variable and then decrements it by **1**.

```dart
main() {
  var postfixDecrement = 5;

  print(postfixDecrement--);
  print(postfixDecrement);
}
// 5
// 4
```



### Equality and Relational Operators

![Equality and Relational Operators](../images/equality.svg)

| **Operator** | **Use**                                                      |
| ------------ | ------------------------------------------------------------ |
| `==`         | Checks if the values of the two operands are equal (true if equal) |
| `!=`         | Checks if the values of the two operands are not equal (true if not equal) |
| `>`          | Checks if the value of the left operand is greater than the value of the right operand |
| `<`          | Checks if the value of the left operand is less than the value of the right operand |
| `>=`         | Checks if the value of the left operand is greater than or equal to the value of the right operand |
| `<=`         | Checks if the value of the left operand is less than or equal to the value of the right operand |



### Type Test Operators

![Type Test Operators](../images/type.svg)

| Operator | Use                                        |
| -------- | ------------------------------------------ |
| `as`     | typecast                                   |
| `is`     | True if the object has the specified type  |
| `is!`    | False if the object has the specified type |

![type-operator](../images/type-operator.svg)

```dart
main() {
  double type1 = 5.0;
  int type2 = 87;
  String type3 = "educative";
  bool type4 = true;

  print(type1 is int);
  print(type2 is int);
  print(type3 is String);
  print(type4 is double);
  print(type4 is! double);
}

// false
// true
// true
// false
// true
```



### Assignment Operators

![Assignment Operator](../images/assignment.svg)



### Compound Assignment Operators 

| =    | -=   | /=   | %=   | >>=  | ^=   |
| ---- | ---- | ---- | ---- | ---- | ---- |
| +=   | *=   | ~/=  | <<=  | &=   | \|=  |

![compound operator](../images/compound operator.svg)

It’s equivalent to the following:

![compound equivalent](../images/compound equivalent.svg)

`+=`

```dart
main() {
  var A = 10;
  var B = 7;
  
  print("Before using a compound assignment operator:");
  print(A);

  A += B;

  print("After using a compound assignment operator:");
  print(A);
}

// 10
// 17
```

### `&=` (performs binary AND)

```dart
main() {
  var A = 10;
  var B = 7;
  
  print("Before using a compound assignment operator:");
  print(A);

  A &= B;

  print("After using a compound assignment operator:");
  print(A);
}
```



### Logical Operators

| **Operator** | **Name**    | **Use**                                                      |
| ------------ | ----------- | ------------------------------------------------------------ |
| `!`          | Logical NOT | Reverses the logical state of its operand. If a condition is true, then the Logical *NOT* operator will make it false |
| `||`         | Logical OR  | If any of the two operands is not false, then the result is true |
| `&&`         | Logical AND | If both the operands are not false, then the result is true  |

![Logical](../images/logical.svg)

> `!` is a unary operator, i.e., it takes one operand.

![logical_ops](../images/logical_ops.svg)

```dart
main() {
  var A = true;
  var B = false;
  var expr = A && B; //false

  print(!A); // !true --> false
  print(!B); // !false --> true
  print(true || expr); // true || expr --> true
  print(false || expr); // false || expr --> expr
  print(true && expr); // true && expr --> expr
  print(false && expr); // false && expr --> false
}
```



### Bitwise and Shift Operators

![bit-wise](../images/bit-wise.svg)

| **Operator** | **Name**                     | **Use**                                                      |
| ------------ | ---------------------------- | ------------------------------------------------------------ |
| `&`          | Bitwise **AND**              | If the corresponding bit in both operands is **1** it will give a **1**, else **0** |
| `|`          | Bitwise **OR**               | If the corresponding bit in at least one operand is **1** it will give a **1**, else **0** |
| `^`          | Bitwise **XOR**              | If the corresponding bit in only one operand is **1** it will give a **1**, else **0**. Same 0 different 1 |
| `~`          | Unary Bitwise **Complement** | Bits which are **0** become **1** and bits which are **1** become **0** [+12 => (-)13][-12 => (+)11] |

### Shift Operator

| **Operator** | **Name**    | **Use**                                                      |
| ------------ | ----------- | ------------------------------------------------------------ |
| `<<`         | Shift Left  | Shifts all the bits of its operand to the left by the specified amount |
| `>>`         | Shift Right | Shifts all the bits of its operand to the right by the specified amount |

> Both bitwise and shift operators work on binary numbers.
>
> The numbers are stored in binary form. However, we see the operands and the results in decimal, while the operations take place in binary.

![bitwise-rules](../images/bitwise-rules.svg)

![bitwise-and](../images/bitwise-and.svg)

### Right Shift

![Shift](../images/shift.png)



### Precedence Table

| **Description** | **Operator**                                  |
| --------------- | --------------------------------------------- |
| Unary postfix   | `.`, `?.`, `++`, `--`, `[``]`, `()`           |
| Unary prefix    | `-`, `!`, `˜`, `++`, `--`, `await`            |
| Multiplicative  | `*`, `/`, `˜/`, `%`                           |
| Additive        | `+`, `-`                                      |
| Shift           | `<<`, `>>`, `>>>`                             |
| Bitwise AND     | `&`                                           |
| Bitwise XOR     | `ˆ`                                           |
| Bitwise OR      | `|`                                           |
| Relational      | `<`, `>`, `<=`, `>=`, `as`, `is`, `is!`       |
| Equality        | `==`, `!=`                                    |
| Logical AND     | `&&`                                          |
| Logical Or      | `||`                                          |
| If-null         | `??`                                          |
| Conditional     | `?` `:`                                       |
| Cascade         | `..`                                          |
| Assignment      | `=`, `*=`, `/=`, `+=`, `-=`, `&=`, `ˆ=`, etc. |

## Dart Collections

#### Functions

In computer programming, a function or a method is a block of code that performs a specific task. The block of code is given a name, much like a variable. The function is called using this name whenever that specific task needs to be performed. This removes the need to type the same code over and over again; all you have to do is call the function’s name.

Like mathematical functions, programming functions take in an input, known as an **argument**, perform some operations on that input, and then return the resulting output.

![Functions](https://www.educative.io/api/collection/10370001/6069685319630848/page/5717658492207104/image/5116049630429184.png)

We can divide functions into two broad categories:

- Built-In Functions
- User-Defined Functions

Examples

```dart
main() {
  String s1 = "hello";
  print(s1.indexOf("o"));
}
```

## Optional positional parameters

Dart has two kinds of function parameters: positional and named. Positional parameters are the kind you’re likely familiar with:

```dart
int sumUp(int a, int b, int c) {
  return a + b + c;
}
// ···
  int total = sumUp(1, 2, 3);
```

With Dart, you can make these positional parameters optional by wrapping them in brackets:

```dart
int sumUpToFive(int a, [int b, int c, int d, int e]) {
  int sum = a;
  if (b != null) sum += b;
  if (c != null) sum += c;
  if (d != null) sum += d;
  if (e != null) sum += e;
  return sum;
}
// ···
  int total = sumUpToFive(1, 2);
  int otherTotal = sumUpToFive(1, 2, 3, 4, 5);
```

Optional positional parameters are always last in a function’s parameter list. Their default value is null unless you provide another default value:

```dart
int sumUpToFive(int a, [int b = 2, int c = 3, int d = 4, int e = 5]) {
// ···
}
// ···
  int newTotal = sumUpToFive(1);
  print(newTotal); // <-- prints 15
```

## Collections

**Collections** are objects that group other objects together according to a conceptual schema. For example, a dictionary is a collection of words and a card deck is a collection of cards.

Another name for collections is *data structures* and there is a good reason for that. **Data structures** are a means of structuring data. They are used to store, manipulate, and retrieve all types of data.

![Collections](../images/collections.svg)



`List`, `Set`, and `Map` are all types in Dart. A variable can be of the above three types along with the primitive types.

### List: The Dart Array

**Lists** are an *ordered* collection of objects. This means that every element in a list has a fixed position. Use a List when you need to access objects by index.

### Creating a List [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/qAEGvv8k8V7#creating-a-list)

#### * Using Literals

The simplest way is using literals along with square brackets (`[]`).

![Lists](../images/list.svg)

```dart
main() {
  var simpleList = [1,2,3];

  print(simpleList);
}
```

> Remember how we said that `List` is a type when we were discussing [data types](https://www.educative.io/collection/page/10370001/6069685319630848/5618358982541312)? Well in the code above, Dart [infers](https://www.educative.io/collection/page/10370001/6069685319630848/5672642201780224) that `simpleList` has a type `List` (a `List` with elements of type `int`).

#### Using a Constructor [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/qAEGvv8k8V7#using-a-constructor)

You can also declare a list using a *List constructor*. A **List constructor** creates an object using the `List` keyword followed by parenthesis (`()`).

![List](../images/dynamic_list.svg)

```dart
main() {
  var listOfVegetables = List();

  print(listOfVegetables);
}
```

```dart
main() {
  var listOfVegetables = List(2);

  print(listOfVegetables);
}
```

#### List with Type

Instead of depending on Dart’s type inference, we can specify the type that a list should contain.

![List With Type](../images/list_with_type.svg)

```dart
main() {
  var listOfVegetables = List<String>();

  print(listOfVegetables is List<String>);
}
// true
```

Lists use zero-based indexing. This means that the first element of a list is located at the **0th** index.

![Indexing](../images/indexing.svg)

Since each element has its own position, a list can contain duplicates of a single element because each duplicate is still unique in its position

#### Accessing an Element [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/qVqzogoyYBG#accessing-an-element)

![Accessing Lists](../images/accessing_lists.svg)

```dart
main() {
  var listOfVegetables = ['potato', 'carrot', 'cucumber'];

  print(listOfVegetables[1]);
}
```

#### Finding the Length of a List

The length of a list is simply the number of elements in that list. To find the length of a list, we can access the `length` property. To access any property we use the dot operator (`.`).

![List Length](../images/length.svg)

```dart
main() {
  var listOfVegetables = ['potato', 'carrot', 'cucumber'];

  print(listOfVegetables.length);
}
```

#### Adding a Single Element

We can add a single element to the end of an already existing list using the `add` method. The only condition is that the element you add must be of the same type as the elements of the list.

![Add elements](../images/add_list.svg)

```dart
main() {
  var listOfVegetables = ['potato', 'carrot', 'cucumber'];

  listOfVegetables.add('cabbage');

  print(listOfVegetables);
}
```

#### Adding Multiple Elements

We can add multiple elements to an already existing list using the `addAll` method. Again, the only condition is that the elements you add must all be of the same type as the elements of the list.

The `addAll` method also has a single parameter which is a list. The list should contain the elements you want to add to an already existing list. The type of the parameter is `List`, where the data type depends on the list you call the method on.

In conclusion, `addAll` basically merges the elements of two lists into one.

![Add all](../images/add_all.svg)

```dart
main() {
  var listOfVegetables = ['potato', 'carrot', 'cucumber', 'cabbage'];

  listOfVegetables.addAll(['broccoli', 'zucchini']); 

  print(listOfVegetables);

  var vegetablesToAdd = ['okra', 'capsicum'];

  listOfVegetables.addAll(vegetablesToAdd);

  print(listOfVegetables);
}
```

#### Adding Elements in an Index

```dart
var vegetables = [];
orders.insert(0,'potato');
```

#### Removing a Single Element

To remove a single element from an already existing list, we can use the `removeAt` method which removes the element at the specified index.

The `removeAt` method has a single parameter which is the index of the element you want to remove. The type of the parameter is `int`.

![removeAt](../images/removeAt.svg)

```dart
main() {
  var listOfVegetables = ['potato', 'carrot', 'cucumber', 'cabbage', 'broccoli', 'zucchini'];

  listOfVegetables.removeAt(0);
  print(listOfVegetables);

  listOfVegetables.removeAt(2);
  print(listOfVegetables);
}
```

```dart
main() {
  var listOfVegetables = ['carrot', 'cucumber', 'zucchini'];

  var carrotIndex = listOfVegetables.indexOf('carrot');
  listOfVegetables.removeAt(carrotIndex);

  print(listOfVegetables);
}
```

#### Removing All Elements

```dart
main() {
  var listOfVegetables = ['cucumber', 'zucchini'];

  listOfVegetables.clear();

  print(listOfVegetables);
}
```

## The `map()` Method 

`map()` maps all the items of a list to an expression or statement. For instance, we could have a list of integers and we want to calculate the square of each integer in the list. `map()` could be used to solve such a problem.

![Map](../images/map.svg)

```dart
main() {
  var listOfVegetables = ['carrot', 'cucumber', 'zucchini'];
  var mappedVegetables = listOfVegetables.map((vegetable) => 'I love $vegetable');
  print(mappedVegetables);
}

// (I love carrot, I love cucumber, I love zucchini)
```

You might have noticed that the output is not a list, as it does not have square brackets. To transform the result of `map()` to a list we can use the `toList()` method.

```dart
main() {
  var listOfVegetables = ['carrot', 'cucumber', 'zucchini'];
  var mappedVegetables = listOfVegetables.map((vegetable) => 'I love $vegetable').toList();
  print(mappedVegetables);
}

// [I love carrot, I love cucumber, I love zucchini]
```

## Sets

In Dart, a **set** is an *unordered* collection of *unique* items. This means that items do not have a specified position in a set, therefore, a set cannot have duplicates of the same item.

## Creating a Set 

##### * Using Literals

Just like lists, sets can also be created using set literals. The syntax is pretty much the same, the only difference is that list literals use square brackets (`[]`) while set literals use curly brackets (`{}`).

![Set](../images/set.svg)

```dart
main() {
  var simpleSet = {1,2,3};

  print(simpleSet);
}
```

sets don’t have duplicates. However, you can still insert duplicates when creating a set, but adding a duplicate item has no effect.

```dart
main() {
  var simpleSet = {1,2,3,3};

  print(simpleSet);
}

// {1, 2, 3}
```

> Dart infers that `simpleSet` has a type `Set`, a `Set` with elements of type `int`.

![with_type](../images/with_type.svg)

```dart
main() {
  var setOfNumbers = <num>{1,1.5,2,2.5};

  // Driver Code
  print(setOfNumbers);
}
```

### Creating an Empty Set Using a Constructor

![set_datatype](../images/set_datatype.svg)



```dart
main() {
  var setOfFruit = <String>{};
  print(setOfFruit);

  Set<String> anotherSetOfFruit = {};
  print(anotherSetOfFruit);
}
```

Just like a List, a Set is a type and is, therefore, an object. This means that sets have particular properties and particular methods that they can perform. Let’s look at some of them below.

#### Adding a Single Item to a Set [#](https://www.educative.io/courses/learn-dart-first-step-to-flutter/RLgOGLVQ7LK#adding-a-single-item-to-a-set)

We can add a single element to an already existing set using the `add` method. The only condition is that the item you add must be of the same type as the other items of the set.

![set_ele](../images/set_ele.svg)

```dart
main() {
  var setOfFruit = <String>{};

  setOfFruit.add('apples');
  setOfFruit.add('bananas');
  setOfFruit.add('oranges');

  print(setOfFruit);
}
```

#### Iterables and Iterator

An **iterable** is one kind of collection in Dart. It’s a collection that you can move through sequentially one element at a time. `List` and `Set` are two common examples of iterable collections. `Queue` is another one, though less common

`EfficientLengthIterable` is itself a subclass of `Iterable`, a class you’ll learn more about later. So by its very definition, you can see that lists are iterables.

Next you’ll see some of the benefits of being an iterable collection.

## Iterating over the elements of a collection

Being able to move sequentially through all the elements of a collection is a prerequisite for using a `for-in` loop.

```
final myList = [2, 4, 6];
for (var number in myList) {
  print(number);
}
```

Since `List` is iterable, you’re able to *iterate* over it.

Not all Dart collections are iterables, though. Most notably, `Map` isn’t. That’s why you can’t directly use a `for-in` loop with the elements of `Map` collection.

If you try to do the following:

```
final myMap = {'a': 1, 'b':2, 'c':3};
for (var element in myMap) {
  print(element);
}
```

You’ll get an error:

```
The type 'Map<String, int>' used in the 'for' loop must implement Iterable.
```

However, maps do have `keys` and `values` properties, which *are* of type `Iterable`. That means you can iterate over either of them. Here’s an example of iterating over the `keys`:

```
final myMap = {'a': 1, 'b':2, 'c':3};
for (var key in myMap.keys) {
  print('key: $key, value: ${myMap[key]}');
}
```

## Other benefits of iterables

An iterable gives you access to lots of other features besides being able to use them with a `for-in` loop. For example, there are quite a few higher order methods available, such as `map`, `where`, `fold`, and `expand`.

Here’s an example of the `where` method, which is useful for filtering out certain elements of a collection:

```
const myList = [1, 2, 3, 4, 5, 6, 7, 8];
final evenNumbers = myList.where((element) => element.isEven);
print(evenNumbers);
```

This prints:

```
(2, 4, 6, 8)
```

There are parentheses surrounding the collection instead of square brackets because `where` returned an object of type `Iterable` rather than `List`. If you actually do want a `List` specifically, you can use the `toList` method that iterables have:

```
print(evenNumbers.toList());
```

This gives the expected square brackets:

```
[2, 4, 6, 8]
```

***Note\****: An iterable represents a potential collection of elements, but it doesn’t do the work of giving you those elements until you ask for it. That can be useful in situations where it might take some heavy work to calculate what the elements are. You don’t want to do that work unless you actually need the elements. However, when you call* `*toList*`*, you are forcing the iterable to iterate through all of the elements in order to create the list.*

# How to create your own iterable

As you learned above, `List`, `Set`, `Queue`, and the `keys` and `values` of `Map` are all iterables, but what if you want to create your own iterable type?

To create an iterable class with all the benefits described above, you have to make an **iterator**. The reason is, an iterable doesn’t actually know how to iterate over its own elements. However, all iterables have an iterator, and it’s the job of the iterator to move sequentially through all the elements of the iterable.

In the example below I’ll walk you through making your own iterable class along with its iterator.

## Describing the problem

In the example that follows, you’ll make a simple iterable whose elements are the runs of text between the points where it’s OK to make a line break. Since this is just a basic demonstration, you’ll just use a space character as a break point.

For example, given the following string:

```
This is a long string that I want to iterate over.
```

The `|` characters show locations that it would be fine to line wrap at:

```
This |is |a |long |string |that |I |want |to |iterate |over.
```

The substrings between the `|` characters represent the elements of your iterable.

## Make a class that extends Iterable

The first thing you should do when making an iterable is extend the `Iterable` class.

```
class TextRuns extends Iterable<String> {
  TextRuns(this.text);
  final String text;  @override
  Iterator<String> get iterator => TextRunIterator(text);
}
```

I could have called it `LineBreaks`, but I decided on `TextRuns` to emphasize that the elements of the collection are strings.

Notice that the only requirement for an iterable is that it has a getter named `iterator` of type `Iterator`. Like I said earlier, iterables don’t know how to iterate over their own elements themselves. That’s the job of the iterator.

When you’re making your own iterable, you have to make your own iterator, too. In the code above, you can see that I called the iterator `TextRunIterator`. Since you haven’t made that yet, you’ll do that next.

## Make a class that implements Iterator

The iterator is where all the work gets done. Basic iterators only have to implement the following simple abstract class:

```
abstract class Iterator<E> {
  E get current;
  bool moveNext();
}
```

The `E` represents a generic type and stands for element. That means that you can have a collection whose elements are of any type.

While there are bidirectional iterables (the `runes` property of `String`, for example), a plain `Iterator` only moves one direction through the collection. Whenever, `moveNext` is called the iterator chooses the next element of the collection. It calls this element `current`.

**Creating the basic class**

Here is a start to `TextRunIterator`:

```
class TextRunIterator implements Iterator<String> {
  TextRunIterator(this.text);
  final String text;}
```

You’ll pass in the text string in the constructor, which comes from the iterable that you already made.

**Adding private fields for the substring indexes**

You haven’t implemented `current` or `moveNext` yet, but first think about how you are going to iterator over the breaks in a string. To get the text runs between the break locations, you’ll use String’s `substring` method, which has a start and end index. So add the following private fields to `TextRunIterator`:

```
int _startIndex = 0;
int _endIndex = 0;
```

Although not a requirement, you’ll start from the beginning of the string, so you can initialize the indexes with `0`.

**Adding the current getter**

Next you’ll implement the `current` getter. Add the following lines to your class:

```
String _currentTextRun;@override
String get current => _currentTextRun;
```

For now you haven’t really done anything. You’ll set `_currentTextRun` in the `moveNext` method in just a minite. If people try to get `current` before they call `moveNext` they’ll get a `null`.

**Adding the moveNext method**

Finally, implement `moveNext` by adding the following code:

```
@override
bool moveNext() {
  _startIndex = _endIndex;  if (_startIndex == text.length) {
    _currentTextRun = null;
    return false;
  }  final next = text.indexOf(breakChar, _startIndex);
  _endIndex = (next != -1) ? next + 1 : text.length;
  _currentTextRun = text.substring(_startIndex, _endIndex);
  return true;
}final breakChar = RegExp(' ');
```

Here’s what’s happening:

- When calculating the substring, `_startIndex` is inclusive while `_endIndex` is exclusive. At the beginning of each attempt to find the next substring, you’ll move the start index to wherever the last substring ended.
- The `moveNext` method returns a Boolean. If `false`, it means that the iterator can’t move to the next element because there are no more. Because of that, you start by checking if `_startIndex` has reached the to the end of the text. Return `false` if it has.
- Then you find the index of the next location of a line break character. The pattern matcher `breakChar` is a regular expression that matches a space character, but you could make it more sophisticated to match additional characters as well.
- String’s `indexOf` returns `-1` if there is no match. In that case you’ll just set `_endIndex` to the end of the string. Otherwise, set `_endIndex` one character past the break character (since you’re including the break character in the preceding text run).
- Finally, set `_currentTextRun` to the substring represented by `_startIndex` and `_endIndex`, and then return `true` to indicate that users can still call `moveNext` again.

That completes your iterator, which also makes your iterable usable.

## Using your iterable

Now you can use your iterable as you would any other iterable. Here it is with a `for-in` loop:

```
const myString = 'This is a long string that I want to iterate over.';final myIterable = TextRuns(myString);
for (var textRun in myIterable) {
  print(textRun);
}
```

Run that and you’ll see the following:

```
This 
is 
a 
long 
string 
that 
I 
want 
to 
iterate 
over.
```

# Full code

Here is the full source code. You can also [play with it in DartPad](https://dartpad.dev/dfd2ba694699af6e7f494b5a2f3d2e7e).

```dart
void main() {
  const myString = 'This is a long string that I want to iterate over.';
  final myIterable = TextRuns(myString);
  for (var textRun in myIterable) {
    print(textRun);
  }
}

class TextRuns extends Iterable<String> {
  TextRuns(this.text);
  final String text;

  @override
  Iterator<String> get iterator => TextRunIterator(text);
}

class TextRunIterator implements Iterator<String> {
  TextRunIterator(this.text);
  final String text;

  String _currentTextRun;
  int _startIndex = 0;
  int _endIndex = 0;

  final breakChar = RegExp(' ');

  @override
  String get current => _currentTextRun;

  @override
  bool moveNext() {
    _startIndex = _endIndex;
    if (_startIndex == text.length) {
      _currentTextRun = null;
      return false;
    }
    final next = text.indexOf(breakChar, _startIndex);
    _endIndex = (next != -1) ? next + 1 : text.length;
    _currentTextRun = text.substring(_startIndex, _endIndex);
    return true;
  }
}
```







