# REACT JS

> React Js is a JavaScript Library.It is used to build easy and high responsive UI'S.It renders with the help of Virtual DOM (faster than the normal DOM renderers)

 # REACT NATIVE

> React Native is a Framework used to design cross platform mobile applications.It is very efficient when compared to MobileGap(by adobe),Cordova mobile developing platforms asIt uses webView(that converts normal HTML,CSS,JS) into mobile componenets.It is a browser bundeled inside of the mobile application).But React renders this the help of Native API's

 Use Babel Perprocessor, react, reactDOM imports

In Html,

```html
<div id = "app"></div>
```

In Js,

```js
function Person (props) {
    return (
        <div>
           <p>{props.name}</p>
           <p>{props.age}</p>
        <div>
    );
}
 
const app = (
    <person name = "balaji" age = 12/>
    <person name = "venkatraman" age = "21"/>
);
 
ReactDom.render(app,document.getElementById('app'));
```

---

# Brush Up

### Rest / Spread Operator

* **Rest** - Used to distribute the arrays and objects

* **Spread** - Used to accept the variable arguments

 #### Example for Rest

```js
const array = [1, 2, 3];
const newArray = [...array, 4];
 
const obj = {
    name: 'Balaji'
}
 
const newObj = {
    ...obj,
    age: 21
}
```

#### Example for Spread

```js
const test = (...args) => {
    return args.filter(el => el === 1)
}
 
console.log(test(1, 2, 3));   // output: [1] 
```

#### Destructuring

```js
const numbers = [1, 2, 3];
[num1, num2] = numbers;
console.log(num1, num2);     // output: 1 2
[num1, ,num3] = [1, 2, 3];
console.log(num1, num3);     // output: 1 3
{name} = { name: 'balaji', age: 28}
console.log(name);           // output balaji
```

> Note: Non-primitive datatypes (array, obj) are REFERENCE TYPES (does not copy the values). So use Spread Operator. Primitive datatypes copies the values

---

# React

```react
React.createElement('Element',config,'text');       or
React.createElement('Element',config,React.createElement('Another Element', config, 'text'));
```

#### Example

```react
React.createElement('div', { className: 'App'}, 'Hai hello') or
React.createElement('div', {className: 'App'}, React.createElement('h1', {className:'Tag'},'hai hello')});
```

# Starters

* Install [node](https://nodejs.org)
* Install npm
* npm install create-react-app -g
* npm start
* npm install --save prop-types

---

* Package -- **Radium**, <StyleRoot></StyleRoot>,

> Used for PseudoClasses, media queries and animation and transitions

 #### Example

`  export default Radium(App)`

###### Pseudo-classes

```react
const style = {
  ':hover':{
    backgroundColor: 'red'
  }
 }
```

###### media-queries

```react
const style = {
  '@media (min-width:500px)': {
    width: 450px;
   }
}
```

* npm run eject

  > Used Unlock CSS modules

  **In new react eject**,

```react
 web.config.js -->  modules: true,
 localIdentName: '[name]__[local]__[hash:base64:5]' // in line no.  498
```

* Source Map

  > Used for Debugging

* Error Boundary

  > Used To handle errors

   componentDidCatch = ( error, info ) => {}                  ** Comes under ErrorBoundary **

> Triggred when the component is frozen with error

#### Example

```react
 import React, { Component } from 'react';
 
class ErrorBoundary extends Component {
  state = {
    hasError: false,
    errorMessage: ''
  }

  componentDidCatch = (error,info) => {
    this.setState({hasError: true,errorMessage: error});
  }

  render() {
    if(this.state.hasError) {
      return <h1>{this.state.hasError}</h1>
    } else {
      return this.props.children;
    }
  }
}
export default ErrorBoundary;
```

 

> !! Wrap the whole component with ErrorBoundary to display Custom errorMessage, Use ErrorBoundary only in the place where the code might fail

 # Types of React Component

* Statefull - SMART - CONTAINER  - CONTROLLER - DATA

* Stateless - DUMB - PRESENTATION - VIEW    - DISPLAY

* Stateless in statefull component

* HOC    - Enhancer Component - component with render call backs

# Key Notes

> In map method **Key** property should be attached and it should be on the **outer element/div/some outer tag**

Key prop is important always and it used for identifying the differences in elements by React. This is made through [Reconciliation Algorithm](https://reactjs.org/docs/reconciliation.html).

The **Key** prop should be,

* stable 

  > An element should always have the same key, regardless of its position in the array. This
  > means key={index} is a bad choice.

* Permanent

  >An element’s key must not change between renders. This means key={Math.random()}
  >is a bad choice.

* Unique

  	> No two elements should have the same key.

 `throw new Error('Some errorMessage'); // throws an error,this the error made by developer` 

> Always Create **Containers**(statefull), **Components**(stateless), assets ... structure to maintain clean file structure

* statefull component --> this.XY, this.props.XY

*  stateless component --> props.XY

> Maintain State and Handlers in State component alone, always use Stateless component as much as possibleUse statefull components only for Containers with state

 # LifeCycle hooks

 ### Creation Phase

| Phase                                                        | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| constructor(props)                                           | **Instialized on component creation**.Dont reach out to web , No AJAX call. always Use super(props) |
| componentWillmount()  now **static getDerivedStateFromProps(nextProps, prevState)** | **Not used mostly, but there for historic reasons**          |
| render()                                                     | **Prepares JSX rendering code**                              |
| Render child components                                      | **Renders children components**                              |
| componentDidmount()                                          | **Executed after all the components are mounted**. Reach out to the web, AJAX,Dont Update the state, causes **Re-rendering** |

​                          

### Update Phase

###### Triggered by Parent ( Change in props)

| Phase                                                        | Description                                                  |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| componentWillReceiveProps(nextProps) now **static getDerivedStateFromProps(nextProps, prevState)** | **Used for sync in state**. Dont Reach out to web            |
| shouldComponentUpdate(nextProps, nextState)                  | return true or false. Update - true,Not update - false(updated but not reflected in DOM). return true when **nextProps.XY !== this.props.XY && nextState.XY !== nextState.XY** |
| componentWillUpdate(nextProps, nextState)                    | **Used for sync in state**                                   |
| render(), rendering children                                 | **Prepares JSX rendering code**                              |
| getSnapshotBeforeUpdate(nextProps, nextState)                | returns the snapshot                                         |
| componentDidUpdate(prevProps, prevState, snapshot)           | **Executed after all the updated components are updated**. Can Reach out to web. Dont update state, Causes **re-rendering** |

###### Triggred when change in state

| Phase                                        |
| -------------------------------------------- |
| shouldComponentUpdate (nextProps, nextState) |
| componentWillUpdate()                        |
| render(), rendering child components         |
| componentDidUpdate()                         |

### De-mounting Phase

| Phase                  | Description                                                  |
| ---------------------- | ------------------------------------------------------------ |
| componentWillUnmount() | This will be called when the component is un-mounted. You should invalidate any timers you created (using clearInterval() or clearTimeout()),disable event handlers (with removeEventListener()), and perform any other necessary cleanup. |

### Error Phase

| Phase               | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| componentDidCatch() | This will be called once there is some error in the component after the render. It is triggered only when the children throws error. It is not invoked if the error happened within the component itself |



> In **version 16.3**, we should not use componentWillMount(), componentWillUpate(), componentWilReceiveProps(). Instead use 
>
> * **static getDerivedstatefromprops(**) - componentWillUpdate()** in updated Triggered by Parent(Props) - sync
> * **getSnapshotBeforeUpdate()** - get a snap shot of the dom that is about to change due to of update.It is executed before componentDidUpdate() - used for storing scrolling position

### shouldComponentUpdate()

> **shouldComponentUpdate** is an important method with returning false / true

* return this.props.XY !== nextProps.props.XY /

*  return this.state.XY !== nextState.XY

>  It will check only the states / props are different (this is not a strict check it is a shallow check)

 ### Alternatives to shouldComponentUpdate()

An alternative to **shouldComponentUpdate()** is ***PureComponent*** (strict check of shouldComponentUpdate())

> No Need to implement shouldComponentUpdate() everywhere. It will Cause Performance Issues. **USE PureComponent only in Parent / Root !!!**

 ## Virtual DOM

 ###### Types of DOM

*  **Old Virtual DOM** - present JS DOM representation 
*  **Re-Rendered DOM**(Future DOM) - Future DOM (Changes Happen in this DOM at first) 
* **Real DOM** - Rendered DOM

> React updates the real DOM only when there is a differnce in the old virtual DOM and the Re-Rendered DOM

# Restrictions in JSX

> Every component needs a wrapping div.This can be overcomed by returning array like component / AUX

  ### * Return array with key (MUST)

###### Example

```react
return [
  <p key = "1"></p>
  <p key = "2"></p>
  <p key = "3"></p>
  <p key = "4"></p>
 ];
```

  ### * AUX in HOC

#### Example

```react
const aux = (props) => props.children;
export default aux;
```

###Custom HOC / WithClass

> Used to give same structure to components with different classes with props.children

```react
import React from 'react';
const WithClass = (props) => {
  return(
    <div className = {props.classes}>    
      {props.children}                               
    </div>
  );
};
export WithClass;
```

> This is an alternative to AUX for same structure.

###  AUX with withClass

 ```react
import React from 'react';                         
const withClass = (WrappedContent, classname) => {
  return (props)=>(
    <div className = {classname}>
      <WrappedContent {..props}/>
    </div>
  )
 }
 ```

```react
import React, { Component } from 'react';

const withClass = ( wrappedComponent, className) => {
  return class extends Component {
    render() {
      return (
        <div className = {className}>
          <wrappedComponent {...props} />
        </div>
      )
    }
  }
};
export default withClass;
```

In **App.js**,

` export default withClass(App, classes.App);`  

 **Wrap the component with withClass**

#### Example

```react
export default withClass(App, classes.App);  // classes.App = className for the APP component
```



> If update in a state depends on the previous value of same state,then dont use **this.setState** mutablely, because this.setState is a async function that causes undesirable changes. so, use **this.setState** like this below (In Immutable manner)

 #### Example

* With prevState

```react
this.setState((prevState, props) => {
	return { 		XY_Counter_Value_that_depends_on_prev_state:prevState.XY_Counter_Value_of_on_prev_state_counter+ 1;
}
});
```

 

```react
this.setState((prevState, props)=>{
  return {
    counter: prevState.counter + 1
  }
});
```

This is called as **Functional setState.**

```react
this.setState((state, props)=>{
  return {
    key: state.value + 1
  }
});
```



### Sequential setStates

```react
this.setState((state, props) => {
  return {
  	value: state.value + 1
  }
});
this.setState((state, props) => {
  return {
  	value: state.value + 1
  }
});
this.setState((state, props) => {
  return {
  	value: state.value + 1
  }
});
```

>This would work as expected, eventually incrementing value by 3. It works because calling setState
>“queues” the updates in the order they’re called, and when they’re executed, they receive the latest state
>as an argument instead of using a potentially-stale this.state.

*What is pure function?*

A function **without side effects** is called as pure function.Functional setState is the preferred way to call setState because it’s guaranteed to work correctly, everytime. Try to use it whenever you can.

* **Props** are read-only, state are read. 

#### Prop-types

> Use only in Class Component. Used for validating the datatypes in the component.Throws Error for data type mis-matches

 ##### How to Use?

* npm install --save prop-types;
* import PropTypes from 'prop-types';
* className.propTypes = { state_field: PropTypes.type}

#### Example

```react
import PropTypes from 'prop-types';
Person.propTypes = {
  name:PropTypes.string,
  Changed:PropTypes.func,
  deleted:PropTypes.func,
  age:PropTypes.number
}
```

 **prop-types** works only in Class Component and not in functional Components

#### Types of Prop-Types validators

* PropTypes.array
* PropTypes.bool
* PropTypes.number
* PropTypes.func
* PropTypes.object
* PropTypes.string
* PropTypes.node
* PropTypes.element

#### Instance of 

> Will check props is an instance of specific class

PropTypes.instanceOf(<className>);

* To Limit the **prop** to specific values with oneOf:

`PropTypes.oneOf(['person', 1234, true]);`

* To Check **prop** is one of a few types

`PropTypes.oneOfType([ PropTypes.array, PropTypes.object, PropTypes.number ])`

* To Check Array with specific data type

  `PropTypes.array(PropTypes.string);`

* To Check Object with specific data type

  `PropTypes.object(PropTypes.string);`

* To Object has specific schema

  ```react
  PropTypes.shape({
    name: PropTypes.string,
    age: PropTypes.number
  });
  ```

### Required Props

```js
PropTypes.bool.isRequired
PropTypes.oneOf(['person', 'place', 1234]).isRequired
PropTypes.shape({
  name: PropTypes.string,
  age: PropTypes.number
}).isRequired
```

## Custom Validators

> We can create a custom validator for props using propTypes package. The function should take a prop, prop name, prop type and component name and should return a error. It should return error, it should not throw error.

#### Example

Build a prop type to check whether the passed prop is of length 3.

```react
// Custom PropType
function customValidator(props, propName, componentName) {
  if(props[propsName].length !== 3) {
     return new Error(`Invalid prop ${propsName} supplied to ${componentName}. Length is not    			3`);
   }
}

// Custom Function
import PropTypes from 'prop-types';
import CustomValidator from './customValidator';
const CustomComp = ({ myCustomProp }) => {
  <span>{myCustomProp}</span>
}

CustomComp.PropTypes = {
  myCustomProp: customValidator
}

// Passing prop to custom component
import CustomComp from './CustomComp';
class TestComponent extends Component {
  render () {
    return (
    	<CustomComp myCustomProp='abc' />
    )
  }
}
```



## [REACT](https://reactjs.org) CHILDREN

>The text node wrapped in a react component are called as children. It switches between the data-types of object and array.
>
>* When there is only one child (**React Element**), it has the data-type of object
>* When there is multiple children(**React Elements**), it has the data-type of array

We can access this children through React.Children / props.children

**React Provides many utility function for children**,

* `React.Children.map(children, function)`
* `React.Children.forEach(children, function)`
* `React.Children.count(children)`
* `React.Children.only(children)` - returns the single child or it throws error if there are more than one child
* `React.Children.toArray(children)`

### PropTypes for children

```js
propTypes: {
  children: PropTypes.element // If you want it to accept only a single child, use the element 																validator
}
```

```js
propTypes: {
  children: PropTypes.node //If you want your component to accept zero, one, or more children, 														use the .node validator
}
```

* PropTypes.element - accepts only single React Element and it will not accept the string or number
* PropTypes.node - accepts both React Element and Number / String with one or more React.Element

**If you need to allow an element or a string, you can use the node validator (which will accept elements,**
**strings, and more) or be more explicit with a oneOfType validator like this:**

```js
propTypes.oneOfType({
  propTypes.element,
  propTypes.string,
  propTypes.number
});

or 
propTypes: {
  propTypes.node
}
```



### Customizing React Children Before Rendering

In the example above, we simply inserted some text. What if we wanted to do something more ex-
pressive, like creating our own custom component hierarchy?

Imagine that we constructed our own “API” of sorts for expressing a navigation header

```react
function Parent = () => {
  return (
    <NavChild>
    	<Nav>
        <NavItem url='/'>Home</NavItem>
        <NavItem url='/about'>About</NavItem>
        <NavItem url='/contact'>Contact</NavItem>
			</Nav>
    </NavChild>
  )
}
```

```react
function NavChild({ children }) {
  let items = React.Children.toArray(children);
  for(let i = items.length - 1; i >= 1; i--) {x
  	items.splice(i, 0,<span key={i} className='separator'>|</span>);
  }
  return (
  	<div>{items}</div>
  );
}
```

# Shallow and Deep Merge

#### Shallow Merge

```react
state = {
  name: 'test',
  user: {
    age: 1,
    gender: 'male'
  },
  dob: '11/02/1998'
};

this.setState({
  name: 'testing'
}); // this is replace only the name key with new value and leave all other fields untouched
```



#### Deep Merge

```react
state = {
  name: 'test',
  user: {
    age: 1,
    gender: 'male'
  },
  dob: '11/02/1998'
};

this.setState({
  user: {
    age: 21
  }
}); // this will replace entrie user object and replaces with the object, hence gender no more        available
```



## Events

> The events is javascript are called as Synthetic events. Each events has **events object** created. By default react events are pooled which means that the event object are not created each time , react replaces only the values of previous **event object**

>The event object passed to a handler function is only valid right at that moment. The SyntheticEvent
>object is pooled for performance. Instead of creating a new one for every event, React replaces the
>contents of the one single instance. The event objects are nullified by react. There are pooled by react by default.

```react
function onClick(event) {
  console.log(event); // => nullified object.
  console.log(event.type); // => "click"
  const eventType = event.type; // => "click"

  setTimeout(function() {
    console.log(event.type); // => null
    console.log(eventType); // => "click"
  }, 0);

  // Won't work. this.state.clickEvent will only contain null values.
  this.setState({clickEvent: event});

  // You can still export event properties.
  this.setState({eventType: event.type});
}
```

> **Note**
>
> If you want to access the event properties in an asynchronous way, you should call `event.persist()` on the event, which will remove the synthetic event from the pool and allow references to the event to be retained by user code.

#### Example

```react
import React from 'react';
import logo from './logo.svg';
import './App.css';

class App extends React.Component {
  btnClickHandler = (event) => {
    event.persist();
    console.log(event);
    console.log(event.bubbles);
    const eventType = event.type;
    setTimeout(function() {
      console.log(event);
      console.log(event.type);
    }, 0);
    console.log(event);
  }
  render () {
    return (
      <button onClick={(e) => this.btnClickHandler(e)}>Click me</button>
    )
  }
}

export default App;
```

>React is a declarative way not imperative way( Angular, jQuery)

## Types of Inputs

* Controlled Inputs - **binded with state**
* Un-Controlled Inputs - **not binded state**

19) Reference - Ref

  Available only in Containers, only for focus of the input field

  desc: Used to access focus() and media Playback...

  video attach : 099

  ex:

​    <input

​      ref = {(inp)=>{ this.inputElement = inp }}/>

 

​    Now we can access the inputElement in the Class as Reference

 

​    In componentDidMount () {

​      if(this.props.pos === 0){

​        this.inputElement.focus();

​      }

​    }

​    Because, in componenDidMount() all the components have been mounted

 

​    Refer Video attach: 099

 

In new react 16.3, there is React.createRef()

in class/constructor declare a ref variable like

 this.inputElement = React.createRef() // in constructor

inputElelement = React.createRef() // not in constructor

 

connect the ref variable in input like,

ref = {this.inputElemenet}

 

this.inputElement.focus

\-----------------------------------------------------------------------------------------------------------

​                        Burger Builder

 

  Transform Object to Array

  \-------------------------

  Object.keys(OBJ) will return arrays of keys of the object

  example:

   ingredients = {

​     salad: 1,

​     meat: 2,

​     bacon: 1,

​     cheese: 2

   };

 

   const transformedIngredients = Object.keys(ingredients).map(igKey => {

​     return [...Array(ingredients[igKey])].map((_,index)=>{

​       return <BurgerIngredient key = {key + index} type = igKey />

​     })

   }).reduce((arr,el)=>{

​     return arr.concat(el);

   },[]);

​    

   Using Reduce

   \------------

   array1 = [[1,2],[1,2,3],[0]];

 

   const transformedArray = array1.reduce((arr, el)=>{

​     return arr.concat(el)

   },[]);

 

   console.log(transformedArray); // Output: [1, 2, 1, 2, 3, 0]

 

   

 

20) Map, Reduce

 

  the Reduce Method In JavaScript gives you a mini CodePen

  where you can write whatever logic you want.

  It will repeat the logic for each amount in the array and then return a single value.

 

  ex:

  var euros = [29.76, 41.85, 46.5];

  var sum = euros.reduce( function(total, amount){

   return total + amount

  },0);

 

  sum // 118.11

 

  const euros = [29.76, 41.85, 46.5];

  const average = euros.reduce((total, amount, index, array) => {

  total += amount;

  if( index === array.length-1) {

   return total/array.length;

  }else {

   return total;

  }

  });

 

  average // 39.37

 

 

  ****** count the objects ******

 

  const fruitBasket = ['banana', 'cherry',

​           'orange', 'apple', 'cherry', 'orange', 'apple', 'banana',

​           'cherry', 'orange', 'fig' ];

 

  const count = fruitBasket.reduce( (tally, fruit) => {

​     tally[fruit] = (tally[fruit] || 0) + 1 ;

​     return tally;

  } , {});

 

  console.log("/n",count);

 

  output: {'banana': 2, 'cherry': 3, 'orange': 3, 'apple': 2, 'fig': 1}  

 

 

  Refer: https://medium.freecodecamp.org/reduce-f47a7da511a9 

 

For Modal : transition property is attached to the css itself, hide and show the modal based on the

​      transform property with help of showModal state.

 

For Backdrop: Show / Hide the backdrop with showModal state and return backdrop,if true, else return false

 

DesktopOnly / MobileOnly classes are applied only for the components only based on the

media query

 

Set Active classes also with the help of the props.active video: 128

 

when using the same with component with different css styles can bring Problem.Hence resolve the problem with,

 

  \* Passing as props (height, width,..) accordingly as needed for the components

  \* cover the component with a div wrapper and change its height and width....

  \* Use DesktopOnly, MobileOnly classes in media query as needed

 

 

  DesktopOnly --- In media query of Mobile devices (max-width: 499px) -- Only for Desktop

  MobileOnly ---- In media query of Desktop devices (min-width: 500px) - Only for Mobile

 

21) Video attach: 128 + 7

​    Responsive component

 

22) Course Enabled --> Cross domain platform API access

 

23) async func

  ex:

​    loadPost(function() {

 

​    });

  axios,ajax,superagent,fetch api - Asyn methods

 

24) STATUS CODES 200 - ok, 403 - forbidden, 404 - Not found

 

25) READY STATES

​    0 - Request not Instialized

​    1 - Connection Established

​    2 - Requset Received

​    3 - Processing

​    4 - Response

26) forEach loop

  arrayObject.forEach(function(itr){

​    console.log(itr.XY);

  })

27) GET,POST,PUT,DELETE

28)ICNDB - JUNK NORRIS - INTERNER CHUCK NORRIS DATABASE - FAKE DATABASE

29)REST - Representational State Transfer

  API - Application Programe Interface

  AJAX - Async JavaScript and XML

  XHR - XML HttpRequest

 

30) Callback function

  ex:

​    function createPosts(post, callback){

​      posts.push(post);

​      callback();

​    }

​    function getPosts(){

​      console.log(posts);

​    }

​    createPosts({name:'post1'}, getPosts)

 

31) Head Method - Returns Headers

  Option Method - Return Supported HTTP methods

  Patch Method - Updates the partial Resources

 

32) End Points - URL'S with different methods

  ex: [www.ex.com/users/1](http://www.ex.com/users/1) - GET 

​    [www.ex.com/users/delete/1](http://www.ex.com/users/delete/1) - DELETE 

​    [www.ex.com/users/post/1](http://www.ex.com/users/post/1) - PUT 

 

33) Promises - alternative to callback

 

34)Fetch - window object

  

  function getPosts(){

​    return new Promise(function(resolve,reject) {

​    var err = true/false;

​    if(!err){

​      resolve()

​    }else{

​      reject("Something went wrong");

​    }

  })

  }

 

  createPosts().then(getPosts)

​        .catch(function(err){

​          console.log(err);

​        })

  

35) Axios - For Fetching data and sending and stroing data from,into the server

 

  npm install axios --save

\-----------------------------------------------------------------------------------------------------------

 

  import axios from 'axios';

 

  axios.get(url).then((res)=>{

​            console.log(res.data);

​          })

​          .catch((err)=>{

​            console.log(err);

​          })

 

36)axios.get(url) --> fetch the data from url

 

  In get Request dont render the values immediately,check for the loaded values to set in the state

 

37) Take care of componentDidUpdate() because it will cause infinite request.

  so have check before sending request

  video attach:148

 

38) axios.post(url, data) --> Post the data to the url

 

39) axios.delete(url, id/data) --> Delete the particular id/data from the url

 

 

  If the get,post,delete requests fails, then catch block will Executed

  Then setState error as true and display some errorMessage in the screen

 

40) Interceptors --> Used handle error globally usually in index.js

 

41) Interceptors will be in axios package.

  ex:

​    axios.interceptors.request.use(request=>{  *** This is Request error Interceptor ***

​      console.log(request);

​      return request;

​    },error=>{

​      console.log(error);

​      return Promise.reject(error)

​    });

 

​    axios.interceptors.response.use(response=>{ *** This is Response error Interceptor ***

​      console.log(response);

​      return response;

​    },error=>{

​      console.log(error);

​      return Promise.reject(error);

​    })

 

  Use this in index.js for global configuration

 

42) axios.default.XY

  desc: Used to assign defaults globally

  ex:

​    axios.defaults.baseURL = 'url';

​    [axios.defaults.headers.common](http://axios.defaults.headers.common/)['Auth'] = 'AUTH TOK';

​    axios.defaults.headers.post['Content-Type'] = 'application/json';

 

43) defaults will be applied globally and will be applied to all the files and folders.

  Also we can have some of the js files that does not follow the interceptors like baseURL and so on..

 

  Hence We use INSTANCES, the assign/overrides the properties of defaults of the global axios.defaults

  INSTANCES,INTERCEPTORS ARE THE FEATURES OF AXIOS.

  ex:

​    create a new file with name axios.js

 

​    import axios from 'axios';

 

​    const instance = axios.create({

​      baseURL: 'url'

​    })

 

​    [instance.defaults.headers.common](http://instance.defaults.headers.common/)['Auth] = 'AUTH TOK FROM INSTANCE' //may be we can change the defaults

​    .... so on properties

 

​    [// also can use interceptors(request, response interceptors)]

​    export default instance;

 

​    Use the export instance in the file where it does not follow the defaults.

​    import into the file needed

 

  CONTROLS THE DEFAULTS OF PARTICULAR COMPONENT

 

44) Firebase --> Google database with RESTFUL API that allows to send data to the end points

 

 

Use Modal withErrorHandler as a global file and wrap it with the component that uses axios.

It should have componentWillMount method implemented

 

 

45) withErrorHandler

  desc: A HOC component for handling errors that use axios**

  ex:

​    import React, { Component } from 'react';

 

 

​    import Aux from './Aux';

​    import Modal from '../UI/Modal/Modal';

 

​    const withErrorHandler = (WrappedContent, axios) => {

​       return class extends Component {

​       state = {

​        error: null

​       }

​       componentWillMount () {

​         this.reqInterceptor = axios.interceptors.request.use(req=>{

​         return req;

​       },err=> {

​         this.setState({error:null})

​       });

 

​        this.resInterceptor = axios.interceptors.response.use(res=>{

​         return res;

​        },err=>{

​        this.setState({error:err})

​       })

​      }

 

​    componentWillUnmount () {

​      axios.interceptors.request.eject(this.reqInterceptor);

​      axios.interceptors.response.eject(this.resInterceptor);

​    }

 

​    clearModelHandler = () => {

​      this.setState({error: null})

​    }

​    render () {

​      return (

​        <Aux>

​          <Modal

​            showModal = {this.state.error}

​            closed = {this.clearModelHandler}>{this.state.error ? this.state.error.message : null}</Modal>

​          <WrappedContent {...this.props}/>

​        </Aux>

​      );    

​    }

   }

}

 

export default withErrorHandler;

 

Video attach: 165 - 167

 

46) MPA(simply multiple jsx files to re-render) in SPA

  Desc: we use Router Package for implementing i.e. Routing

 

  It does

​    \* PARSING THE URL / PATH

​    \* READING THE CONFIG

​    \* LOAD / RENDER / RE-RENDERING THE JSX

 

47) npm install react-router

  npm-install react-router-dom

 

 

  Now In app.js wrap the export with object BrowserRouter(import from react-router-dom)

  ex:

​    <BrowserRouter>

            <div>

​        <App />

            <div>

​    </BrowserRouter>

 

48) Route

  desc: Used for routing.But basically reloads the page

 

  <Route path = "/" render = {() => { return <h1>This is a test Route</h1>}}

 

  path = This is endpoint

  render = this will be rendered when path matches

 

  <Route path = "/" render = {()=>{return <h1>This is a test Route </h1>}}

 

  exact = matches the exact path.Matches for the exact string in the path

 

49) <a href="/">some link</a> with Route causes reloading of the page

  Hence we use <Link to = {{

​            pathname: "/"

​            search: "?auth-user=true",

​            hash: #home

  }}

 

  This will not re-render the page

 

50) While consoling this.props in componentDidMount() will give some info like history,location,match

 

51) Routing component details is not passed down the component tree and information about the route stays

  within the component

 

  so, Import withRouter from 'react-router-dom';   ** It will give the info of the nearest route **

 

  wrap the export with withRouter;

 

  This will give the info of the router details

 

  (AND)

 

  Pass the router details from Parent component to child component in props

 

The path Links are always absolute path.i.e., the path urls's are always added with the root URL

Ex: localhost:3000/posts,localhost:3000/post,localhost:3000/new-post,[example.com/posts](http://example.com/posts)

 

To change the path to relative path use,

 

path: this.props.match.url + '/posts'; or

   this.props.match.path

 

ex: <Link to = {{

  pathname: this.props.match.url + '/new-post'; // This in turn will create a relative path

}}>New Post</Link>

 

 

52) this.props.match.url

  This will gives the current url(active link)

 

53) NavLink

  desc: It is same as Link but it has some extra props when compared to Link.ex: It has active

  active = decorating the active link

  ex:

   <li><NavLink exact to = {{

​                pathname: "/home",

​                hash: '/#home',

​                search: '?auth-user=true'                   

​              }} activeClassName = "highlight" activeStyle = {{color:'#fa923f'}}>Home</NavLink></li>

​              <li>

 

  activeClassName = "Your-Class-Name"

  activeStyle = "Your Active Class Style"

 

  The NavLink with default active class will not work in the css modules(npm run eject).

  Hence use activeClassName = {classes.active} to include active class style

 

Dynamic routes can be set as <Route path = ":id" component = {FullPost}/>

​              <Link to = {{

​                pathname: "/" + post.id

​              }}

 

This will go into the this.props.history.params.

 

54) <Switch>

  desc: Will be present in react-router-dom

​     import {Switch} from 'react-router-dom';

 

​     It will load only one route at a time.It matches the first path and renders it

 

55) this.props.history   *** Only the componenets loaded through route will have access to this.props.hisory,this.props.tach ***

  desc:

  An alternative to the Link is history which act as a stack of pages for navigation

 

  In case after submiting a form that which become success we have to navigate to another page.

  In that state use we use history

 

  ex:

​    this.props.history.push({pathname: "path"})

 

​    path = any another jsx page

 

   Link,NavLink,Route,this.props.history,<Switch>,this.props.match.url,Redirect

 

 

 

   **** For Loading the different posts on diiferent click - Use both componentDidMount() , componentDidUpdate() ****

  

  

  We have to use componentDidUpdate when the component is mounted through route.This is to change/update

  the component because the route will not umount.

  ex: posts and FullPost

  === watch video attach: 191 ===

 

56) Redirect

  desc: Used to redirect to a particular page from a another page

  ex:

 

​    <Redirect from = "" to = "" />

 

​    Use inside Switch or else from cannot be specified.Redirect has only to props outside of the

​    switch

  push - pushes the new page into the stack and hence we can go back

  replace - replace the old page with new page in the stack and hence we cannot go back

 

57) Conditional redirect --> Use a state to check for redirection

  desc:

​    If redirection is true;Them redirect with <Redirect/>

 

58) Conditional Redirect will not allow us to go back.But this.props.history.push({pathName:''}) will

  allow us to go back.there is another method to prevent back this.props.history.replace({pathName:''})

 

  This will not allow to go back it will prevent go back and replaces the page

 

59) Guards

  desc: This is used to check whether the user is authenticated or not

 

  This can be done with two ways

 

  1) Use state auth: true / false

​    Preventing and redirecting the user if he is not authenticated by

​    this.props.history.push({pathName:'redirectUrl'}) in componentDidMount()

​    ex: if(auth === false){

​        this.props.history.push({

​          pathname: './home'

​        })

​      }

 

  2)By using conditional check as

​    {this.props.auth ? <Route path = "/post" component = {Posts}/> : null};

 

60) Route without "to" is used to handle 404 error pages or unknown pages

  desc:

​    <Route component = {ErrorPage}/>

 

  Dont use this with Redirect

 

  LAZY LOADING / CODE SPLITTING

 

  It is used to load the page at the time of need. There may be some pages where user will use it

  occasionally / do not use it often. Those code are need not to be downloaded and need to increase

  the size of bundle.js

  so, use CODE SPLITTING / LAZY LOADING

 

  Create asynComponent in hoc

\---------------------------------------------------------------------------

  const asynComponent = (importComponent) => {

​    return class extends Component{

​      state = {

​        component: null

​      }

​      componentWillMount () {

​        importComponent()

​            .then(cmp=>{

​              this.setState({component: cmp});

​            })

​      }

​      render () {

​        const C = [this.state.component;](http://this.state.component;/) 

​        return C ? <C {...this.props} /> : null;

​      }

​    }

  }

  export default asynComponent;

 

 

In Lazy Loading using Component dont use regular import instead use,

 

 

import asynComponent from '../../hoc/asynComponent';

 

 

const AsynComp = asynComponent(() =>{

  return import('../../COMPONENT');

});

 

IN ROUTE,

<Route path = "/new-post" component = {AsynComp}/>

\---------------------------------------------------------------------------

 

 

 

61) basename=".my-app"

  desc: Used to change the default url like www/[example.com/my-app](http://example.com/my-app)

  This is the base url always

 

62) Redux -- Used in-replacement of STATE

 

npm install react-redux

npm install redux

 

\-----------------------------------------------------------------------------------------------------------

 

Reducer ---> Store ---> Subscription ---> Dispatching Actions

 

 

Reducer --- This is the one that will Update the central Store

Store --- Universal Central Store

Subscription --- This is the component that will receive the updated states from the Central Store

Dispatching Action --- These are the actions that are dispatched from the components

 

nodejs with redux--

 

const redux = require("redux");

const createStore = redux.createStore;

 

const initialStore = {

  counter: 0

}

 

const rootReducer = (state = initialStore, action.type) => {

  if(action.type === "INC_COUNTER"){

​    return {

​      ....state,

​      counter: state.counter + 1

​    }

  }

 

  else if(action.type === "DEC_COUNTER"){

​    return {

​      ...state,

​      counter: counter + action.value

​    }

  }

  

  return state;

}

 

const store = createStore(rootReducer);

console.log(store.getState());

 

store.subscribe(() => {

  console.log("[Subscription]", store.getState());

})

 

store.dispatch({

  type: "INC_COUNTER"

})

store.dispatch({

  type: "DEC_COUNTER",

  value: "1"

})

 

 

**** CREARE STORE IN INDEX.JS ****

 

import { createStore } from 'redux';

import { Provider } from 'react-redux';

 

const store = createStore(reducer);

 

ReactDom.render(<Provider store = {store}><App /></Provider>)

 

**** CREATE REDUCER JS FILE ****

 

const initialStore = {

  counter: 0,

  ..............

}

 

const reducer = (state = initialStore, action) => {

  switch(action.type){

​    case '':

​     return

​    case '':

​     return

​    default:

​     break;

  }

  return state;

}

 

 

In component for SUBSCRIPTION

import { connect } from 'redux-react';

 

mapStateToProp = state => {

  ctr: state.counter;

}

 

dispatchStateToProps = dispatch => {

  onIncrement: () => {dispatch({type: 'INCREMENT', payload: ''})}

}

 

export default connect(mapStateToProp,dispatchStateToProps)(COMPONENT);

 

 

 

const newObj = Object.assign({}, oldObj); // copies/clones the old obj into new obj Immutably

filter() return a new array

const updatedArray = oldArray.filter((element, index)=>{

  return index !== id

})

 

 

combineReducers

 

It is used to combine the different reducers into one reducer

 

import { Provider, combineReducers } from "redux";

 

const rootReducer = combineReducers({

  ctr: reducer1,

  res: reducer2

})

 

const store = createStore(rootReducer);

 

Provider must be the parent component of BrowserRouter

 

 

**Advanced Redux**

 

It uses Middleware to execute asyn code

 

component --> actions --> Middleware --> reducer ---> central store --> Subscription --> component

 

 

// a example Middleware

 

import { applyMiddleware } from "redux";

 

const logger = store => {

  return next => {

​    return action => {

​      console.log("[Middleware] Dispatching", action);

​      const result = next(action);

​      console.log("[Middleware] next state", store.getState());

​      return result;

​    }

  }

}

 

const store = createStore(rootReducer, Enhancers); Enhancers === applyMiddleware(logger) [Middleware]

const store = createStore(rootReducer, applyMiddleware(logger)); ---- createStore(rootReducer, applyMiddleware(logger,.....))

 

compose -- used to combine Enhancers;

combineReducers -- Used to combine reducers

 

import { compose } from "redux";

 

const combineEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;

const store = redux.createStore(rootReducer, composeEnhancers(applyMiddleware(logger)))

 

---- This is used to use and unlock Redux dev Tools ----

 

Reducers that we created will not accept asyn code like reaching out to the web, setTimeout().so, use

action Creators

 

we can use actionCreators for asyn code and sync codes also

refer video set 265 - 268

 

 

ASYN CODE

 

To Handle async actionCreators we need to use redux-thunk

Thunk is a Middleware.so add in the applyMiddleware

import thunk from "redux-thunk";

 

const store = redux.createStore(rootReducer, composeEnhancers(applyMiddleware(logger, thunk)));

 

export const saveResults = (val) => { <--------------------------|

  return {                           |

​    type: actionCreators.STORE_RESULT,            |

​    ctrValue: val                       |

  }                               |

}                                 |

​                                 | Will execute this after 2 seconds

​                                 | (Async)

export const storeRes = (val) => {                |

  return dispatch => {                     |

​    setTimeout(()=>{                     |

​      dispatch(saveResults(val)) ---------------------------|

​    },2000)

  }

}

 

Refer video 270 for restructuring the actions

 

Manipulate the asyn code results in reducer not in the actionCreators

 

 

How to get the state from Redux in actionCreators ?

 

\1. getState()

 

const oldValue = getState().counter;

 

\2. getState() while in combineReducers (more than one Reducers)

 

const oldValue = getState().ctr.counter;

 

​          BUT USING THIS APPROACH IS NOT BETTER; SEND THE STATE VALUES FROM THE CONTAINER THAT HAS

​                            ACCESS TO THE STORE STATES

 

 

3.const mapDispatchToProps = dispatch => {

  return {

​    onIncrement: dispatch({actionCreators.increment(10, this.props.ctr)})

  }

}

 

 

UTILITY FUNCTIONS - USED TO SIMPLIFY THE REDUCERS,it is optional

 

1) IMMUTABILITY

 

create utility.js in actions in primary position

 

In utility.js,

 

export const updateObj = (oldObj, updatedValues) => {

  return {

​    ...oldObj,

​    ...updatedValues

  }

}

 

Import this utility js file in reducers as default

 

In reducer.js

 

  import { update } from "../utility";

 

  ..........

  ..........

  ..........

  case actionCreators.INCREMENT:

​    return updateObj (state, {counter: counter + 1})

 

 

REACT TRANSITION GROUPS

 

npm install --save react-transition-group

 

Used for adding transition to pages with animation in Routing

 

 

AUTHENTICATION IN REACT

 

WHILE USING FIREBASE,

 

In firebase use authToken to access the protected resources.Change the rules of the protected

resources in the firebase.

 

Get the key while signing in and store it into the firebase and use while accessing the

protected resources.Send the authToken along with the post,get request.

 

AUTH TOKEN WILL BE GET WHILE CORRECT LOG IN FIREBASE AS THE RESPONSE DATA

 

 

access the data form firebase with help of queryParams

 

queryParams = '?auth='+ token + '&orderBy="userId"&eaqualTo="' + userId + '"';

 

 

NOTE: YOU HAVE ENABLE IN FIREBASE TOO BY CHANGING THE RULES

 

"order": {

​     ".read": "auth != null",

​    ".write": "auth != null",

​    ".indexOn": ["userId"]

  }

 

ADD THE FIELD TO BE PASSED IN THE queryParams INDEXON ARRAY

video attach = 320

 

 

Unlock the Redux store in development mode not in production mode.This can be done with environment variable(NODE_ENV)

const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ || compose;

const composeEnhancers = process.env.NODE_ENV === 'development' ? window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__ : null || compose;

 

TESTING

 

Automatic Testing -- Unit testing(split the components and test) isolated test

 

Requirements,

 

\1. Test Runner - executes the test code and provides results / errors -- React js uses JEST (JavaScript Testing Tool)

// Embedded in React

\2. Testing Utilites - React Test Utils is used in react - Used for simulation also use Enzyme(developed By AirBNB)

// Suggested by React Team

 

Mind This:

 

\1. Not need to test Library (Axios,Redux)

\2. Dont Test Complex Connections

\3. Test Conditional outputs(loops and if, switch checks)

\4. Test Isolated Units (Own Components, Own Containers)

 

 

JEST will be installed by default. Enzyme need to be installed.But it needs 2 packages

to work with JEST AND REACT

 

 

JEST HAS TWO METHODS,

\1. describe() -- describes the module to be tested

\2. it() -- allows one unit test

 

Then, create an instance for the testing componenet...

 

\3. configure // import { configure } from "enzyme";

\4. Adapter  // import Adapter from "enzyme-adapter-react-16";

 

configure({adapter: new Adapter()})

 

\4. shallow // import shallow from "enzyme"; shallow renders only the unit component not the children

  or full // used to check and test children too // import { mount } from enzyme

  or static // use import { render } from "enzyme";

\5. expect() // expect() checks for the testing component

\6. find() // finds a particular componenet in the testing component

\7. beforeEach() // runs before all tests

\8. afterEach() // runs after all tests

\9. setProps() // sets props to the mentioned wrapper

 

DEPLOYING THE REACT APP

 

npm run build // This will create build folder in the project folder

 

Deploying into Firebase

 

1) npm run build

2) firebase login

3) firebase init

​    i) select hosting

​    ii) type upload folder as build

​    iii) type yes for spa index.html

​    iv) type no for modifications

 

 

WEBPACK

 

1) It optimizes the code and the workflow

2) It bundles the all js,css,images into optimised pattern

3) It transpilles ts to js

4) It implements loaders into the project

5) It hook various plugins called 'loaders'

 

4 important features of webpack

 

1) It needs a entry point.Here it is app.js and it looks for child component and builds

  component tree

2) And in result create

  a bundle.js(correctly ordered files)

3) It applies loaders for the js and css.It is applied to each single file

  Loaders - file dependent transformations

  ex: css - css Loaders

​    js - Babel Loaders

4) It also plugins.It takes the pre-bundled files that comes as the output of appling

  loaders. ex: Uglify

 

Requirements of webpack in React

 

1) Handle jsx

2) support next generation js

3) supports autoprefixing

4) support images and image imports

5) create optimised code

 

STEPS

 

1) npm init

2) sudo npm install --save-dev webpack webpack-dev-server

3) add start script to package.json ex: "start": 'webpack-dev-server'

4) config webpack by,

   i) create a new file webpack.config.js,

  ii) add the code attached

  iii) resolve files that has no extensions

  iv) config Babel by installing

  v) create .babelrc file in root 

  vi) config css loader by installing

  vii) config autoprefixing by installing it

  viii) install autoprefixer

  ix) install image loaders

​     Image loader will use the image if it is smaller size

​     Image loader will copy the image into the folder and fits image path is the image size is bigger

  x) To support url loader also install fall-back

  xi) enable Lazy Loading

  xii) enable Lazy loading by installing babel plugins

  xiii) To serve the index.html and to injects imports into index.html install another webpack plugin

  xiv) edit package.json and add "build":'webpack' // This is for development

 

  while production or building

  create a new webpack.prod.config.js next to webpack.config.js

​    i) copy all the codes from webpack.config.js

​    ii) edit plugins and add new webpack.optimize.UglifyJsPlugin()

 

  xiv) install rimraff to delete the default development dist flow and install production flow

  xv) edit "build":"rimraff dist && webpack --config webpack.prod.config.js --progress --profile --color"

  xvi)

 

 

NOTE: WE CAN INSTALL ALL THE DEPENDENCIES IN THE SHARED PROJECT BY,

npm install GIVEN THAT THE PROJECT HAS package.json

 

 

 

Crawling with React js is difficult hence there comes Next.js is miniature React Framework

It has inbuilt lazy loading and used for lazy loading

 

Refer Nextgram in workspace

 

Transition group

 

npm install --save react-transition-group

import Transition from "react-transition-group/Transition';

 

Transition has 4 states

 

\1. Entering

\2. Entered

\3. Exiting

\4. Exited

 

6 different events

 

\1. onEnter = {() => console.log("onEnter")}

\2. onEntering = {() => console.log("onEntering")}

\3. onEntered = {() => console.log("onEntered)}

\4. onExit = {() => console.log("onExit)}

\5. onExiting = {() => console.log("onExiting)}

\6. onExited = {() => console.log("onExited)}

 

 

Transition has properties like,   in = decides the component has to be rebdered or not

​                  timeout = animation time

​                  mountOnEnter = will mounts component on enter state

​                  umountOnExit = will unmounts componet on exit state

​                  

Wrap The animate element inside the Transition.Transition accepts only function

 

 

CSSTransistion

 

4 classes Use classNames

 

\1. fade-slide-enter // css classes added when entering

\2. fade-slide-enter-active // css classes added when active when running through timeout

\3. fade-slide-exit  // css classes added when exiting

\4. fade-slide-exit-active // css classes added when running through timeout

 

fade-slide-enter, fade-slide-exit are used for initilization like opacity values

fade-slide-enter-active, fade-slide-exit-active -- use animation values

 

TransitionGroup

 

Use TransitionGroup in <ul>

 

<TransitionGroup componenet = "ul" ></TransitionGroup>

Use TransitionGroup along with CSSTransistion

Use TransitionGroup for ul

Use CSSTransistion for li

CSS Transition needs classNames and timeout 

 

 

 

ALTERNATIVES

 

** MOTION

** MOVE

** REACT-ROUTER-TRANSITION

 

 

 

REDUX SAGA

 

\1. Use in async side effect codes of actionCreators like logout,localStorage

\2. related to actions

\3. It is not a func but like a function use as function* (Generators)

 

 

** MATERIAL UI REACT

** BOOTSTRAP REACT

 

**UPDATED LIFE CYCLE HOOKS IN REACT 16.3**

 These life cycles are discouraged in react 16.3+

- componentWillMount() 
- componentWillReceieveProps()
- componentWillUpdate()

The new life cycles added are,

- **static getDerivedStateFromProps(nextProps, prevState) -**
- - **runs before render and componentShouldUpdate() and render**
  - **Used to update the state when there is change in the props and we need to update it in state**
  - **Used to sync props with state**
  - Must return something
  - Must implement static
- **getSnapshotBeforeUpdate() -** will get the snap shot of the DOM before update / changes 
- - Runs before componentDidUpdate()
  - Used for saving the current scrolling position of user
  - Must be implemented with componentDidUpdate()
  - Must return something

**SET INTERVAL WITH LIFE CYCLES IN REACT**

- Use SetInterval() in **componentDidMount()** 
- Use clearInterval() in **componentWillUnmount()** 

**TYPES OF REF API**

- Legacy String Ref's API
- Newer callback Ref's API
- Newest Object Ref's 
- Forward Ref

**STRICT MODE**

import React, { StrictMode } from "react";

 

<StrictMode>

...... Other codes

</StrictMode>

 

It is used to overlook of using best Practices

------

react scripts is responsible for webpack, npm, development server, babel

registerServiceWorker.js is responsible for PWA and it responsible for caching data. 

dangerouslySetInnerHTML is set html code in to the code explicitly 

All npm installs

 

** npm install create-react-app -g

** npm install --save prop-types

** npm install --save radium

** npm install --save axios

** npm install --save react-router

** npm install --save react-router-dom

** npm install --save redux

** npm install --save react-redux

** npm install --save redux-thunk

** npm install --save react-deduct-offline 

** npm install --save enzyme react-test-renderer enzyme-adapter-react-16

** npm install --save react-transition-group

** npm install --save redux-saga

** npm install --save react-bootstrap bootstarp

 

All webpack installs

 

** npm install --save-dev webpack

** npm install --save-dev webpack-dev-server

** npm install --save-dev babel-loader babel-core babel-preset-react babel-preset-env

** npm install --save-dev css-loader style-loader

** npm install --save-dev postcss-loader

** npm install --save-dev autoprefixer

** npm install --save-dev url-loader

** npm install --save-dev file-loader

** npm install --save-dev babel-plugin-syntax-dynamic-import

** npm install --save-dev babel-preset-stage-2

** npm install --save-dev html-webpack-plugin

** npm install --save-dev rimraf

`<p>hgsd<p>`