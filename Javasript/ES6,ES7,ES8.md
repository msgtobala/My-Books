# ES Versions of JS

### Using Spread Opeators in JS

```js
let fullName = {
	first: 'Akash',
	last: 'Rajvanshi'
};

fullName = {...fullName, age: 22}
console.log(fullName) // { first: 'Akash', last: 'Rajvanshi', age: 22 }

// Extra Features 
// 1. Changing content of an object
fullName = {...fullName, age: 25}
console.log(fullName) // { first: 'Akash', last: 'Rajvanshi', age: 25 }

// 2. Copy data of an object :
const copy = {...fullName};
console.log(copy) // { first: 'Akash', last: 'Rajvanshi', age: 25 }

// 3. Defaults Values  
const allData = {age: 30, ...fullName} // Remain default for fullName
console.log(allData) // { first: 'Akash', last: 'Rajvanshi', age: 25 }
```

