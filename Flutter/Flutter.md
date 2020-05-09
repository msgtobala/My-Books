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
	content: Text('Added Item to the Cart!', align: TextAlign.center),
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

**textInputAction** is the customized action button which appears in the right corner of thekeyboard, This is basically a enum with properties like done, next, previous....etc..,

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

> FocusScope is like Navigator which is used to focus the fields programmatically. These focus nodes need to be disposed when the page is left

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

Flutter allows us to validator functions which in turn validates the values entered in the TextField. 

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

This validator function is triggered by `globalKey.currentState.validate()` or by giving `autoValidate: true`. This will call all validator fucntions in the Form

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

#### Inherited Widget

This is used for passing data to the nested widgets. This is done with InheritedWidget.

```dart
class InheritedData extends InheritedWidget {
  final Image asset;
  InheritedData({ this.asset,  Widget child }) : super(child: child);
  
  @override
  bool updateShouldNotify(InheritedWidget oldWiget) => true;
  
  static InheritedData of(BuildContext context) =>
    	context.inheritFromWidgetOfExactType(InheritedData);
}


// any child insided of InheritedData can use,
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

##### Flutter commands

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

#####      Static Analayzer

​      Flutter by default is enabled with static analyser which helps to write cleaner code.Dart has a static analysis tool. Static analysis allows you to find problems before executing a single line of code. It’s a great tool used to find possible bugs and ensure that code conforms to style guidelines. When you use IDE to develop an app, Flutter tool analyzes the project’s Dart code and keeps you in a safe place. For example, when you define FloatingActionButton and forget to implement `onPressed`, then IDE warns that the param `onPressed` is required.







