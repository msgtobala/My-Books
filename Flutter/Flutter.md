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

#### In Windows,

* Download [Flutter SDK](https://flutter.dev/docs/get-started/install/windows)
* Extract and unzip the folder and note the location of extraction
* Open environment variables from control panel
* Create new env variable and include the path of Fluter SDK bin folder
* Run `flutter doctor` to conifrm installation
* Install Android studio, configure and download the essentials
* Configure a android virtual device
* Setup android simulator

### Creating a flutter project

```dart
flutter create first_app
```

* Open the app in android studio
* Install Flutter and Dart Plugins
* Create a virtual device and run the virtual device
* Open terminal navigate to the project folder , run `flutter run`

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

> **@required** is exported from the **foundation.dart** file

**To change the keyboard type in TextField**

```dart
TextField(
	controller: _fieldController,
  keyboardType: TextInputType.numberWithOptions(deciaml: true),
);
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

**Theming**

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
   showDatePicker(context: context, initialDate: DateTime.now(), firstDate: DateTime(2019),    lastDate: DateTime.now()),
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

* Portrait mode
* Landscape
* Tablet, Desktop

**Adaptive**

* Android
* IOS

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
  SystemChrome.setPreferredOrientations([
    DeviceOrientation.portraitUp,
    DeviceOrientation.portraitDown,
  ]);
  runApp(MyApp());
}
```

> if this is not working use this inside of MyApp build method

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

* Widget Tree - Controlled by code - frequently rebuilt
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

##### Stateful widgets

* constructor
* initState
* build

##### Statless widgets

* constructor
* initState - runs once not on every rebuilt - used to make http request - no setState in initState
* build - essential method
* didUpdateWidget - called after setState is called / when the widget is updated - used to make http calls
* dispose - called when the widget unmount

###### App Lifecycle

* inactive
* paused
* resumed
* suspending - about to be closed

#### Implementation

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

Every widget can have a key but not stateless widget

* UniqueKey - system generated
* ValueKey - user generated

**Random**

```dart
import 'dart:math';

print(Random().nextInt(4)); will generate a random integer btwn 0 - 4
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
if, size: 60,
then, size: (height / _blockHeight) * SizeConfig.heightMultipler;
```

**width / padding / margin(left and right)**

```dart
if, size: 60,
then, size: (height / _blockWidth) * SizeConfig.widthMultiplier;
```

