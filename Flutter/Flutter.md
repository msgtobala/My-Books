# Flutter

## What is Flutter ?

Flutter is a tool to built native cross platform application using one programming language **( DART )**.

Usually,

**iOS** - swift, objective c

**Android** - java, kotlin

But using flutter we can code for both

**Flutter has / includes**

* SDK - Collection of tools to write programs, allows to compile the code in the native devices.
* A Framework / widget library - Allows to use vibrant widgets to use and interact

Flutter = **SDK + Framework**

**Flutter** uses DART. **Dart** is a programming language for Front-end applications( web, mobile ).It is developed by **GOOGLE**. **DART** is object oriented, strongly typed language. 

### Flutter Architecture

* UI based ( Tree based Structure )
* Supports ios and Android with one code base
* Everything is a widget
* No drag and drop
* Hot reload
* Uses <file>.dart

### How Dart is complied to Native apps ?

**Flutter** user dart that will be complied to native apps ( ios and android ) with the help of **Flutter SDK**. It will be compiled.It has hight performance applications.

This gives compiled highly optimised and performance applications

### How Flutter works ?

A widget from flutter is not compiled individually to ios and Android devices. But flutter directly controls the UI and functionality. This is not compiled to native equilance. Flutter directly controls. The widgets and the components are not compiled to native codes.Those are directly controled by **Flutter** out-of-box.

**Flutter** has composition of reactive programming and widgets composition

### Flutter Versions

Flutter is open source project.Keeps on updating and becoming more more stable.

## Installation

#### In MacOS,

* Download [Flutter SDK]()(https://flutter.dev/docs/get-started/install/macos)
* Extract and unzip the folder and note the location of extraction
* Open terminal run, `sudo open ~/.bash_profile`
* Include the line in the file `export PATH="$PATH:[THE_PATH_OF_EXTRACTED_FILE]/bin:$PATH"`
* run `source ~/.bash_profile`
* Check whether **flutter** is installed or not by typing `flutter doctor`
* Install Android studio, configure and download the essentials
* configure a Android virtual device
* Setup android simulator

> For sdk manager error, go to site https://androidsdkmanager.azurewebsites.net/SDKTools

#### In Windows,

* Download [Flutter SDK](https://flutter.dev/docs/get-started/install/windows)

* Extract and unzip the folder and note the location of extraction

* Open environment variables from control panel

* Create new env variable and include the path of Fluter SDK bin folder

* Run `flutter doctor` to conifrm installation

* Install Android studio, configure and download the essentials

* Configure a android virtual device

* Setup android simulator

  If you face any error on licenses the run `flutter doctor --android-licenses`

### Creating a flutter project

```dart
flutter create first_app
```

* Open the app in android studio
* Install Flutter and Dart Plugins
* Create a virtual device and run the virtual device
* Open terminal navigate to the project folder , run `flutter run`

Running the APP in ios devices,

* Need to have apple account
* The apple account should be a developer account
* Select that account in xcode
* Go to vscode and run `open -a Simulator.app`

### Material Design

It is a material UI used by google. Flutter uses material ui. We also can set up own UI.

### Flutter Alternatives

* Ionic - No Compilation to Native Apps. Uses **Web View**
* React Native - Partly compiled to Native Apps / UI is compiled to native apps
* Flutter - Compiled to Native Apps / UI is not compiled. Rendering will be taken care by Flutter itself 

## THE BASICS

**Project Name**

* Should not contain caps, - and spaces, special chars

**pubspec.yaml**

* Manages the dependencies like third party packages

**pubspec.lock**

* created automatically based on **pubspec.yaml**

**Flutter Fundementals**

* Dart is strictly typed.
* Statictly Typed
* Dart has **type Inference** 

**Type Inference**

Dart is able predict the datatype based evaluation made 

`double a = 1.1 + 1.2`

* Dart is Object oriented Programming language

*  Classes in Dart

  ```dart
  class Person {
    String name = 'balaji';
    int age = 21;
  }
  
  void main() {
    var p1 = Person();
    var p2 = new Person();
    print(p1.name, p2.age); // balaji, 21
  }
  ```

* While defining a variable use `int age;`

* While Initializing a variable use `var age = 21;` (This is because Dart provides **Type inference**)

* Program always start from void main()

**Flutter Fundemantals**

* Flutter is always about widgets
* Program Starts from void main(). This is a mandatory method
* Widgets are also objects
* Use pascal cases (MyApp) for class names
* Dart uses named arguments and Positional arguments

#### Positional Arguments

```dart
void addNum(num1, num2) {
  print(num1+ num2);
}
addNum(1, 2); // positional arguments
```

> Position should not be interchanged

#### Named Arguments

> Function accepts many arguments, so the arguments are targeted by names

```dart
return MaterialApp(
  title: 'Flutter Demo',
  theme: ThemeData(primarySwatch: Colors.blue),
  home: Scaffold(
    appBar: AppBar(
      title: Text('Flutter'),
    ),
  ),
);
```

**Constructor Functions in DART** (Positional Arguments)

```dart
Class Person {
  var name; // class variable
  var age; //  class variable
  
  Person(String name, String age) { // constructor variable
    this.name = name;
    this.age = age;
  }
}
var p = Person('balaji', 21);
print(p.name);
```

> Dart has feature called **scoping**, as it can differentiate class variables and constructor variables. so we can use same names for class variables and constructor variables

**Constructor Functions in DART** (Named Arguments)

```dart
Class Person {
  var name; // class variable
  var age; //  class variable
  
  Person({String name, String age}) { // constructor variable
    this.name = name;
    this.age = age;
  }
}
var p = Person(name: 'balaji', age: 21);
```

> All **named arguments** are optional. So if you are not passing a value that is need then **App** might break. To Prevent it use,

```dart
Class Person {
  var name; // class variable
  var age; //  class variable
  
  Person({String name = 'bala', String age = 20}) { // constructor variable
    this.name = name;
    this.age = age;
  }
}
var p = Person(name: 'balaji', age: 21);
```



or



```dart
Class Person {
  var name; // class variable
  var age; //  class variable
  
  Person({@required String name, @required String age}) { // constructor variable
    this.name = name;
    this.age = age;
  }
}
var p = Person(name: 'balaji', age: 21);
```

> Include @required for mandatory fields( This is a  **FLUTTER** feature not **DART** feature )

**Shorthand for contsructor function**

```dart
Class Person {
  var name; 
  var age; 
  
  Person({this.name, this.age = 20});
}
var p = Person(name: 'balaji', age: 21);
print(p.age);
```

* All Widgets will have build method and it will be painted on the screen.All stateless and statefull widget will have

  build method and it is called by Flutter

**@override decorator**

* Used to make clear the code
* Since we deviate a widget with our custom code we use `@override`

```dart
Widget build(BuildContext context) {
  return MaterialApp(
    title: 'Flutter Demo',
    theme: ThemeData(primarySwatch: Colors.blue),
    home: Scaffold(
      appBar: AppBar(
        title: Text('Flutter'),
      ),
      body: Text('DEMO'),
    ),
  );
  }
```

**void main() function**

* This is the first code that Flutter executes

```dart
void main() {
  runApp(MyApp());
}
```

**shorthand**

```dart
void main() => runApp(MyApp());
```

> MyApp() function calls the widget object you pass to it and ensures that the widget tree of that widget gets created.

#### Widgets and Types

* **Page setup widgets** - MaterialApp(), Scaffold()
* **Row / Column children** - Flexible(), Expanded()
* **Content Containers** - Stack(), Card()
* **Repeating Elements** - ListView(), GridView(), ListTile()
* **Content Types** - Text(), Image(), Icon()
* **User Input** - TextField(), RaisedButton(), FlatButton(), InkWell()
* **Layout Widgets** 
  * **Visible Widgets** - UI -  Text(), raisedButton()
  * **Invisible Widgets** -  Layout - Row(), column(), ListView()
  * **Both** - Container() 

**Invisible Widgets**

* Row - renders children next to each other
* Column - renders children after each other(beneath each other)

**Enums and Multiple constructors**

In Dart we can we have multiple constructors

```dart
class Person {
  String name;
  String age;
  
  const Person({ this.name, this.age});
  
  Person.veryOld(this.name) {
    age = 60;
  }
  
  Person.empty() : this('', 0); // this refers to default constructor
}

void main() {
  var p1 = Person.veryOld('test');
  print(p1.name); // test
  print(p1.age); // 60
  
  var p2 = Person.empty();
  print(p2.name); // ''
  print(p2.age); // 0
}
```

**Multiple constructor for EdgeInsets**

```dart
class EdgeInsets {
  double left;
  double right;
  double top;
  double bottom;

  // default constructor
  EdgeInsets(
    this.left,
    this.right,
    this.top,
    this.bottom,
  );

  // all constructor
  EdgeInsets.all(double value)
      : left = value,
        right = value,
        top = value,
        bottom = value;

  // only constructor
  EdgeInsets.only({
    this.left = 0.0,
    this.right = 0.0,
    this.top = 0.0,
    this.bottom = 0.0,
  });

  // symmetic constructor
  EdgeInsets.symmetric({
    double horizontal = 0.0,
    double vertical = 0.0,
  })  : left = horizontal,
        right = horizontal,
        top = vertical,
        bottom = vertical;

  // Redirecting constructor
  // this here refers to default constructor
  EdgeInsets.zero() : this(0, 0, 0, 0);
}

void main() {
  // EdgetInsets
  final normal = EdgeInsets(8, 8, 8, 8);
  print('EdgeInsets default constructor');
  print('left:' + normal.left.toString());
  print('top:' + normal.right.toString());
  print('bottom:' + normal.top.toString());
  print('right:' + normal.bottom.toString());

  // EdgeInsets.all
  final all = EdgeInsets.all(8);
  print('\nEdgeInsets.all');
  print('left:' + all.left.toString());
  print('top:' + all.right.toString());
  print('bottom:' + all.top.toString());
  print('right:' + all.bottom.toString());

  // EdgeInsets.only
  final only = EdgeInsets.only(left: 8);
  print('\nEdgeInsets.only');
  print('left:' + only.left.toString());
  print('top:' + only.right.toString());
  print('bottom:' + only.top.toString());
  print('right:' + only.bottom.toString());

  // EdgeInsets.symmetric
  final symmetric = EdgeInsets.symmetric(horizontal: 8);
  print('\nEdgeInsets.symmetric');
  print('left:' + symmetric.left.toString());
  print('top:' + symmetric.right.toString());
  print('bottom:' + symmetric.top.toString());
  print('right:' + symmetric.bottom.toString());

  // Redirecting constructor
  final empty = EdgeInsets.zero();
  print('\nEdgeInsets.empty');
  print('left:' + empty.left.toString());
  print('top:' + empty.right.toString());
  print('bottom:' + empty.top.toString());
  print('right:' + empty.bottom.toString());
}
```

```dart
class Customer {
  String name;
  int age;
  String location;

  // constructor
  Customer(String name, int age, String location) {
    this.name = name;
    this.age = age;
    this.location = location;
  }
}
```

Now you can create new object using a constructor.

```dart
var customer = Customer("bezkoder", 26, "US");
```

**Shortest form**

```dart
class Customer {
  String name;
  int age;
  String location;

  Customer(this.name, this.age, this.location);
}
```

**Multiple constructors**

```dart
class Customer {
  // ...

  Customer(String name, int age, String location) {
    this.name = name;
    this.age = age;
    this.location = location;
  }

  // Named constructor - for multiple constructors
  Customer.withoutLocation(this.name, this.age) {
    this.name = name;
    this.age = age;
  }

  Customer.empty() {
    name = "";
    age = 0;
    location = "";
  }

  @override
  String toString() {
    return "Customer [name=${this.name},age=${this.age},location=${this.location}]";
  }
}
```

**Short form**

You can write it more simply with Syntactic sugar:

```dart
Customer(this.name, this.age, this.location);

Customer.withoutLocation(this.name, this.age);

Customer.empty() {
  name = "";
  age = 0;
  location = "";
}
```

Now we can create new `Customer` object by these methods.

```dart
var customer = Customer("bezkoder", 26, "US");
print(customer);
// Customer [name=bezkoder,age=26,location=US]

var customer1 = Customer.withoutLocation("zkoder", 26);
print(customer1);
// Customer [name=zkoder,age=26,location=null]

var customer2 = Customer.empty();
print(customer2);
// Customer [name=,age=0,location=]
```

## Redirecting Constructor

We can redirect a constructor to another constructor in the same class by using a colon (:). Remember that body of Redirecting Constructor is empty.

For example, I will rewrite `Customer.empty()` & `Customer.withoutLocation()` above.

```dart
class Customer {
  String name;
  int age;
  String location;

  Customer(this.name, this.age, this.location);

  // Redirecting constructors
  Customer.empty() : this("", 0, "");
  Customer.withoutLocation(String name, int age) : this(name, age, "");
```

Let’s run and check again:

```dart
var customer1 = Customer.empty();
print(customer1);
// Customer [name=,age=0,location=]

var customer2 = Customer.withoutLocation("zkoder", 26);
print(customer2);
// Customer [name=zkoder,age=26,location=]
```

## Factory Constructor in Dart/Flutter

We can use the `factory` keyword for a constructor that return an object instead of creating a new instance.

```dart

class Customer {
  String name;
  int age;
  String location;

  Customer(this.name, this.age, this.location);
  static final Customer origin = Customer("", 0, "");

  // factory constructor
  factory Customer.create() {
    return origin;
  }

//   @override
//   String toString() { ... }
}

void main() {
  var customer = Customer.create();
  print(customer);
  // Customer [name=,age=0,location=]
}
```

### Dart Constructor using Square brackets: Positional optional parameters

```dart
class Customer {
  String name;
  int age;
  String location;

  // Positional optional parameters
  Customer(this.name, [this.age, this.location]);

  @override
  String toString() {
    return "Customer [name=${this.name},age=${this.age},location=${this.location}]";
  }
}
```

Let’s make some test by calling constructor without the optional parameters:

```dart
var customer = Customer("bezkoder", 26, "US");
print(customer);
// Customer [name=bezkoder,age=26,location=US]

var customer1 = Customer("bezkoder", 26);
print(customer1);
// Customer [name=bezkoder,age=26,location=null]

var customer2 = Customer("zkoder");
print(customer2);
// Customer [name=zkoder,age=null,location=null]
```

### Dart Constructor using Curly braces: Named optional parameters

```dart
class Customer {
  String name;
  int age;
  String location;

  // Named optional parameters
  Customer(this.name, {this.age, this.location});

  @override
  String toString() {
    return "Customer [name=${this.name},age=${this.age},location=${this.location}]";
  }
}
```

When calling the constructor, we have to use parameter name to assign a value which separated with colan `paramName: value`.

```dart
var customer = Customer("bezkoder", location: "US", age: 26);
print(customer);
// Customer [name=bezkoder,age=26,location=US]

var customer1 = Customer("bezkoder", age: 26);
print(customer1);
// Customer [name=bezkoder,age=26,location=null]

var customer2 = Customer("zkoder");
print(customer2);
// Customer [name=zkoder,age=null,location=null]
```

## Dart/Flutter Constructor default value

For the constructors with either Named or Positional parameters, we can use `=` to define default values.

The default values must be compile-time constants. If we don’t provide value, the default value is null.

### Positional optional parameters

```dart
class Customer {
  String name;
  int age;
  String location;

  Customer(this.name, [this.age, this.location = "US"]);

  @override
  String toString() {
    return "Customer [name=${this.name},age=${this.age},location=${this.location}]";
  }
}
```

Now create some `Customer` objects, you can see that default value for `age` is `null` and for `location` is `"US"`.

```dart
var customer = Customer("bezkoder", 26, "US");
print(customer);
// Customer [name=bezkoder,age=26,location=US]

var customer1 = Customer("bezkoder", 26);
print(customer1);
// Customer [name=bezkoder,age=26,location=US]

var customer2 = Customer("zkoder");
print(customer2);
// Customer [name=zkoder,age=null,location=US]
```

### Named optional parameters

```dart
class Customer {
  String name;
  int age;
  String location;

  Customer(this.name, {this.age, this.location = "US"});

  @override
  String toString() {
    return "Customer [name=${this.name},age=${this.age},location=${this.location}]";
  }
}
```

Let’s run to check default values for `age` & `location`.

```dart
var customer = Customer("bezkoder", age: 26, location: "US");
print(customer);
// Customer [name=bezkoder,age=26,location=US]

var customer1 = Customer("bezkoder", age: 26);
print(customer1);
// Customer [name=bezkoder,age=26,location=US]

var customer2 = Customer("zkoder");
print(customer2);
// Customer [name=zkoder,age=null,location=US]
```

## Constant constructor

If we want all intances of our class will never change, we can define a const constructor in which all fields are `final`.

```dart
class ImmutableCustomer {
  final String name;
  final int age;
  final String location;

  // Constant constructor
  const ImmutableCustomer(this.name, this.age, this.location);
}
```

Now we can put the `const` keyword before the constructor name:

```dart
var immutableCustomer = const ImmutableCustomer("zkoder", 26, "US");
// immutableCustomer.name = ... // compile error
```

**Functions**

In Dart with my understanding, method parameter can be given in two type.

- Required parameter
- Optional parameter (positional, named & default)

**>> Required Parameter**

Required parameter is a well know old style parameter which we all familiar with it

***example\****:*

```dart
findVolume(int length, int breath, int height) {
 print('length = $length, breath = $breath, height = $height');
}

findVolume(10,20,30);
```

***output:\***

```dart
length = 10, breath = 20, height = 30
```

**>> Optional Positional Parameter**

parameter will be disclosed with square bracket **[ ]** & square bracketed parameter are optional.

***example:\***

```dart
findVolume(int length, int breath, [int height]) {
 print('length = $length, breath = $breath, height = $height');
}

findVolume(10,20,30);//valid
findVolume(10,20);//also valid
```

***output:\***

```dart
length = 10, breath = 20, height = 30
length = 10, breath = 20, height = null // no value passed so height is null
```

***>> Optional Named Parameter\***

- parameter will be disclosed with curly bracket { }
- curly bracketed parameter are optional.
- have to use parameter name to assign a value which separated with colan **:**
- in curly bracketed parameter order does not matter
- these type parameter help us to avoid confusion while passing value for a function which has many parameter.

***example:\***

```dart
findVolume(int length, int breath, {int height}) {
 print('length = $length, breath = $breath, height = $height');
}

findVolume(10,20,height:30);//valid & we can see the parameter name is mentioned here.
findVolume(10,20);//also valid
```

***output:\***

```dart
length = 10, breath = 20, height = 30
length = 10, breath = 20, height = null
```

***>> Optional Default Parameter\***

- same like optional named parameter in addition we can assign default value for this parameter.
- which means no value is passed this default value will be taken.

***example:\***

```dart
findVolume(int length, int breath, {int height=10}) {
 print('length = $length, breath = $breath, height = $height');
} 

findVolume(10,20,height:30);//valid
findVolume(10,20);//valid 
```

***output:\***

```dart
length = 10, breath = 20, height = 30
length = 10, breath = 20, height = 10 // default value 10 is taken
```

> **@required** is exported from the **foundation.dart** file

**final** - Runtime constant

**const** - compile time constant

All the types in **Dart** are treated as objects.Hence, Dart will not store the values in the variables.It only stores the address.

**String Interpolation**

```dart
var a = 10;
print('$a');
var b = {
  c: '10'
}
print('${b.c}'); // needs braces
```

**Date Formatting using `intl`**

```dart
DateFormat().format(date); // returns string
// or
DateFormat('<Format-pattern>').format(date);
// or some pre-configured pattern
DateFormat.yMMMd().format(date); // May 20, 2019
```

| S.No | Format                      | Sign       |
| ---- | --------------------------- | ---------- |
| 1    | ABBR_WEEKDAY                | E          |
| 2    | WEEKDAY                     | EEEE       |
| 3    | ABBR_STANDALONE_MONTH       | LLL        |
| 4    | STANDALONE_MONTH            | LLLL       |
| 5    | NUM_MONTH                   | M          |
| 6    | NUM_MONTH_DAY               | Md         |
| 7    | NUM_MONTH_WEEKDAY_DAY       | MEd        |
| 8    | ABBR_MONTH                  | MMM        |
| 9    | ABBR_MONTH_DAY              | MMMd       |
| 10   | ABBR_MONTH_WEEKDAY_DAY      | MMMEd      |
| 11   | MONTH                       | MMMM       |
| 12   | MONTH_DAY                   | MMMMd      |
| 13   | MONTH_WEEKDAY_DAY           | MMMMEEEEd  |
| 14   | ABBR_QUARTER                | QQQ        |
| 15   | QUARTER                     | QQQQ       |
| 16   | YEAR                        | y          |
| 17   | YEAR_NUM_MONTH              | yM         |
| 18   | YEAR_NUM_MONTH_DAY          | yMd        |
| 19   | YEAR_NUM_MONTH_WEEKDAY_DAY  | yMEd       |
| 20   | YEAR_ABBR_MONTH             | yMMM       |
| 21   | YEAR_ABBR_MONTH_DAY         | yMMMd      |
| 22   | YEAR_ABBR_MONTH_WEEKDAY_DAY | yMMMEd     |
| 23   | YEAR_MONTH                  | yMMMM      |
| 24   | YEAR_MONTH_DAY              | yMMMMd     |
| 25   | YEAR_MONTH_WEEKDAY_DAY      | yMMMMEEEEd |
| 26   | YEAR_ABBR_QUARTER           | yQQQ       |
| 27   | YEAR_QUARTER                | yQQQQ      |
| 28   | HOUR24                      | H          |
| 29   | HOUR24_MINUTE               | Hm         |
| 30   | HOUR24_MINUTE_SECOND        | Hms        |
| 31   | HOUR                        | j          |
| 32   | HOUR_MINUTE                 | jm         |
| 33   | HOUR_MINUTE_SECOND          | jms        |
| 34   | HOUR_MINUTE_GENERIC_TZ      | jmv        |
| 35   | HOUR_MINUTE_TZ              | jmz        |
| 36   | HOUR_GENERIC_TZ             | jv         |
| 37   | HOUR_TZ                     | jz         |
| 38   | MINUTE                      | m          |
| 39   | MINUTE_SECOND               | ms         |
| 40   | SECOND                      | s          |

**Examples Using the US Locale:**

  **Pattern                                                        Result**

1.  new DateFormat.yMd()                          -> 7/10/1996
2.  new DateFormat("yMd")                        -> 7/10/1996
3.  new DateFormat.yMMMMd("en_US")   -> July 10, 1996
4.  new DateFormat.jm()                             -> 5:08 PM
5.  new DateFormat.yMd().add_jm()           -> 7/10/1996 5:08 PM
6.  new DateFormat.Hm()                           -> 17:08 // force 24 hour time

>SingleChildScrollView. + Column = ListView
>
>ListView must have controllable height from parent

**Using ListView**

ListView must have bounded width

**Types*

* ListView
* ListView.builder()

**To change the keyboard type in TextField**

```dart
TextField(
	controller: _fieldController,
  keyboardType: TextInputType.numberWithOptions(deciaml: true),
);
```

**onEditingCompleted**

This is an event just to tell/inform that the user has completed typing. This is the function which is responsible for closing the keyboard on 'completion' actions like 'Done', 'Go', 'Send'.This function will not close the keyboard on other 'non-completion' actions like 'Next'. 'Previous'.`onEditingCompleted` will always be called before `onSubmited`.This will not pass the value of input which the user is typing

**onSubmitted**

This is an event to perform business logic on the value on which the user typing.The callback conveniently passes the value to you, so you can do your business logic with it.

If you don't like this behaviour, you should modify it. For example, "send" is considered a "completion action" here, thus in an Instant Messaging (chatting) app, each time user sends a short message, the keyboard will be collapsed, that's not good. But if we override the `onEditingComplete` callback to an empty function, it will stop the default behaviour and not hide the keyboard. For example:

```dart
TextField(
  controller: _controller,
  onSubmitted: (text) {
    sendMessage(text);
    _controller.clear();
  },
  onEditingComplete: () {},
  textInputAction: TextInputAction.send,
)
```

**Actions in Appbar**

```dart
appBar: AppBar(
	title: 'App',
  actions: <Widget>[
    IconButton(icon: Icon(Icons.add,), onPressed: (){}),
  ],
),
```

**floatingActionButton**

```dart
Scaffold(
	appBar: AppBar(),
  body: Contanier(),
  floatingActionButton: FloatingActionButton(child: Icon(Icon.add),onPressed: (){},),
  floatingActionButtonLocation: FloatingActionButtonLocation.centerFloat
);
```

**BottomSheet**

```dart
showModalBottomSheet(context: ctx, builder: (bCtx) {
  return Widget();
},);
```

> **context** means metadata about the widget. It holds the information about the widget like where the widget has been mounted.

**HitTestBehavior**

To Avoid the default gesture functionality for a Widget.

```dart
GestureDetector(child: Container(), onTap: () {}, behavior: HitTestBehavior.opaque);
```

**Theming**

> primaryColor - It is a just single color
>
> primarySwitch - It is a combination of colors that creates different shades. These different shades will be used by widgets internally.So always better to use `primarySwatch`.

> Secondary color is called as `accentColor`

```dart
theme: ThemeData(
		scaffoldBackgroundColor: AppTheme.appBackgroundColor,
    brightness: Brightness.light,
    textTheme: lightTextTheme,
    primaryColor: Colors.purple,
    accentColor: Color.amber,
    fontFamily: 'OpenSans',
    appBarTheme: AppBarTheme(
      textTheme: ThemeData.light().textTheme.copyWith(
        title: TextStyle(
          fontFamily: 'OpenSans',
          fontSize: 20,
        ),
      ),
    ),
  errorColor: Colors.red,
),
```

```dart
static final TextTheme lightTextTheme = TextTheme(
    title: _titleLight,
    subtitle: _subTitleLight,
    button: _buttonLight,
    display1: _greetingLight,
    display2: _searchLight,
    body1: _selectedTabLight,
    body2: _unSelectedTabLight,
  );
```

**Usage**

```dart
color: Theme.of(context).primaryColor
```

**Images**

```dart
Image.asset('/image', fit: BoxFit.cover), // this needs a wrapper to control
```

**DatePicker**

```dart
FlatButton(child: Text('Choose Date'), onPressed: (){
   showDatePicker(context: context, initialDate: DateTime.now(), firstDate: DateTime(2019),    lastDate: DateTime.now()),`
},),
```

**Future**

```dart
FlatButton(child: Text('Choose Date'), onPressed: (){
   showDatePicker(context: context, initialDate: DateTime.now(), firstDate: DateTime(2019),    lastDate: DateTime.now()).then((enteredDate) {
     print(enteredDate)
   }),
},),
```

#### Responsive and Adaptive designs

**Responsive**

Running the APP in,

* Portrait mode
* Landscape
* Tablet, Desktop

**Adaptive**

Different look and Feel in,

* Android - material design, android page transitions, android animations, android default fonts
* iOS - Cupertino design, iOS animations, ios page transitions. The main important factor is to run the app with responsive and adaptive design

**Dynamic width and height**

```dart
MediaQuery.of(context).size.width
MediaQuery.of(context).size.height
```

**To make the page fit to be scrollable**

```dart
Container(
  height: (mediaQuery.size.height -
           appBar.preferredSize.height -
           mediaQuery.padding.top) *
  0.3,
  child: Chart(_recentTransactions),
),
```

**To get the information about the available space -> use LayoutBuilder()**

```dart
return LayoutBuilder(builder: (ctx, constraints) {
      return Widget()
    },);
```

**To Prevent the phone from landscape mode**

```dart
import 'package:flutter/services.dart';

void main() {
  WidgetsFlutterBinding.ensureInitialized();
  SystemChrome.setPreferredOrientations([
    DeviceOrientation.portraitUp,
    DeviceOrientation.portraitDown,
  ]);
  runApp(MyApp());
}
```

> if this is not working use this inside of MyApp build method
>
> Import `SystemChrome` from 'package:flutter/services.dart'

#### Adaptive Design

> Some **widgets already have platform based designs**

```dart
// android toggle switch
Switch(
	onChanged: (){},
  value: true
); 
// adaptive or platform based switch
Switch.adaptive(
	onChanged: (){},
  value: true
)
```

**To know the space occupied by keyboard**

```dart
Padding(padding: EdgeInsets.only(left: 10, right: 10, top: 10, bottom: 10 + MediaQuery.of(context).viewInsets.bottom));
```

**To detect the platform that we are running**

```dart
import 'dart:io';

Platform.isAndroid ? Widget1() : Container();
Platform.isIOS ? Widget2() : Container();
```

**Using cupertino widgets**

```dart
Scaffold() // android
CupertinoPageScaffold(); // ios
```

> import **package:flutter/cupertino.dart** for using **cupertino** widgets

**cupertinoAppBar**

```dart
CupertinoNavigationBar(
  middle: Text('Personal Expenses'), // as title in material app bar
  trailing: Row( // as actions in material app bar
    mainAxisSize: MainAxisSize.min, // since row will take inf width, it is to give the width 
    children: <Widget>[             // as it needs
      GestureDetector(              // since we dont have IconButton we need to create it
        child: Icon(CupertinoIcons.add),
        onTap: () => _initiateAddNewTransaction(context),
      )
    ],
  ),
);
```

**mainAxisSize**

This is used because **Row/Column** by default will have infinite width / height. To restrict as much the children needs use `mainAxisSize: MainAxisSize.min` by default it will be `mainAxisSize: MainAxisSize.max`

```dart
mainAxisSize: MainAxisSize.min, 
```

**To overcome the reserved spaces for Notch, default bottom navigation control**

```dart
SafeArea(child: Widget(),);
```

**To acheive IOS routing and to use theme for IOS**

Since to achieve routing behavior of IOS and to have theme data use **CupertinoApp and CupertinoThemeData**

```dart
CupertinoApp(
  title: 'Personal Expenses',
  debugShowCheckedModeBanner: false,
  theme: CupertinoThemeData(
    primaryColor: Colors.purple,
  ),
  home: MyHomePage(),
)
```

But the downside is that we cannot acheive all the theme features.So use `Theme.of(context)`.

#### Performance and Flutter core basics

**Flutter** gives 60fps application which means it updates the screen with 60 times per second. On first paint it will venture through all the widgets and get all information like **position, data, text, context, theme** etc., On later paints, if nothing changes it will use the old information stored. So it will be fast.

**What build method is?**

##### Types of trees

* Widget Tree - Controlled by code - frequently rebuilt-It is bascially a configuration of widgets
* Element Tree - controlled by flutter - internaly depends on **widget tree** - not frequently rebuilt
* Render Tree - controlled by flutter -  internaly depends on **widget tree** - final output - not frequently rebuilt

**Widget Tree**

It is only the configuration of the widgtes.It will be re-rendered frequently .It is controlled by the code.It is a bunch of configuration

**Element Tree**

It is internally handled by flutter. It depends on widget tree and it is not freq rebuilt. Flutter always create **element** when it encouters the widget for the first time. **Element** is an object managed in memory which has the reference to widget.For stateful widgets **Element** creates an object for reference and a state object(**independent object**). It also has a reference on the **rendered box( the rendered object on the screen )**. Each **Element** has reference to **widget tree** and **rendered tree**. The rendered box / the render Object which are rendred in the screen can be seen on dart devtools

When **setState** called it will call re-rendering. Whenever the rebuild is happening, it will create a new widget tree with new instances of **Widget classes**.

> Widget and widget trees are immutable. only setState can do it. But this will create new widget and new instance as mentioned below

Also, whenever there is change in `of(context)` changes there is re-rendering will happen.

**Things that cause re-rendering**

* setState()
* of(context) - `MediaQuery.of(context)` and `Theme.of(context) and Navigator.of(context)`

**How re-builds and repaints are happening**

**Build of parent** causes **build of children** also happens.

**Improving Performance**

* const constructors
* const widgets

**Usage**

* All stateless widgets are **immutable**, hence we can use const constructor
* Use **const** for static widgets / classes
* Uses **const** for paddings, margins

**Lifecycles in Flutter**

##### Stateless widgets

* constructor
* build

##### Stateful widgets

* constructor
* initState - runs once not on every build - used to make http request - no setState in initState(super.initState first and logic follows next)
* build - essential method
* didUpdateWidget - called after setState is called / when the widget is updated - used to make http calls(used for comparing widgets)
* dispose - called when the widget unmounts- used to clear listeners and cleaning the memory

###### App Lifecycle

* inactive - no user input(switching will go to inactive first)
* paused - minimised
* resumed - when the app is visible again
* suspending - the app is about to be closed

#### Implementation

* Need to add mixin with the class  `with WidgetsBindingObserver`
* Need to add `didChangeAppLifecyleState(AppLifecyleState)`
* Need to register observer for listening the App cycle changes in initState
* Need to remove obsever in dispose() to clean

```dart
class _NewTransactionState extends State<NewTransaction>
    with WidgetsBindingObserver {
  @override
  void initState() {
    WidgetsBinding.instance.addObserver(this);
    super.initState();
  }

  @override
  void didChangeAppLifecycleState(AppLifecycleState state) {
    print(state);
  }

  @override
  void dispose() {
    WidgetsBinding.instance.removeObserver(this);
    super.dispose();
  }
  
  ....code
}
```

#### context

**context** - meta information about the widget and the location of the widget. It gives communication channel between other widgets

#### Inherited widgets

**MediaQuery, Theme** uses inherited widget. InheritedWidget will create a tunnel for communication and interaction with passing the data around / exchanging the data.

#### key in flutter

Keys are .Every widget can have a key but not stateless widget

* UniqueKey - used when there is no unique data be provided for the key
* ValueKey - used when there is unique data be provided for the key
* ObjectKey - 
* PageStorageKey - Used to preserve the scroll location
* GlobalKey
  * Used when state/information of a widget needs to be shared to other widgets in any parts of the tree

**Random**

```dart
import 'dart:math';

print(Random().nextInt(4)); will generate a random integer btwn 0 - 4
```

### Routing

**GridView**

```dart
GridView(
	children: [],
  gridDelegate: SliverGridDelegateWithMaxCrossAxisExtent(
  	maxCrossAxisExtent: 200, // width
    childAspectRatio: 3/2, 
    crossAxisSpacing: 20,
    mainAxisSpacing: 20,
  ),
);
```



**Route**

```dart
Navigator.of(context).push(MaterialPageRoute(builder:(context){	 
  return page();
});
```

When the page is pushed back button will be automatically provided

**Named Routes**

```dart
 routes: {
   '/catagories': context => comp(),
   '/test':  context => anotherComp()
 }
```

**Passing Data in route**

```dart
Navigator.of(context).pushNamed('/catagories', arguments: {
  'id': 'test',
  'title': 'testing'
});
```

**Extracting data from route**

Inside on the build method, use

```dart
final routeArgs = ModalRoute.of(context).settings.arguments as Map<String, String>;
```

onGenerateRoute, onUnknownRoute are fallback mechanism for unknown routes.Dont use onUnknown Route with onGenerateRoute. Since onGenerateRoute has high priority.

**onGenerateRoute**

* Use along with named routes.

* ```dart
  onGenerateRoute: (settings) {
    return MaterialPageRoute(builder: (ctx) => Screen1(),);
  }
  ```

* ```dart
  onGenerateRoute: (settings) {
    if(settings.name == '/screen1'){
      return MaterialPageRoute(builder: (ctx) => Screen1(),);
    } else if(settings.name == '/screen2'){
      return MaterialPageRoute(builder: (ctx) => Screen2(),);
    } else {
      return MaterialPageRoute(builder: (ctx) => Screen(),);
    }
  }
  ```

**onUnknownRoute**

This is for showing 404 fallback page

```dart
onUnknownRoute: (settings) {
  return MaterialPageRoute(builder: (ctx) => 404(),);
}
```

This is last fallback after the routing table and **onGenrateRoute**

**push**

```dart
Navigator.push(context, MaterialPageRoute(builder(context) => Page()));
```

**pop**

```dart
Navigator.pop(context);
```

**communicating between routes**

```dart
onPressed: () async {
  var navigationResult = await Navigator.push(context, MaterialPageRoute(builder: (context) => Page());
  if(navigationResult == true) {
    print('yes');
  }
}

Navigator.pop(context, true)
```

**Prevent the Page of the APP to pop**

> Wrap the Scaffold of the page where the `pop` needs to prevented with `WillPopScope`

```dart
WillPopScope(
  onWillPop: () => Future.value(false),
  child: Scaffold(
    body: Center(
      child: Text('Businer'),
    ),
  ),
),
```

or

```dart
WillPopScope(onWillpop: () aysnc {
  	return false;
});
```



#### Responsive Layout in Flutter

creating normal constructor

```dart
class Images {
  Image._();
  static const image = '/imagePath';
}
```

> Always **export image, strings** in seperate files. And always try to use **themes** file

**To get the orientation of the device**

```dart
print(MediaQuery.of(context).orientation);
// To check whether we are in landscape mode
final isLandscape = mediaQuery.of(context).orientation == Orientation.landscape;
```

> We can use **if** inside the dart in List

```dart
child: Row(children: Children<Widget>[
  if(isLandscape) return Row();
]);
```

**Auto adjusting to the soft keyboard**

> use **viewInsets** to dynamically adjust the soft keyboard

```dart
Container(
	child: bottomSheetFoxExample(),
  margin: EdgeInsets.only(
    top: 10, left: 10, right: 10, bottom: MediaQuery.of(context).viewInsets.bottom + 10), 
    // only bottom is dynamic because the keyboard appears on the bottom
);
```

**Rendering the Widgets based on the size**

```dart
MediaQuery.of(context).size.width > 450 ? Widget1() : Widget2;
```

To Prevent **Multiple media queries usage**

```dart
// declare the mediaquery on the build
final mediaQuery = MediaQuery.of(context);
```

**SizeConfig**

```dart
import 'package:flutter/rendering.dart';
import 'package:flutter/widgets.dart';

class SizeConfig {
  static double _screenWidth;
  static double _screenHeight;
  static double _blockWidth = 0;
  static double _blockHeight = 0;

  static double textMultiplier;
  static double imageSizeMultiplier;
  static double heightMultiplier;
  static double widthMultiplier;
  static bool isPortrait = true;
  static bool isMobilePortrait = false;


  void init(BoxConstraints constraints, Orientation orientation) {
    if (orientation == Orientation.portrait) {
      _screenWidth = constraints.maxWidth;
      _screenHeight = constraints.maxHeight;
      isPortrait = true;
      if (_screenWidth < 450) {
        isMobilePortrait = true;
      }
    } else {
      _screenWidth = constraints.maxHeight;
      _screenHeight = constraints.maxWidth;
      isPortrait = false;
      isMobilePortrait = false;
    }

    _blockWidth = _screenWidth / 100; // gives the layout grids(width grids)
    _blockHeight = _screenHeight / 100; // gives the layout grids(height grids)

    textMultiplier = _blockHeight;
    imageSizeMultiplier = _blockWidth;
    heightMultiplier = _blockHeight;
    widthMultiplier = _blockWidth;

    print(_blockWidth);
    print(_blockHeight);
  }
}
```

**Fonts**

```dart
if, font-size: 32;
then, font-size: (fontSize / _blockHeight ) * SizeConfig.textMultiplier;
      font-size: (32 / 8.96) * 8.96;
      font-size: 3.5 * SizeConfig.textMultiplier;
// Note: _blockWidth is width in portrait and height in landscape
```

**Images**

```dart
if size: 30,
then, width: (size / _blockWidth) * SizeConfig.imageSizeMultiplier;
```

**Height / padding / margin (top and bottom)**

```dart
if, height: 60,
then, size: (height / _blockHeight) * SizeConfig.heightMultipler;
```

**width / padding / margin(left and right)**

```dart
if, width: 60,
then, size: (width / _blockWidth) * SizeConfig.widthMultiplier;
```

#### State Management

##### Installation

```dart
provider: ^3.0.0
```

##### Usage

* Create a provider file for data container(ChangeNotifier)

  ```dart
  import 'package:flutter/material.dart';
  
  import '../models/product_model.dart';
  
  class ProductsProvider with ChangeNotifier {
    List<ProductModel> _items = [];
  
    List<ProductModel> get items {
      return [..._items]; 
    }
  
    void addProduct() {
      // _items.add(value);
      notifyListeners();
    }
  }
  ```

  Use **ChangeNotifier** as mixin for the provider class, use **notifyListeners()** for triggering update signal

  *  Use the provider for providing data. 

    > Always use the provider on the parent class of the class where we need to use provider.ChaneNotifier is also found in foundation.dart

  * Enable the provider in the parent component using ChangeNotifierProvider

    ```dart
    class MyApp extends StatelessWidget {
      @override
      Widget build(BuildContext context) {
        return ChangeNotifierProvider(
          create: (ctx) => ProductsProvider(),
          child: MaterialApp(
            title: 'Shop',
            theme: ThemeData(
                primarySwatch: Colors.purple,
                accentColor: Colors.deepOrange,
                fontFamily: 'Lato'),
            home: ProductsOverviewScreen(),
            debugShowCheckedModeBanner: false,
            routes: RoutingTable.getRoutingTable(context),
          ),
        );
      }
    }
    ```

    * Use the Provider to enable the connection in the to be used component

      ```dart
      final productsData = Provider.of<ProductsProvider>(context);
      ```

      

#### Mixins and inheritance

##### Inheritance

```dart
class Mammal {
  void breathe() {
    print('Breathe in and breath out');
  }
}

class Human extends {
  String name;
  int age;
  
  Human(this.name, this.age);
}

void main() {
  final prs = Person('balaji', 22);
  print(prs.name);
  prs.breathe();
}
```

Inheritance(strong connection) means inheriting the properties and method of a parent class from a child class    

##### Mixins

```dart
mixin Agility {
  var speed = 10;
  void sitDown() {
    print('Sitting down....');
  }
}

class Mammal {
  void breathe() {
    print('Breathe in and breath out');
  }
}

class Human extends Mammal with Agility {
  String name;
  int age;
  
  Human(this.name, this.age);
}

void main() {
  final prs = Person('balaji', 22);
  print(prs.name);
  prs.breathe();
  print(prs.speed);
  print(prs.sitDown);
}
```

Mixin means sharing or adding properties / methods. It also means the addition of utility methods

* Able to extend only one inheritance at a time
* Able to mixin any number of mixins

##### Alternative ways of using Provider

```dart
child: ChangeNotifierProvider(
		value: Products(),
    child: Item(),
);
```

Using **ChangeNotifierProvider.value()**, is right way and suggestible way. Because this is the right way of using provider on list and grids.

#### Cleaning data in Provider

   when a page that uses data from the ChangeNotifierProvider is navigated / pushNamed, then the data used by the page is cleaned up automatically by ChangeNotofierProvider to prevent memory leaks.

##### Alternatives of Provider.of(context)

```dart
Consumer<ProductModel>(
  builder: (ctx, product, child) => IconButton(
    icon: Icon(
      product.isFavorite ? Icons.favorite : Icons.favorite_border,
    ),
    onPressed: () {
      product.toggleFavouriteStatus();
    },
    color: Theme.of(context).accentColor,
  ),
)
```

* `Provider.of(context, listen: true)` will enable update whenever the data changes in the component

* `Provider.of(context, listen: false)` will not enable update whenever the data changes in the component.

* listen: true is the default value

* Whenever the data changes the entire subtree gets rebuilt.

  But when only a part of subtree need to be updated, then we `Consumers`

  ```dart
  import 'package:flutter/material.dart';
  
  import 'package:provider/provider.dart';
  
  import 'package:shop_app/routes/routes.dart';
  import 'package:shop_app/providers/product_model.dart';
  
  class ProductItem extends StatelessWidget {
    @override
    Widget build(BuildContext context) {
      final product = Provider.of<ProductModel>(context, listen: false);
      return ClipRRect(
        borderRadius: BorderRadius.circular(10.0),
        child: GridTile(
          child: GestureDetector(
            onTap: () {
              Navigator.of(context)
                  .pushNamed(Routes.product_details, arguments: product.id);
            },
            child: Image.network(
              product.imageUrl,
              fit: BoxFit.cover,
            ),
          ),
          footer: GridTileBar(
            backgroundColor: Colors.black87,
            leading: Consumer<ProductModel>(
              builder: (ctx, product, child) => IconButton(
                icon: Icon(
                  product.isFavorite ? Icons.favorite : Icons.favorite_border,
                ),
                onPressed: () {
                  product.toggleFavouriteStatus();
                },
                color: Theme.of(context).accentColor,
              ),
            ),
            title: Text(
              product.title,
              textAlign: TextAlign.center,
            ),
            trailing: IconButton(
              icon: Icon(Icons.shopping_cart),
              onPressed: () {},
              color: Theme.of(context).accentColor,
            ),
          ),
        ),
      );
    }
  }
  ```

  In the above code the listen is false so the app will not re-render when the data changes, but only the favorite icon button widget will get re-rendered since we are using `Consumer` around it.

* Arguments of `Consumer(ctx, data_provider, child)`, the child Argument is used to include the non-rendering parts of the consumer

  ```dart
  Consumer<ProductModel>(
    builder: (ctx, product, child) => Column(children: <Widget>[
      IconButton(
      icon: Icon(
        product.isFavorite ? Icons.favorite : Icons.favorite_border,
      ),
      onPressed: () {
        product.toggleFavouriteStatus();
      },
      color: Theme.of(context).accentColor,
    ),
      child // this is the child argument, this is declared in the child arguments in Consumer 
    ]),
    child: Text('Will not be re-rendered even in consumer')
  )
  ```

  > ```dart
  > PopupMenuButton(icon: Icon(Icons.more_vert, itemBuilder: (_)[
  >   PopupMenuItem(child: Text('Fav'), value: 0),
  >   PopupMenuItem(child: Text('All'), value: 1)
  > ]),
  > ```
  >
  > This is **menu** created like android **options menu**

#### Working with muliple providers

```dart
return MultiProvider(provider: [
  ChangeNotifierProvider(value: Provider1),
  ChangeNotifierProvider(value: Provider2),
], child: MaterialApp(/*...*/));
```

###### Imports and Exports

If we have two classes or two things exported, but in the destination file if you need only one thing then use **show**

```dart
import 'package:flutter/foundation.dart';

class CartItem {
  final String id;
  final String title;
  final int quantity;
  final double price;

  CartItem({
    @required this.id,
    @required this.title,
    @required this.quantity,
    @required this.price,
  });
}

class CartProvider with ChangeNotifier {
  Map<String, CartItem> _items = {};

  Map<String, CartItem> get item {
    return {..._items};
  }

  int get itemCount {
    return _items.isEmpty ? 0 : _items.length;
  }
}
```

```dart
import './cart.dart' show CartProvider;
```

#### Notifications

##### Snackbar 

```dart
Scaffold.of(context).showSnackbar(SnackBar(
	content: Text('Added Item to the Cart!', textAlign: TextAlign.center),
  duration: Duration(seconds: 2), // snackbar will be show for 2 seconds
  action: SnackBarAction(label: 'UNDO', onPressed: () {
    // logic
  }),
));
```

##### Rapid Addition and showing of SnackBar

```dart
Scaffold.of(context).hideCurrentSnackBar();
```

##### Dialogs and Dismissible

```dart
Dismissible(
      key: ValueKey(id),
      direction: DismissDirection.endToStart,
      confirmDismiss: (direction) {
        return Platform.isIOS
            ? showCupertinoDialog(
                context: context,
                builder: (ctx) => CupertinoAlertDialog(
                  title: Text('Are you sure?'),
                  content:
                      Text('Do you want to remove the item from the cart?'),
                  actions: <Widget>[
                    FlatButton(
                      child: Text('No'),
                      onPressed: () {
                        Navigator.of(ctx).pop(false);
                      },
                    ),
                    FlatButton(
                      child: Text('Yes'),
                      onPressed: () {
                        Navigator.of(ctx).pop(true);
                      },
                    )
                  ],
                ),
              )
            : showDialog(
                context: context,
                builder: (ctx) => AlertDialog(
                  title: Text('Are you sure?'),
                  content:
                      Text('Do you want to remove the item from the cart?'),
                  actions: <Widget>[
                    FlatButton(
                      child: Text('No'),
                      onPressed: () {
                        Navigator.of(context).pop(false);
                      },
                    ),
                    FlatButton(
                      child: Text('Yes'),
                      onPressed: () {
                        Navigator.of(ctx).pop(true);
                      },
                    ),
                  ],
                ),
              );
      },
      onDismissed: (direction) {
        cart.removeItem(productId);
      },
      background: Container(
        color: Theme.of(context).errorColor,
        child: Icon(
          Icons.delete,
          size: 30,
          color: Colors.white,
        ),
        alignment: Alignment.centerRight,
        padding: const EdgeInsets.all(15),
        margin: const EdgeInsets.symmetric(horizontal: 15, vertical: 4),
      ),
      child: // any child
    );
```

> confirmDismiss: // This will need Future, hence Navigator.of(context).pop(true / false);

> In CircleAvatar, for background Image we cannot use, Image.asset or Image.network instead use AssetImage, NetworkImage

For Normal form use TextField with controllers(TextEditingControllers)[_controller.text].For complex forms use Form() widget

#### Inputs and InputFields

```dart
Form(
	child: Column(children: [
    TextFormField(
      decoration: InputDecoration(labelText: 'Title'),
      textInputAction: TextInputAction.next,
    ),
    TextFormField(
      decoration: InputDecoration(labelText: 'Title'),
      textInputAction: TextInputAction.next,
      keyboardType: TextInputType.numberWithOptions() // this for allowing only num
    ),
  ]),
);
```

**textInputAction** is the customized action button which appears in the right corner of the keyboard, This is basically a enum with properties like done, next, previous....etc..,

Events

* onFieldSubmited - Triggered when textInputAction button is clicked

##### Focus in TextFields

This can be done with the help of **FocusNode*

```dart
 final _priceFocusNode = FocusNode();

body: Form(
	child: Column(children: [
    TextFormField(
      decoration: InputDecoration(labelText: 'Title'),
      textInputAction: TextInputAction.next,
      onFieldSubmitted: (value) {
        FocusScope.of(context).requestFocus(_priceFocusNode);
      }
    ),
    TextFormField(
      decoration: InputDecoration(labelText: 'Title'),
      textInputAction: TextInputAction.next,
      keyboardType: TextInputType.numberWithOptions() // this for allowing only num
      focusNode: _priceFocusNode
    ),
  ]),
);
```

> FocusScope is like Navigator which is used to focus the fields programmatically. These focus nodes need to be disposed when the page is left.This may cause memory leaks.So we need to dispose it.
>
> FocusScope.of(context).requestFocus(_focusNode);

For Long inputs like description use maxLines

```dart
TextField(
	decoration: InputDecoration(labelText: 'Descriptions'),
  maxLines: 3,
  keyboardType: TextInputType.multiline,
  focusNode: _descFocusNode,
);
```



##### Adding listener

```dart
@override
  void initState() {
    _imageURLFocusNode.addListener(_updateImageURL);
    super.initState();
  }

  @override
  void dispose() {
    super.dispose();
    _imageURLFocusNode.removeListener(_updateImageURL);
    _priceFocusNode.dispose();
    _descriptionFocusNode.dispose();
    _imageURLFocusNode.dispose();
  }

  void _updateImageURL() {
    if(!_imageURLFocusNode.hasFocus && _imageUrlController.text.isNotEmpty) {
      setState(() {
        _urlValue = _imageUrlController.text;
      });
    }
  }

Widget build(BuildContext context) {
  return Expanded(
    child: TextFormField(
      decoration: const InputDecoration(labelText: 'Image URL'),
      keyboardType: TextInputType.url,
      textInputAction: TextInputAction.done,
      controller: _imageUrlController,
      focusNode: _imageURLFocusNode,
    ),
  );
}
```

##### Submitting forms

```dart
//call a function on save button click or any trigger or last form field onFieldSubmitted event
// to save the form we need a global key
final _form = GlobalKey<FormState>();
void _submitForm() {
  _form.currentState.save();
}

Widget build(BuildContext context) {
  return Form(
  	key: _form,
    ...//
  );
}
```

> _form.currentState.save() is needed to invoke onSaved method on each TextFields which will save the current value to temporary variable

```dart
import 'package:flutter/material.dart';

import 'package:shop_app/providers/product_model.dart';

class EditProductScreen extends StatefulWidget {
  @override
  _EditProductScreenState createState() => _EditProductScreenState();
}

class _EditProductScreenState extends State<EditProductScreen> {
  final _priceFocusNode = FocusNode();
  final _descriptionFocusNode = FocusNode();
  final _imageURLFocusNode = FocusNode();
  final _imageUrlController = TextEditingController();
  final _form = GlobalKey<FormState>();

  var _editedProduct = ProductModel(
    id: null,
    price: 0.0,
    title: '',
    imageUrl: '',
    description: '',
    isFavorite: false,
  ); // temp var

  String _urlValue = '';

  @override
  void initState() {
    _imageURLFocusNode.addListener(_updateImageURL);
    super.initState();
  }

  @override
  void dispose() {
    super.dispose();
    _imageURLFocusNode.removeListener(_updateImageURL);
    _priceFocusNode.dispose();
    _descriptionFocusNode.dispose();
    _imageURLFocusNode.dispose();
  }

  void _updateImageURL() {
    if (!_imageURLFocusNode.hasFocus && _imageUrlController.text.isNotEmpty) {
      setState(() {
        _urlValue = _imageUrlController.text;
      });
    }
  }

  void _saveForm() {
    _form.currentState.save();
    print(_editedProduct.description); 
    print(_editedProduct.imageUrl);
  }

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: const Text('Edit Product'),
        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.save),
            onPressed: _saveForm,
          ),
        ],
      ),
      body: Padding(
        padding: const EdgeInsets.all(16.0),
        child: Form(
          key: _form,
          child: ListView(
            children: <Widget>[
              TextFormField(
                decoration: InputDecoration(labelText: 'Title'),
                textInputAction: TextInputAction.next,
                onFieldSubmitted: (_) {
                  FocusScope.of(context).requestFocus(_priceFocusNode);
                },
                onSaved: (value) {
                  _editedProduct = ProductModel(
                    title: value,
                    price: _editedProduct.price,
                    imageUrl: _editedProduct.imageUrl,
                    description: _editedProduct.description,
                    id: null,
                   );
                },
              ),
              TextFormField(
                decoration: const InputDecoration(labelText: 'Price'),
                textInputAction: TextInputAction.next,
                keyboardType: TextInputType.numberWithOptions(),
                focusNode: _priceFocusNode,
                onFieldSubmitted: (_) {
                  FocusScope.of(context).requestFocus(_descriptionFocusNode);
                },
                onSaved: (value) {
                  _editedProduct = ProductModel(
                    title: _editedProduct.title,
                    price: double.parse(value),
                    imageUrl: _editedProduct.imageUrl,
                    description: _editedProduct.description,
                    id: null,
                  );
                },
              ),
              TextFormField(
                decoration: const InputDecoration(labelText: 'Description'),
                maxLines: 3,
                keyboardType: TextInputType.multiline,
                onFieldSubmitted: (_) {
                  FocusScope.of(context).requestFocus(_priceFocusNode);
                },
                focusNode: _descriptionFocusNode,
                onSaved: (value) {
                  _editedProduct = ProductModel(
                    title: _editedProduct.title,
                    price: _editedProduct.price,
                    imageUrl: _editedProduct.imageUrl,
                    description: value,
                    id: null,
                  );
                },
              ),
              Row(
                crossAxisAlignment: CrossAxisAlignment.end,
                children: <Widget>[
                  Container(
                    width: 100,
                    height: 100,
                    decoration: BoxDecoration(
                      border: Border.all(
                        width: 1,
                        color: Colors.grey,
                      ),
                    ),
                    margin: const EdgeInsets.only(top: 8, right: 10),
                    child: _urlValue.isEmpty
                        ? const Text('Enter a URL')
                        : Image.network(
                            _urlValue,
                            fit: BoxFit.cover,
                          ),
                  ),
                  Expanded(
                    child: TextFormField(
                      decoration: const InputDecoration(labelText: 'Image URL'),
                      keyboardType: TextInputType.url,
                      textInputAction: TextInputAction.done,
                      controller: _imageUrlController,
                      focusNode: _imageURLFocusNode,
                      onFieldSubmitted: (_) {
                        _saveForm();
                      },
                      onSaved: (value) {
                        _editedProduct = ProductModel(
                          title: _editedProduct.title,
                          price: _editedProduct.price,
                          imageUrl: value,
                          description: _editedProduct.description,
                          id: null,
                        );
                      },
                      // onChanged: (value) {
                      //   setState(() {
                      //     _urlValue = value;
                      //   });
                      // },
                    ),
                  ),
                ],
              ),
            ],
          ),
        ),
      ),
    );
  }
}
```

##### Validators

Flutter allows us to write validator functions which in turn validates the values entered in the TextField. 

```dart
TextFormField(
  decoration: const InputDecoration(labelText: 'Price'),
  textInputAction: TextInputAction.next,
  keyboardType: TextInputType.numberWithOptions(),
  focusNode: _priceFocusNode,
  onFieldSubmitted: (_) {
    FocusScope.of(context).requestFocus(_descriptionFocusNode);
  },
  validator: (value) {
    if(value.isEmpty) {
      return 'Enter valid price';
    }  
    if(double.tryParse(value) == null) {
      return 'Enter Valid Number';
    } 
    if(double.parse(value) <= 0.0) {
      return 'Enter a number greater than zero';
    }
    return null;
  },
  onSaved: (value) {
    _editedProduct = ProductModel(
      title: _editedProduct.title,
      price: double.parse(value),
      imageUrl: _editedProduct.imageUrl,
      description: _editedProduct.description,
      id: null,
    );
  },
);
```

This validator function is triggered by `globalKey.currentState.validate()` or by giving `autoValidate: true`. This will call all validator fucntions in the Form.

This is done by `_form.currentState.validate()`

```dart
void _saveForm() {
    final isValid = _form.currentState.validate();
    if (!isValid) {
      return;
    }
      _form.currentState.save();
    print(_editedProduct.description);
    print(_editedProduct.imageUrl);
  }
```

default initial values can be set to the Inputs

```dart
TextFormField(
 initialValue: 'initialValue ',
  ....
);
```

> Initial values and controllers cannot be used together.

#### Inherited Widget

This is used for passing data to the nested widgets. This is done with InheritedWidget.

```dart
class InheritedData extends InheritedWidget {
  final Image asset;
  InheritedData({ this.asset,  Widget child }) : super(child: child);
  
  @override
  bool updateShouldNotify(InheritedWidget oldWiget) => true;
  
  static InheritedData of(BuildContext context) =>
    	context.dependOnInheritedWidgetOfExactType();
}


// any child inside of InheritedData can use,
class FlipWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    final data = context.inheritFromWidgetOfExactType(InheritedData).asset;
    // the above line can be used in different way with the implementation of static method
    final data = InheritedData.of(context);
    return //..
  }
}
```

**Inherited widgets** are immutable always.

###### Inherited Widgets can even do more.

```dart
// services file
Class Servies {
  ///...
}
```

```dart
// Inherited Widget
class InheritedData extends InheritedWidget {
  final Services service;
  
  @override
  bool updateShouldNotify(InheritedWidget oldWiget) => true;
  
  static InheritedData of(BuildContext context) => 
        context.inheritFromWidgetOfExactType(InheritedData);
}
```

```dart
// descendent children can use like
InheritedData.of(context).service.call();
InheritedData.of(context).service.print();
```

Other Example

```dart
class MyConstants extends InheritedWidget {
  static MyConstants of(BuildContext context) => context. dependOnInheritedWidgetOfExactType<MyConstants>();

  const MyConstants({Widget child, Key key}): super(key: key, child: child);

  final String successMessage = 'Some message';

  @override
  bool updateShouldNotify(MyConstants oldWidget) => true;
}
```

Then inserted at the root of your app:

```dart
void main() {
  runApp(
    MyConstants(
      child: MyApp(),
    ),
  );
}
```

And used as such:

```dart
@override
Widget build(BuilContext context) {
  return Text(MyConstants.of(context).successMessage);
}
```

###### Generate color dynamically

```dart
myColor = UniqueColorGenerator.getColor();
```

##### Types of keys

> Dont use random number for keys

* ValueKey()
* UniqueKey()
* ObejctKey()
* PageStrorageKey()
* GlobalKey()

### Reaching out to web servers

```dart
Future<String> myFuture {
  retur Future.value('This is a Future');
}

// usage
void getFuture() async {
  var res = await myFuture();
  print(res);
}
```

> The can future can built along with asycn also

```dart
Future<String> myFuture async {
  return 'This is a Future';
}
```

**Future delayed**

```dart
Future<String> myFuture async {
  Future.delayed(Duration(seconds: 1));
  retur 'This is a Future';
}
```

we can also use then to resolve

```dart
void getFuture() {
   myFuture().then(res) => print(res);
}
```

**Resturning error using futures**

```dart
Future<String> myFuture {
  retur Future.error('This is a Future');
}
```

**catching errors**

```dart
void getFuture() {
   myFuture().then((res){
     print(res);
   }).on catchError(error){
     print(error);s
   };
}

// other way
void getFuture() {
  myFuture.then((res) {
    print(res);
  }, onError: (error) {
    print(error);
  });
}
```

**Multiple futures**

> For better understanding, downloading files have been mocked

```dart
Future<bool> downloadFile(int id, int duration) async {
  await Future.delayed(Duration(duration: duration));
  print('The download is completed for the $id');
  return true;
}


Future runMultipleDownloads() async {
  var futures = List<Future>();
  for(var i = 0;i < 10;i++) {
    futures.add(download(i, Random(i).nextInt(10)));
  }
  print('Downloads Started');
  await Futute.wait(futures);
  print('All downloads completed');
}
```

Sometimes, some futures might take long time due to some reasons(May be network issues etc.,).In such time if the future is running for longtime we need to cancel the current `Future` and show `Try Again` or do something

```dart
Future<String> myFuture() {
  Future.delayed(Duration(seconds: 5));
  return 'Completed';
}

timeOutFuture() async {
  var futureValue = await myFuture().timeout(Duration(seconds: 2, onTimeout: () {
    print('This is the example for future timeout');
    return 'Default fallback value';
  }));
}
```

Futures

```dart
void main() {
  var myFuture = Future((){
    return 'Hello';
  });
  print('This runs first');
  myFuture.then((res) => print(res));
  print('This also run first before Future');
}

// output
// This runs first
// This also run first before Future
// Hello
```

Futures with then and catch

* **showDialog** returns Future.
* catchError block will be executed when there is an error
* If there are many catchError block the first catchError block that fails with error will be executed 

```dart
void main() {
  var myFuture = Future((){
    return 'Hello';
  });
  print('This runs first');
  myFuture.then((res) => print(res)).catchError((error) => print(error));
  print('This also run first before Future');
}
```

async / await

```dart
Future<void> fetchProducts async {
  try {
    await httpCall;
  } catch(error) {
    print(error);
  }
}
```

**Delaying Future**

```dart
Future.delayed(Durarion.zero);
```



##### Flutter commands

* ```dart
  pub outdated or flutter pub outdated
  ```

  To identify the out-dated packages and dependencies after identifying the outdated packages use `pub upgrade`

* ```dart
  flutter channel
  ```

* ```dart
  flutter channel <channel_name>
  ```

* ```dart
  flutter packages get
  ```

* ```dart
  flutter upgrade
  ```

* ```dart
  flutter analyze
  ```

  Analysis the code and provide static analysis

  > Pub get uses PubGrub algorithm to fetch dependencies.

#####      Static Analayzer

​      Flutter by default is enabled with static analyser which helps to write cleaner code.Dart has a static analysis tool. Static analysis allows you to find problems before executing a single line of code. It’s a great tool used to find possible bugs and ensure that code conforms to style guidelines. When you use IDE to develop an app, Flutter tool analyzes the project’s Dart code and keeps you in a safe place. For example, when you define FloatingActionButton and forget to implement `onPressed`, then IDE warns that the param `onPressed` is required.

###### Inside of initState, we dont need to setState variables for changes, we can directly set the values like `_data = something` .This would automatically changes the UI becuase it renders before the build method.

**Dart 2.8**

We optimized the performance of the pub tool by adding support for parallel fetching of packages when running `pub get`, and by deferring `pub run` precompilation.



If you need to exhange the data between provider file in other word if a data in a provider is needed by other Provider, we need to ChangeNotifierProxyProvider instead of ChangeNotifierProvider

```dart
 ChangeNotifierProxyProvider<dependentProvider, Actual provider>(
   create: (ctx) => actualProvider(),
   update: (ctx, dependentProviderData, previousProviderValues) => actualProvdier(),
 ),
```

But the ChangeNotifierProxyProvider has to be after the dependent Providers

> The previousProviderValues is needed.This is the one to hold back the other data of Actual Provider.These data has to be given to actual provider.So that they will keep the data

**SetTimeout equivalent in flutter**

```dart
import 'dart:aysnc';

Timer authTimer = Timer(Duration(seconds: 3), logout); // syntaxt Timer(Duration, function);
authTimer.cancel(); // cancels the current timer
```

#### Animations

**AnimatedBuilder**

```dart
AnimatedBuilder(
  animation: <>,
  builder(ctx, child) => Container(...),
  child: AnyWidgetThatIsInsdieContainer(...),
);
```

**AnimatedContainer**

> No need of animation and controller

```dart
AnimatedContainer(duration: Duration(milliseconds: 300, curve: Curves.easeIn, child: Widget()));
```

**Custom Transition**

1. Use stateful widget with `SingleTickerProviderStateMixin`

2. Create a animation a controller

3. Create animation for the respective behaviour(FadeTransition etc.,)

4. initialize animation controller and animation in initState

   ```dart
   void initState() {
       _controller = AnimationController(
         vsync: this,
         duration: Duration(
           milliseconds: 300,
         ),
       );
       _opacityAnimation = Tween<double>(
         begin: 0.0,
         end: 1.0,
       ).animate(
         CurvedAnimation(
           parent: _controller,
           curve: Curves.fastOutSlowIn,
         ),
       );
       _slideAnimation = Tween<Offset>(
         begin: Offset(0, -0.5),
         end: Offset(0, 0),
       ).animate(
         CurvedAnimation(
           parent: _controller,
           curve: Curves.easeIn,
         ),
       );
       super.initState();
     }
   ```

5. Create functions to change the controller between **forward and reverse**

   ```dart
   void _switchAuthMode() {
       if (_authMode == AuthMode.Login) {
         setState(() {
           _authMode = AuthMode.Signup;
         });
         _controller.forward();
       } else {
         setState(() {
           _authMode = AuthMode.Login;
         });
         _controller.reverse();
       }
     }
   ```

6. initialize the Animation now in the required places

```dart
AnimatedContainer(
  duration: Duration(milliseconds: 300),
  curve: Curves.easeIn,
  constraints: BoxConstraints(
    minHeight: _authMode == AuthMode.Signup ? 60 : 0,
    maxHeight: _authMode == AuthMode.Signup ? 120 : 0,
  ),
  child: FadeTransition(
    opacity: _opacityAnimation,
    child: SlideTransition(
      position: _slideAnimation,
      child: TextFormField(
        enabled: _authMode == AuthMode.Signup,
        decoration:
        InputDecoration(labelText: 'Confirm Password'),
        obscureText: true,
        validator: _authMode == AuthMode.Signup
        ? (value) {
          if (value != _passwordController.text) {
            return 'Passwords do not match!';
          }
          return null;
        }
        : null,
      ),
    ),
  ),
),
```

**Animating or Lazy loading animation for images**

**FadeInImage**

```dart
FadeInImage(
  fit: BoxFit.cover,
  placeholder: AssetImage('replacementImage.png'),
  image: NetworkImage(
    product.imageUrl,
  ),
),
```

**HeroTransitions**

Wrap the target and destination images or container with `Hero` widget with a unique tag name

```dart
Hero(
  tag: '01',
  child: Image.network(
    loadedProduct.imageUrl,
    fit: BoxFit.cover,
  ),
),
```

**Slivers**(Making Appbar available only on scroll)

1. Use `CustomScrollView` instead `SingleChildScrollView`

2. Dont use `AppBar`

3. ```dart
   Scaffold(
         body: CustomScrollView(
           slivers: <Widget>[
             SliverAppBar(  // The component that appears as Appbar and the Image component
               expandedHeight: 300,
               pinned: true,
               flexibleSpace: FlexibleSpaceBar(
                 title: Text(loadedProduct.title),
                 background: Hero(
                   tag: productId,
                   child: Image.network(
                     loadedProduct.imageUrl,
                     fit: BoxFit.cover,
                   ),
                 ),
               ),
             ),
             SliverList( // rest of the widgets
               delegate: SliverChildListDelegate(
                 [
                   SizedBox(
                     height: 10,
                   ),
                   Text(
                     '\$${loadedProduct.price}',
                     style: TextStyle(
                       color: Colors.grey,
                       fontSize: 20,
                     ),
                   ),
                   SizedBox(
                     height: 10,
                   ),
                   Container(
                     width: double.infinity,
                     padding: const EdgeInsets.symmetric(horizontal: 10),
                     child: Text(
                       '${loadedProduct.description}',
                       textAlign: TextAlign.center,
                       softWrap: true,
                     ),
                   ),
                 ],
               ),
             ),
           ],
         ),
       );
   ```

   **Custom Page Transition**

   install package `animations: ^1.1.1`

   ```dart
   Scaffold(
         appBar: AppBar(
           title: Text(_pages[_activePage]['pageName']),
         ),
         drawer: MainDrawer(),
         body: PageTransitionSwitcher(
               child: _pages[_activePage]['page'],
               duration: const Duration(milliseconds: 300),
               reverse: // dynamic value(true / false),
               transitionBuilder: (Widget child, Animation<double> animation, Animation<double> secondaryAnimation,){
                   retrun SharedAxisTransition(child: child, animation: animation, secondaryAnimation: secondaryAnimation, transitionType: SharedAxisTransitionType.horizontal);
          }),
         bottomNavigationBar: BottomNavigationBar(
           unselectedItemColor: Colors.white,
           selectedItemColor: Theme.of(context).accentColor,
           currentIndex: _activePage,
           onTap: _selectPage,
           items: [
             BottomNavigationBarItem(
               icon: Icon(Icons.category),
               title: Text('Categories'),
             ),
             BottomNavigationBarItem(
               icon: Icon(Icons.favorite),
               title: Text('Favorites'),
             ),
           ],
           backgroundColor: Theme.of(context).primaryColor,
         ),
       )
   ```

   

   **Adding App icons**

   1. Generate the App icon files from [AppIconGenerator](https://appicon.co/)`
   2. Android, flutter_app > android > app > src > res.
   3. replace the mipmap folders with the new generated folders
   4. iOS, flutter_app > iOS > Runner > Assets.xcassets.
   5. replace and Assets.xcassets folder with new generated folder.

   **To create a clean circular app icon in android**

   1. Go to android studio
   2. Open the flutter project
   3. Go to android > app > src > res
   4. Right click the res, select Image Asset
   5. Adjust as per the need
   6. Override the old image
   7. Click next and there you go

   **Debuging in Real device**

   * Android

     1. Enable **Developer Options** in settings
     2. Tap on Build number
     3. Go to Developer options > Enable USB Debugging
     4. Connect the phone with USB
     5. Allow the prompt for Debugging(Always Allow)
     6. Hoolaa, we will be getting the device detected in Android Studio / VS Code

     sudo gem install cocoapods
     pod setup

   * iOS

     1. Should have a Apple id and mac system
     2. Need iphone device
     3. Need xcode installed in the mac system
     4. The ios version and xcode version should be in sync(can be less than 2 versions)
     5. Xcode version should be ahead or equal to iphone ios version
     6. Install [homebrew](brew.sh) (optional / old steps) or
     7. Run the below commands(new steps)
     8. Add apple id to Xcode
     9. open iOS folder in xcode / open Runner.xcworkspace in Xcode
     10. Click on the Runner on the left tab, add Apple ID in `team`
     11. Select the added account
     12. Connect the phone with USB
     13. Allow the prompt with `Trust`
     14. Need to Trust our Development certificate
     15. Go to the iPhone settings > General > Device management > Apple ID > Trust Apple ID > allow the prompt
     16. Create Unique Bundle id, Change the bundle identifier
     17. Run the App in the device using Android Studio / VS Code

**Difference between IgnorePointer and AbsorbPointer**

Consider a blue square  on top red square, both are clickable, where the blue square is smaller and o red square is bigger

By default, without `IgnorePointer`/`AbsorbPointer`, tapping the blue square will send a click event on blue and red gets nothing.

In that situation, wrapping blue square into an `AbsorbPointer` means that when tapping the blue square, neither the blue square nor the red one gets the click event.

If we instead used an `IgnorePointer`, the red square would receive click events when tapping the blue square.























