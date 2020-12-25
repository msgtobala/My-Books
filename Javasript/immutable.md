HAS data types like

- MAP
- LIST

 

**INSTALLATION**

**npm install --save immutable**

 

**USAGE**

 

let Immutable = require('immutable');

 

var a = Immutable.map({

  x: 1,

  y: 2

})

 

var b = a.set('x', 10);

console.log(b);

console.log(a.get('y'));

console.log(Immutable.Map.isMap(a));

 

var map1 = Immutable.map({a:1,b:2,c:4});

var map2 = Immutable.map({d:3,e:4,f:5});

var map3 = map1.merge(map2);

 

var tstMap = Immutable.map({a: 1, b:2, c: 4});

var tsMap2 = tstMap.delete('b');

**LIST**

var list1 = Immutable.List([1, 2, 3, 4, 5]);

var list2 = Immutable.List([6,7]);

var list3 = list1.set(0, 100);

console.log(list3); // [100, 2, 3, 4, 5];