# Learning the the Key Attributes of ES6

> ## Template literal with ES6

> **Template literals** are string literals allowing embedded expressions.You can use multi-line strings and string interpolation features with them.They were called "template strings" in prior editions of the ES2015 specification.

> ## Example 1 with a **string**

> ES5

```javascript
console.log("string line 1\n" + "string line2");
```

> ES6

```javascript
console.log(`String line one string line 2`);
```

> ## Example 2 with **variables**

```javascript
const name = "jimmy";
const day = "Wednesday";
```

> ES5

```javascript
console.log("Hello" + name + "I hope you have a great day on" + day);
```

> ES6

```javascript
console.log(`Hello ${name} I hope you have a great day on ${day}`);
```

> ## Example 3 with an **object**

```javascript
const instructor = {
  name: "Chris",
  lesson: "ES6"
};
```

> ES5

```javascript
console.log(
  "Hello" + instructor.name + "today's lesson is on" + instructor.lesson
);
```

> ES6

```javascript
console.log(
  `Hello ${instructor.name} today's lesson is on ${instructor.lesson}`
);
```

> ## Example 4 with a **function** in ES6 using this

```javascript
const name = "jimmy";
const day = "Wednesday";
const instructor = {
  name: "Chris",
  lesson: "ES6",
  greet: function() {
    return `Hello ${this.name} today's lesson is on ${this.lesson}`;
  }
};
console.log(instructor.greet());
```

> This would result in a **TypeError** because the const variable can only be defined once

```javascript
const bob = ["Billy", "Joe"];
bob = ["John", "Deer"];

console.log(bob);
```

> You can add items to a const variable using the **.push function**

```javascript
const bob = ["Billy", "Joe"];
bob.push("John", "Deer");

console.log(bob);
```

> This is an example of using a **default parameter** in a function

```javascript
function hello(name) {
  name = name || "Mystery Person";

  console.log("Hello" + name + " !");
}
```

> This would log **"Hello Mystery Person !"**, because Mystery Person is the default value of name

```javascript
hello();
```

> ## Binding functions

```javascript
const teachers = {
name: "Jimmy",
speak: function () {
```

> Bound a function to a specific context

```javascript
let boundfunction = function() {
  console.log("later my name is " + this.name);
};
```

> Bound function will always run in bound context

```javascrip
setTimeout(boundfunction, 1000);
}

};

teachers.speak();

```

> To fix the prior exercise since in its current state it would run **undefined** you would want to bind this to the function

```javascript
const teachers = {
name: "Jimmy",
speak: function () {
let boundfunction = function () {
console.log('later my name is ' + this.name);
}.bind(this);
```

> Now this is binded to the function and in this case this is the objects name which is **"Jimmy"**

```javascript
setTimeout(boundfunction, 1000);
}
};

teachers.speak();
```

> ## Arrow functions
>
> An **arrow function expression** has a shorter syntax than a function expression and does not have its own this, arguments, super, or new.target. These function expressions are best suited for non-method functions, and they cannot be used as constructors.

```javascript
var materials = ["Hydrogen", "Helium", "Lithium", "Beryllium"];

console.log(materials.map(material => material.length));
// expected output: Array [8, 6, 7, 9]
```

> This is the previous example written as an **arrow function**

```Javascript

const teachers = {
name: "Jimmy",
speak() {
let boundfunction = () => {
console.log('later my name is' + this.name);
};
setTimeout(boundfunction, 1000);
}
};
teachers.speak();
```

> **Lexical binding** - they bind to scope where defined not where they are used

```javascript
let students = [
  { name: "Hugo" },
  { name: "Candace" },
  { name: "Taylor" },
  { name: "Dimitri" }
];
```

> There is an **implicit** return occuring in this function that can only be done in a single line

```javascript
let names = students.map(student => student.name);
console.log(names);
```

> same as

```javascript
let names = students.map(student => {
  return student.names;
});
console.log(names);
```

> This will log an array of the students names **(Hugo, Candace,Taylor,Dimitri)**

```javascript
function add() {
console.log("arguments object:", arguments);
```

> The **prototype.slice.call** basically takes the numbers given and slices the array starting at 0 and then calling each elemt of the ray and placing it within the argument which is stored in the variable numbers.

```javascript
var numbers = Array.prototype.slice.call(arguments);
var sum = 0;

numbers.forEach(function (number) {
sum += number;
});

return sum;
}
console.log(add(1, 2, 3, 4, 5, 6, 7, 8));
```

> This is the ES6 way of doing the previous function

> This is also an example of a rest function

```javascript
let add = (...numbers) => {
  console.log("rest parameters", numbers);

  let sum = 0;

  numbers.forEach(function(number) {
    sum += number;
  });
  return sum;
};
console.log(add(1, 2, 3, 4, 5, 6, 7, 8));
```

> This will give you the sum of all the numbers in the console log above

```javascipt
let add = (...numbers) => numbers.reduce((sum, number) => sum += number, 0);
```

> The 0 is the initial value in the above arrow function

> The **rest parameter syntax** allows us to represent an indefinite number of arguments as an array.

> Another example of a rest function using ES6

```javascript
function addStuff(x, y, ...z) {
return (x _ y) _ z.length
}
console.log(addStuf(1, 2, 'Hello', 'World', true, 99));
```

> ES6 example of a **Spread Operator** (takes the value of its elements and assigns it to another array)

```javascript
let random = ["Hello", "World", true, 99];
let newArray = [1, 2, ...random, 3];

console.log(newArray);
```

> This will log 1, 2, 'Hello', 'World', true, 99, 3

```javascript
let spreadEx = item => {
  let spreadArray = [...item];

  console.log(spreadArray);
  return spreadArray;
};
spreadEx("hello world");
```

> This will log ['h','e','l','l','o'...]

```javascript
let restEx = (...z) => {
  console.log(z);
  return z;
};
restEx("hello, world");
```

> This will log **["hello","world"]**

> Dry way of pulling out the elements of an array **destructuring**

```javascripting
var students = ["Julian", "AJ", "Matt"];

var x = students[0];
var y = students[1];
var z = students[2];

console.log(x, y, z);
```

> ## ES6 way of destructureing

The **destructuring assignment syntax** is a JavaScript expression that makes it possible to unpack values from arrays, or properties from objects, into distinct variables.

```javascripting
var a, b, rest;
[a, b] = [10, 20];

console.log(a);
// expected output: 10

console.log(b);
// expected output: 20

[a, b, ...rest] = [10, 20, 30, 40, 50];

console.log(rest);
// expected output: [30,40,50]
```

```javascripting
var students = ["Julian", "AJ", "Matt"];
let [x, y, z] = students
console.log(x, y, z)
```

> This would log Julian, AJ, Matt

> This is a way to omit an element in an array

```javascripting
let [x, , z] = students

This would log Julian, Matt

let [x, ...rest] = students
console.log(x, rest)
```

> This would log Julian **["AJ","Matt"]**

> This is an example of a function destructureing an array into 3 variables

```javascripting
let completedHomework = () => {
return ["Julian", "AJ", "Matt"]
};
let [x, y, z] = completedHomework();
console.log(x, y, z)
```

> This also works on objects

```javascripting
let instructor = {
name: 'Jimmy',
email: 'no@no.com'
}
let {
name: x,
email: y
} = instructor
console.log(x)
```

> This is an example of using a function and object and destructering it

```javascripting
let car = {
make: 'Honda'
};

function something(vehicle, year = 2011) {
console.log(vehicle.make, year);
};
something(car);
```

> This is an example of an **constructor function**

```javascripting
function Person(name, job) {
this.name = name;
this.job = job;
}
Person.prototype.getName = function getName() {
return this.name
}
Person.prototype.getJob = function getJob() {
return this.job
}
var goodGuy = new Person("Aang", "Avatar");
console.log(goodGuy);
```

> This logs Person { name: **'Aang'**, job: **'Avatar'** }

> This is the way to use class when using a constructors

```javascripting
class Person {
constructor(name, job) {
this.name = name;
this.job = job;
}
getName() {
return this.name;
}
getJob() {
return this.job;
}
}
var badGuy = new Person("Thanos"**, **"Murderer");
console.log(badGuy);
```

> This logs Person { name: **'Thanos'**, job: **'Murderer'** }

```javascripting
class Person {
constructor(name, job) {
this.name = name;
this.job = job;
}
getName() {
return this.name;
}
getJob() {
return this.job;
}
}

class SuperHero extends Person {
constructor(name, heroName, superPower) {
super(name);
this.heroName = heroName;
this.superPower = superPower;
}
secretIdentity() {
return `${this.heroName} is ${this.name} !!`
}
}

let batman = new SuperHero("Bruice Jonson II", "Batman", "Super Intelegence")
console.log(batman.secretIdentity())
```

> This is an example of extending one class with another one

```javascripting
class Person {
constructor(name) {
this.name = name;
}
set name(name) {
this.\_name = name;
}
get name() {
return this.\_name
}
}
let goodGuy = new Person('Jim Gordon');
console.log(goodGuy.name);
```

> This will log **Jim Gordon**

```javascripting
goodGuy.name = 'James Gordon';
console.log(goodGuy.name);
```

> This changes the log to **James Gordon**

```javascripting
let student = {
name: 'A-aron'
};
let status = new Map();

status.set(student.name, 'A-aron');
status.set('feeling', 'churlish');
console.log(status.get(student.name));
console.log(status.get('feeling'))
```

> Using the map class to map out a students name and feeling

```javascripting
const Guy = (function () {
const \_name = new WeakMap();
class Guy {
constructor(name) {
this[_name] = name;
}
set name(name) {
this[_name] = name;

        }
        get name() {
            return this[_name];
        }
    }
    return Guy;

}());
let guy = new Guy('Fieri');
console.log(guy.name);
```

> This is an example of **encapulation**
