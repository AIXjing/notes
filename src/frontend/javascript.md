# Javascript note

## 1. Javascript functions
### 1.1 Define a function
`function a() {...}`
`var a = function() {}`
### 1.2 Invoke a function
function execution or function invocation
`a();`

### 1.3 function scope
*Global
*lexical

## 2. Javascript type
### 2.1 Object is a collection of name/value pairs.
### 2.2 *Primitive type represents a single, immutable value
* Boolean: true or false
* Undefined: signify that no value has ever been set
It has been declared, and variable memoty has been allocated, but not been set to any value. 
undefined is not equal to not defined.
Can only have one value: undefined.

```js
var x;
console.log(x);

if(x== undefined){
    console.log("x is undefined");
}
```
* Null: lack of value
As opposed to undefined, which is lack of definition.
Can only have one value: null.
* Number 
It is the only numeric type in Javascript.
Always represented under the hood as double-precision 64-bit floating points.
JS does not have an integer type.
* String
It is a sequence of characters used to represent text.
use 'text' or "text"
* Symbol 
Not widely supported. 

## 3. Common Language Constructs
* String concatination
```js
var string = "Hello";
string += "World"; 
// string = string + "World";
console.log(string + "!");
```
* Math operators: +, -, *, /
```js
console.log(undefined/5); // return NaN, meaning not a number

function test1(a){
console.log(a/5);
}
test1(); // return NaN;
```
* Equality
```js
var x = 4, y = 4;
if (x == y) {
    console.log("True"); // return True
}

x = "4";
if (x == y) {
    console.log("True"); // return True
}
```

* Strict equality
```js
var x = '4', y = 4;
if (x === y) {
    console.log("True"); 
}
else {
    console.log("False"); // return False
}
```

* If statement (all false)
```js
// ***** If statement (all false)
if ( false || null || undefined || "" || 0 || NaN) {
  console.log("This line won't ever execute");
}
else {
  console.log ("All false");
}

// ***** If statement (all true)
if (true && "hello" && 1 && -1 && "false") {
  console.log("All true");
}
```

* Best practice for {} style
```js
// ***** Best practice for {} style
// Curly brace on the same or next line...
// Is it just a style?
function a() 
{
  return
  { 
    name: "Yaakov"
  };
}

function b() {
  return { 
      name: "Yaakov"
  };
}

console.log(a()); // return undefined;
console.log(b()); // return Object{name: "Yaakov"};
```
* For loop
```js
var sum = 0;
for (var i = 0; i < 10; i++) {  // if i has been defined early, do not define it again.
  console.log(i);
  sum = sum + i;
}
console.log("sum of 0 through 9 is: " + sum);
```

### 4. Handling default values
```js
function orderChickenWith(sideDish) {
  sideDish = sideDish || "whatever!";
  console.log("Chicken with " + sideDish);
}

orderChickenWith("noodles"); // return Chicken with noodle;
orderChickenWith(); // return Chickehn undefined without 2. line; 
```

### 5. Creating Objects using 'new Object() syntax'
* Object creation
```js
var company = new Object();
company.name = "Facebook";
company.ceo = new Object();
company.ceo.firstName = "Mark";
company.ceo.favColor = "blue";

console.log(company);
console.log("Company CEO name is: " 
  + company.ceo.firstName);

console.log(company["name"]);
var stockPropName = "stock of company";
company[stockPropName] = 110;

console.log("Stock price is: " + 
  company[stockPropName]);
```

* Better way: object literal
```js
var facebook = {
  name: "Facebook",
  ceo: {
    firstName: "Mark",
    favColor: "blue"
  },
  "stock of company": 110
};

console.log(facebook.ceo.firstName);
```

### 6. Functions explained
* Functions ARE objects
```js
// Functions are First-Class Data Types
function multiply(x, y) {
  return x * y;
}
multiply.version = "v.1.0.0";

console.log(multiply(3,5));
console.log(multiply); // return the code
console.log(multiply.version); // return "v.1.0.0"
```

* Function factory
```js
function makeMultiplier(multiplier) {
  var myFunc = function (x) {
    return multiplier * x;
  };

  return myFunc;  // passing the value of myFunc
}

var multiplyBy3 = makeMultiplier(3);
console.log(multiplyBy3(10));
var doubleAll = makeMultiplier(2);
console.log(doubleAll(100));

// Passing functions as arguments
function doOperationOn(x, operation) {
  return operation(x);
}

var result = doOperationOn(5, multiplyBy3);
console.log(result);
result = doOperationOn(100, doubleAll);
console.log(result);
```
### 7. Passing(Copying) variables by value vs. by reference
* Passing by value
Given b = a, passing/copying by value means changing copied value in b does not affect the value stored in a.
* Passing by reference
Given b = a, passing/copying by value means changing copied value in b does affect the value stored in a.
In JS, primitives are passed by value, objects are passed by reference. ("Under the hood", everything is actually passed by value. )
* primitives 
```js
var a = 7;
var b = a;
```
In this case, the number 7 is stored in an address (a box), e.g., 001. When copying a to b, b is copied in another box, e.g,, 002. Thus, changing b value does not affect a value.
* objects 
```js
var a = {x: 7};
var b = a;
```
The address of object a stores another address where store {x:7}.
When copying a to b, it actually copy the address to b, and the address is where stores {x:7}.
The way to change the object value follows:
`b.x = 5;`

### 8. Function Constructors, prototype, and the 'this' Keyword
```js
function test(){
    console.log(this);
    this.myName = "Jing"; // this points to the global object, i.e., this.
}
test();
console.log(window.myName); // "Jing"
```
* Function constructors 
Constructor functions technically are regular functions. There are two conventions though:
1. They are named with capital letter first.
2. They should be executed only with "new" operator.
```js
function Circle (radius) { 
  //console.log(this);      // Circle {}
    this.radius = radius;
}
Circle.prototype.getArea = 
  function () {
    return Math.PI * Math.pow(this.radius, 2);
  };

var myCircle = new Circle(10);  // equivalent to new object(); new when invoking the function together with new, "this" points to the created object.
console.log(myCircle.getArea());    // Circle {}

var myOtherCircle = new Circle(20);
console.log(myOtherCircle);

```
Another example:
```js
function User(name) {
  this.name = name;
  this.isAdmin = false;
}

let user = new User("Jack");

alert(user.name); // Jack
alert(user.isAdmin); // false
```
When a function is executed with new, it does the following steps:

1. A new empty object is created and assigned to this.
2. The function body executes. Usually it modifies this, adds new properties to it.
3. The value of this is returned.
In other words, new User(...) does something like:
```js
function User(name) {
  // this = {};  (implicitly)

  // add properties to this
  this.name = name;
  this.isAdmin = false;

  // return this;  (implicitly)
}
```
So `let user = new User("Jack")` gives the same result as:
```js
let user = {
  name: "Jack",
  isAdmin: false
};
```
Now if we want to create other users, we can call `new User("Ann")`, `new User("Alice")` and so on. Much shorter than using literals every time, and also easy to read.

That’s the main purpose of constructors – to implement reusable object creation code.
Functions created with the Function constructor do not create closures to their creation contexts; they always are created in the global scope. When running them, they will only be able to access their own local variables and global ones, not the ones from the scope in which the Function constructor was created. This is different from using eval with code for a function expression.
```js
var x = 10;

function createFunction1() {
    var x = 20;
    return new Function('return x;'); // this |x| refers global |x|
}

function createFunction2() {
    var x = 20;
    function f() {
        return x; // this |x| refers local |x| above
    }
    return f;
}

var f1 = createFunction1();
console.log(f1());          // 10
var f2 = createFunction2();
console.log(f2());          // 20
```

### 9. Object literals and the ´this´ keyword
```js
var literalCircle = { // new Object()
    radius: 10,
    
    getArea: function () {
        console.log(this);  // refer to {radius: 10}
        
        var increaseRadius = function(){
            this.radius = 20;        
}
        return Math.PI * Math.pow(this.radius, 2); // this refers to literalCircle
    }   
};

console.log(literalCircle.getArea()); // 314.1593
```

```js
var literalCircle = { // new Object()
    radius: 10,
    
    getArea: function () {
        var self = this;
        console.log(this);  // refer to {radius: 10}
        
        var increaseRadius = function(){
            self.radius = 20;        
        }
        increaseRadius();
        return Math.PI * Math.pow(this.radius, 2); // this radius = 20
    }   
};

console.log(literalCircle.getArea()); // 1256.64
```

### 10. Arrays in JS
```js
var array = new Array();
array[0] = "Yaakov";
array[1] = 2;
array[2] = function (name) {
  console.log("Hello " + name);
};
array[3] = {course: " HTML, CSS & JS"};

console.log(array);
array[2](array[0]);
console.log(array[3].course);


// Short hand array creation
var names = ["Yaakov", "John", "Joe"];
console.log(names);

for (var i = 0; i < names.length; i++) {
  console.log("Hello " + names[i]);
}

names[100] = "Jim";
for (var i = 0; i < names.length; i++) {
  console.log("Hello " + names[i]);
}


var names2 = ["Yaakov", "John", "Joe"];

var myObj = {
  name: "Yaakov",
  course: "HTML/CSS/JS",
  platform: "Courera"
};
for (var prop in myObj) {
  console.log(prop + ": " + myObj[prop]);
}

for (var name in names2) {
  console.log("Hello " + names2[name]);
}

names2.greeting = "Hi!";

for (var name in names2) {
  console.log("Hello " + names2[name]);
}
```

### 11. Closures
```js
// Closures
function makeMultiplier (multiplier) {
  // var multiplier = 2;
  function b() {
    console.log("Multiplier is: " + multiplier);
  }
  b();


  return (
      function (x) {
        return multiplier * x;
      }

    );
}

var doubleAll = makeMultiplier(2);
console.log(doubleAll(10)); // its own exec env
```

### 12 Fake namespaces
```js
// in js/script1.js file
var name = "Yaakov";
function sayHello (){
    console.log("Hello" + name);
}
// in js/script2.js file
var name = "John";
function sayHi (){
    console.log("Hi" + name);
}

sayHello(); // Hello John since name is in global scope.
sayHi(); // Hi John
```
To solve the problem,
```js
// in js/script1.js file
var yaakovGreeter = {};
yaakovGreeter.name = "Yaakov";
yaakovGreeter.sayHello = function (){
    console.log("Hello" + yaakovGreeter.name);
}
// in js/script2.js file   
var johnGreeter = {};
johnGreeter.name = "John";
johnGreeter.sayHi = function (){
    console.log("Hi" + johnGreeter.name);
}
    
// in app.js file
yaakovGreeter.sayHello(); // Hello John since name is part of global object.
johnGreeter.sayHi(); // Hi John
```     

### 13 Immediately Invoked Function Expressions (IIFE) 
```js
// in js/script1.js file
(function (window) {
    var yaakovGreeter = {};
    yaakovGreeter.name = "Yaakov";
    yaakovGreeter.sayHello = function (){
        console.log("Hello" + yaakovGreeter.name);
    } 
    
    window.yaakovGreeter = yaakovGreeter;
})();
// in js/script2.js file   
(function () {
    var johnGreeter = {};
    johnGreeter.name = "John";
    johnGreeter.sayHi = function (){
        console.log("Hi" + johnGreeter.name);
    }
    
    window.johnGreeter = johnGreeter;
})();

// in app.js file
yaakovGreeter.sayHello; // Hello John since name is part of global object.
johnGreeter.sayHi; // Hi John
```  
// Immediately Invoked Function Expression    
// IIFE
// (function (name) {
//  console.log("Hello " + name);
//})("Coursera!");
```