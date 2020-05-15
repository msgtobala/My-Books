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

Variables are used for storing information which can then be used by the computer program. Let’s look at this concept from a different angle.

![img](https://www.educative.io/api/collection/10370001/6069685319630848/page/4624163710959616/image/5427857654284288)

```dart
main() {
  int myFirstDartVariable = 5;
}
```

![img](https://www.educative.io/api/collection/10370001/6069685319630848/page/5618358982541312/image/4563202891317248)

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

```dart
Dart numbers are further divided into two subtypes:

integers (int)
doubles (double)
Both int and double are subtypes of num.

Let’s look at each type in a bit more detail below.
```

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

![img](https://www.educative.io/api/collection/10370001/6069685319630848/page/5370884871159808/image/6044750744387584)

![img](https://www.educative.io/api/collection/10370001/6069685319630848/page/5370884871159808/image/5497756166651904)

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

## Type Inference and Annotation

Dart is strongly typed. Strongly typed languages take extra precaution and have rules and restrictions to ensure that a variable’s value always matches the variable’s static type.

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

