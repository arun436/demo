## Document Object Model

Document:-
-> Document is a root object and below it every object is connected like a tree structure.

Object:-
-> Every element is an object which is connected to root node document.

## How to select a particular object
-> If you want to select something it becomes easy if we give id's and classes.
-> If we want to access any element of a certain id or class name.




# querySelector returns the first element occured
-> But if you want all the elements matched then we can go through querySelectorAll.
-> querySelector,querySelectorAll always gives you an array.


## If you want to change the style of an object
const node = document.getElementbyId("div1");
node.style.background = "yellow" <- changes the background to yellow


## To create and element and attach to the tree
-> first create element
const newDiv = document.createElement("div"); <- I created some where this element
let node = document.getElementbyId("div3");<- Then we get the element of the tree where to attach 
node.appendChild(newDiv); <- It attaches the newDiv created to the div3 id element
-> The order that you append will be the order that will be in the tree.

## How to give text to the created element
newDiv.innerHTML = "Some Text"


## How to set an attribute to the created element
newDiv.setAttribute("anything","div-something");


## How to add text to body
const body = document.getElementsbyTagName("body")[0];
body.innerHTML = "This is a text"


## If you want to get the value of an attribute
console.log(newDiv.getAttribute("anything"));
-> It gives the answer (div-something)


## If you want to delete a child
node.removeChild(newDiv);


### Events:-
-> Whenever you click something you want something to happen that is called event.

## EventListener
const node = document.getElementbyId("div3")
node.addEventListener("click",function handleClick() {
    alert("Hello World!");
}
-> Here function handleClick() is called callback
## callback
-> It is nothing but it will be executed when something is done to execute that function
-> If function is somewhere
node.addEventListener("click",handleClick)
-> Here we don't use handleClick() because it is callback it calls automatically when it is clicked 
   so we use handleClick


## Event Bubbling and Event Capturing
-> It is default behaviour of JS
## Bubbling
const node = document.getElementbyId("div3")
node.addEventListener("click",function handleClick() {
    alert("Hello World!");
}
const node2 = document.getElementbyId("div2")
node.addEventListener("click",function handleClick() {
    alert("Hello World!");
}
const node3 = document.getElementbyId("div1")
node.addEventListener("click",function handleClick() {
    alert("Hello World!");
}
-> If all of these are connected child by child
-> Then if we click the utmost child then their parents will also be executed. This is called Bubbling.
## Capturing
-> If if gives the output from parent to child when clicked. This is called Capturing

## How to stop bubbing and capturing
event.stopPropagation();

##### ###########################################################################################
12 - Jan
##### ###########################################################################################

## Anonymous function
-> Functions which do not have any name are called Anonymous function
const something = function(){

}

## callback
-> Callback is a function which will be executed after an event is occured



## setTimeout
-> SetTimeOut is a method provided by web , it expects two parameters first is function second it timeout
setTimeout(function(){
    console.log("3");
}, 5000)
-> Here 3 will be printed after 5 sec


## setInterval
-> setInterval(function(){
    console.log("8")
}, 5000)
-> Here it will not stop printing 8 but it will print 8 for every 5000 milliseconds


## clearInterval
-> It accepts an id which is uniquely defined only one time and it stops execution of setInterval function and stops the execution doing repeatedly.

const demoInterval = setInterval(function (){
	console.log("8");
},2000)
clearInterval(demoInterval);



###
Heap -> It is used for storing variables i.e., memory allocation
### callstack
-> Whenever you call a function it will be pushed to stack. * It is removed only when the function execution completes or it returns something.
# function for below explanation
function division(x){
	throw new Error("custom error");
}

function multiply(x,y){
	const something = division(x);
}
function printSquare(x){
	const s = multiply(x,x);
  return s;
}
console.log(printSquare(5));
#
-> If an error is occured then we can find it in console
i.e., we get Uncaught error .... like that
    at division
    at multiply
    at printsquare
-> Here error is occured at division function which is called by multiply function which is called by printsquare function.


### Environment
-> It is a client side language so that our code will be executed in browser.
-> SetTimeout , SetInterval , ajax will be handled by browser in seperate thread.


######  Event Loop #########

### callstack webapi's callback queue
check in latentflip.com javascript

function
#
console.log("Hi!");

setTimeout(function(){
    console.log("Click the button!");
}, 5000);

console.log("Welcome to loupe.");
#
-> Here "Hi!" will be printed and setTimeout will be timed in webapi in seperately and "Welcome to loupe." will be printed by keep it in call stack and after completion of time of 5000 milliseconds then it will be pushed to callback queue and if the callstack is empty then it pushed setTimeout function to the callstack and "Click the button!" will be printed then
i.e.,
-> setTimeout gives guarentee that the function() will take atleast time of 5000 milliseconds time to execute but this not guarentee that the function() will be executed exactly at 5000 milliseconds because it may take more time because if any execution is pending in callstack it will not be pushed to callstack from callback queue

-> If we have many setTimeout functions then according to time and first in and first out the program will be executed


#### Key Points
-> JS is single threaded.
-> JS can be executed in asynochronous manner because of setTimeout and setInterval because its execution will be different by time.


### #################################################################################################
13 - Jan
### #################################################################################################
## ES-6 (Echma Ecript)
-> Our syntax became very easy to understand by EchaScript
Let's say
#
const property = "value" <!-- This  is property -->
const obj = { <!-- This is an object -->
    property1:"Value1",
    property:property
}
## Literal Objects
-> When key and values are same we can use some short hand like below
const obj={
    property1:"Value1",
    property,
}
## template String

## Difference between let,const,var
# var
-> It is function scoped
# let and const
-> block scope
-> Also const values cannot be changed

# ex - 1
const a = "Hello"
a = "World" 
-> you cannot reassign a value to const.

# ex-2
const a = {b:"Hello"}
a.b = "World"
-> It is valid because we are not reassigning const we are changing one of its value
because in JS objects are copied using reference and not by value.

## Arrow functions
-> Earlier
    function foo(){
        return "Hello"
    }
-> Now
    const foo= ()=>{
        return "Hello"
    }
    -> If you donot surround the flower braces it automatically returns "Hello"
    const foo= ()=> "Hello"

## Destructuring
-> suppose you have an object
# ex-1
const obj={
    a:{
        b:{
            c:{
                d:{
                    e:"Finally Some Value"
                }
            }
        }
    }
}
<!-- If you want to print e we use below line -->
console.log(a.b.c.d.e);
# ex-2
const obj2={
    a:"Hello"
}
-> If you want to print value of a
we use
console.log(obj.a);


const {a} = obj2;
-> The above line is from obj2 extract a

# ex-3
const obj3={
    a:{
        b:"Hello"
    }
}
const {b} = obj3;
console.log(b); -> It gives undefined -> because it checks only one level

-> Then to get we should use

const {b} = obj3.a;
console.log(b);

-> To change the name of that variable(b) then we use below syntax

const {b:storedValue} = obj2.a;
console.log("B is ", storedValue);

# In Ex-1 
-> If we need to print e
const {e} = obj.a.b.c.d;
console.log("The Value of E is " + e);
-> But still you are writing (obj.a.b.c.d) so we need to write purely destructuring
<!-- Find it out -->


## Array methods
const arr=[1,2,3,4,5,6]; <!-- The output should be [2,3,4,5,6,7] -->
-> You want to increment every number in the array by 1
# map 
-> Map is a function which goes through each and every item in your array and perform some operation to that item
arr.map((item)=>item+1);
or
const newArr = arr.map(function(item){
    return item+1
    });
console.log("New Array is ",newArray);
-> map function returns a function

# ex - 2
-> You need to find elements which are greater than 3
# filter
-> filter will go through each and every item in the array and checks the criteria that you have mentioned.
const filteredArray = arr.filter(function(item){
    return item > 3;
});

-> can we do that with map? Ok lets try
const newArr = arr.map(function(item){
    return item > 3;
    });
console.log("New Array is ",newArray);
-> It is returning the array of same size and it returned true and false i.e., map checks if it is greater or smaller and filter returns that value.

### #################################################################################################
15 - Jan - This keyword and object prototypes
### #################################################################################################
# Ex - 1
function foo(){
    console.log("This is",this);
}
foo();
# Output
This is [window]

-> Whenever you a create function this keyword is associated.
-> The root object of DOM is window.
-> If i use strict mode then is window still the root object ? -- No

Before that let us learn about call sight
-> let us design a call stack for the above function in example - 1.
-> But what is this here ? (Where this function was called right ?  Yeah that's true !!).
-> foo() will be in stack and that foo function is called from window object i.e., the function below it in the call stack.
    |           |
    |           |
    |           |
    |           |
    |   foo()   |
    |  window   |
    -------------
-> Here in stack foo() is called by window as shown in above figure.
-> It is an assumption that there is nothing below window and window is not a function.
-> call sight is a place from where a particular function is called.
-> If we use window.foo() also gives same output as in line number (335).

# Ex - 2
<script>
function something(){
    console.log(this);
}
function baz(){
    something();
}
function bar(){
    baz();
}
function foo(){
    bar();
}
foo();
</script>

# In call stack
-> First foo is pushed and foo pushed bar and similarly bar pushed baz and baz pushed something and something is using this keyword.
-> Then what will be this now ? baz()? wait but we got window now !!!!
-> We are going to study four rules now to identify this.

## Four Rules
# 1st Rule - Default binding
-> Default binding means "decide the call site and this will refer to the call site object".
-> Call site is a place from where a function is called.(check line no - 354).
-> Call stack is used to decide call site.
Example - 1:-
    function foo(){
        console.log("This is",this);
    }
    foo();
-> Here this refers to window and foo is called from window.
    -> console.log(this === window); gives true.
Example - 2:-
    var a = "Hello";
    function foo(){
        console.log("This is",this.a); <!-- Equal to -> sconsole.log(window.a)-->
    }
    foo();
## Rule - 2 - Implicit Binding
# Example 1 :-

<script>
    const a = 
    {
        caller:"Some Person",
        foo:function()
        {
            console.log(this.caller);
        }
    }
    const caller = "Some other person";
    a.foo();
</script>

Ouput:-
    "Some Person"

    -> foo() is called from a object , so this refers to a object , so this.caller refers to "Some Person".
# Example - 2

<script>
    const a = {
        caller:"Some Person",
        foo:function(){
            console.log(this.caller);
        }
    }
    var caller = "Some other person";
    let storedFunction = a.foo;
    storedFunction();
</script>

# Output:-
    "Some other person"

    -> Because we are not calling the function but we are storing the reference of the function in storedFunction as shown in line 427 and then this refers to window here , So we get Some other person.

## Rule - 3 - Explicit Binding

-> Till now we are getting the value of this by using call site.
-> Can we decide the value of this keyword explicitly,, Let's see
-> It can be done in three ways 
    -> bind
    -> call
    -> apply
# bind
-> Bind creates new copy of that function and to that function this is changed.
# Example - 1
<script>
    var pokemon={
        firstname:"Pika",
        lastname:"chu",
        getPokeName: function() {
            var fullname = this.firstname + this.lastname;
            return fullname;
        },
    };
    var pokemonName = function(){
        console.log(this.getPokeName() + " I chose you ");
    }
    var logPokemon = pokemonName.bind(pokemon);
    logPokemon();
</script>

# Output:-
    " Pikachu I chose you "

-> If we remove bind(pokemon) in line 456 and we place only (var logPokemon = pokemonName)
we get an error because there is no function on window named getPokeName() in window.
-> my requirement is i dont want to change syntax but i want this refers to pokemon.
-> We use bind

-> Bind creates exactly the same copy of pokemon name but what's difference ?
-> Inside bind i need to give what will be the value of this.

# call
-> In call copy is not created.
# Example - 1
<script>
    var pokemon={
        firstname:"Pika",
        lastname:"chu",
        getPokeName: function() {
            var fullname = this.firstname + this.lastname;
            return fullname;
        },
    };
    var pokemonName = function(){
        console.log(this.getPokeName() + " I chose you ");
    }
    pokemonName.call(pokemon);
</script>
-> Here we are not storing it but we call directly as shown above and making this refers to pokemon.
-> With bind keyword i can only pass one parameter which considers as this.
-> But in call we can pass many where first one refers to this and and we can pass parameters which are used in the function like below.
<script>
    var pokemon={
        firstname:"Pika",
        lastname:"chu",
        getPokeName: function() {
            var fullname = this.firstname + this.lastname;
            return fullname;
        },
    };
    var pokemonName = function(snack, hobby){
        console.log(this.getPokeName() + " I chose you and my favourite snack is " + snack + " and hobby is " + hobby);
    }
    pokemonName.call(pokemon, "Pizza", "reading");
</script>

# Output:-
    "Pikachu I chose you and my favourite snack is Pizza and hobby is reading"

# Apply
-> It is similar to call but you have to send your parameters in an array as shown below.
<script>
    var pokemon={
        firstname:"Pika",
        lastname:"chu",
        getPokeName: function() {
            var fullname = this.firstname + this.lastname;
            return fullname;
        },
    };
    var pokemonName = function(snack, hobby){
        console.log(this.getPokeName() + " I chose you and my favourite snack is " + snack + " and hobby is " + hobby);
    }
    pokemonName.apply(pokemon, ["Pizza", "reading"]);
</script>
# Output:-
    "Pikachu I chose you and my favourite snack is Pizza and hobby is reading"

-> Here we get same output as we get in call.

## Exception => Arrow Function

function foo(){
    return "Hello";
}
const foo = () => "Hello";

-> Arrow functions adopt this binding of enclosing scope.
-> Lexical binding of arrow functions cannot be overriden (even explicitly).

Example :-
<script>
    function foo(){
        return (a) => {
            console.log(this.a);
        };
    }
    var obj1 = { a:2 };
    var obj2 = { a:3 };
    var bar = foo.call(obj1);
    bar.call(obj2); // this doesnot over ride line 552 because of line 541.
</script>
-> Output will be 2
-> Here bar refers to 
    bar = (a) => {
        console.log(this.a);
    }
-> In line 540 - Arrow functions adopt this binding of enclosing scope.
-> value of this in arrow function depends on value of this in foo function.
-> Here it is enclosed in foo function which refers to obj1.
-> Then in line 541 again it will not be overriden hence the output will be 2 only not 3.
Example - 2 :-
<script>
    function foo(){
        setTimeout(()=>{
            console.log(this.a);
        },100)
    }
    var obj = {a:2};
    foo.call(obj);
</script>
Output:- 2

### ##################################################################################################
18 - Jan
### ##############################################################################################
## Shallow copy vs Deep copy
-> Shallow : only level 0 elements are copied by value
-> Deep: Each and every object is copied by value

# shallow copy
const obj2 = Object.assign({}, obj);

# Deep copy
JSON.stringify = converts object to string and stores at new location
JSON.parse => converts string to object
const obj2 = JSON.parse(JSON.stringify(obj)); <!-- This is not recommended -->
keep using try catch
try{
    const obj2 = JSON.parse(JSON.stringify(obj));
}catch(error){}


## OOPs concepts:-
-> JS is a functional programming language
-> JS is purely Object Oriented.
-> Classes in js are nothing but syntactical sugar.
# Example:
class Vehicle{
    constructor(noOfPeopleItCanCarry, noOfEngines, wheels) {
        this.people = noOfPeopleItCanCarry;
        this.engines = noOfEngines;
        this.wheels = wheels;
    }
    getPropertySpecs = () => {
        console.log(
            `This vehicle has ${this.people} people and wheels as ${this.wheels}`
        );
    };
}
const car = new Vehicle(5, 2, 4);
car.getPropertySpecs();
# Output
-> This vehicle has 5 people and wheels as 4

-> Constructors are also functions which will be called with new keyword
-> Whenever you call new keyword
    -> A brand new object is created somewhere
    -> Newly constructed object is prototype linked (later)
    -> Newly constructed object is set a this binding for function

-> Class :- A blueprint of how object would look like
-> Object :- instantiated from class

# Inheritance
class Car extends Vehicle{
    <!-- Assignment 2 - What type of copy it is -> reference or value. -->
    constructor(){

    }
    getPropertySpecs = () => {
        console.log("Hello");
    }
}
-> It gives output - Hello -> which is overriding of polymorphism

# Multiple Inheritance
-> In JS multiple inheritance is not supported because of ambiguity

### #################################################################################################
19 - Jan
### #############################################################################################

## Prototypes
-> Whenever you create an object a hidden property(__proto__) is automatically created.
function foo() {
    console.log("This is a function);
}
console.log("function is " ,foo.__proto__);
-> As everything is an object in Js, so function is also an object so we can proto of a function also.
-> We get a proto of a function and also we can get proto of an object and proto of an array.

# Example - 1
-> We have two object obj and obj2
-> We override the proto of obj2 and write it with obj

const obj = {
    name: "Vanshu",
    city: "Patiala",
    getIntro: function() {
        console.log(this.name, this.city);
    },
};
const obj2 = {
    name: "Arun",
}
<!-- warning : never use this -->
obj2.__proto__ = obj;

-> When we use  ->  obj2.city
    -> Search the object if not found then to next step.
    -> Search for proto of that object.

# Example - 2
const obj = {
    name: "Vanshu",
    city: "Patiala",
    getIntro: function() {
        console.log(this.name, this.city);
        return this.name;
    },
};
const obj2 = {
    name: "Arun",
};

obj2.__proto__ = obj;
console.log("Object 2 proto is ",obj2.getIntro());
# Output
"Arun", "Patiala"
"Object 2 proto is ", "Arun"

-> Here this.name in line (312) pointing to the name of obj2 i.e., it searches in current object.
-> Then this.city is not present in the obj2 so we search in its proto obj and prints Patiala.
-> return gives "Arun" if it does not return anything it will print undefined.

-> Whenever you create an object from class, that object gets access to all the public properties and methods of class.
let obj = new Object();
-> Now obj has prototype where all the methods are located like toString(), hasownProperty() etc.,

Object.prototype.toString = {

}
-> Here Object is a class which has protoype property and toString() method.

# Example
class Object{
    this.prototype = {
        toString = () => {}
    }
    constructor(){
        this.__proto__=this.prototype;
    }
}


### 1. Reverse a String With Built-In Functions
For this solution, we will use three methods: the String.prototype.split() method, the Array.prototype.reverse() method and the Array.prototype.join() method.

The split() method splits a String object into an array of string by separating the string into sub strings.
The reverse() method reverses an array in place. The first array element becomes the last and the last becomes the first.
The join() method joins all elements of an array into a string.
<script>
    function reverseString(str) {
    // Step 1. Use the split() method to return a new array
    var splitString = str.split(""); // var splitString = "hello".split("");
    // ["h", "e", "l", "l", "o"]
 
    // Step 2. Use the reverse() method to reverse the new created array
    var reverseArray = splitString.reverse(); // var reverseArray = ["h", "e", "l", "l", "o"].reverse();
    // ["o", "l", "l", "e", "h"]
 
    // Step 3. Use the join() method to join all elements of the array into a string
    var joinArray = reverseArray.join(""); // var joinArray = ["o", "l", "l", "e", "h"].join("");
    // "olleh"
    
    //Step 4. Return the reversed string
    return joinArray; // "olleh"
}
 
reverseString("hello");
</script>


### 2.
## Objective

In this challenge, we practice implementing inheritance and use JavaScript prototypes to add a new method to an existing prototype. Check out the attached Classes tutorial to refresh what we've learned about these topics.

## Task

We provide the implementation for a Rectangle class in the editor. Perform the following tasks:

# Add an area method to Rectangle's prototype.
# Create a Square class that satisfies the following:
# It is a subclass of Rectangle.
# It contains a constructor and no other methods.
# It can use the Rectangle class' area method to print the area of a Square object.
# Locked code in the editor tests the class and method implementations and prints the area values to STDOUT.

<script>
class Rectangle {
    constructor(w, h) {
        this.w = w;
        this.h = h;
    }
}

/*
 *  Write code that adds an 'area' method to the Rectangle class' prototype
 */
Rectangle.prototype.area = function (){
    return this.w * this.h;
}
/*
 * Create a Square class that inherits from Rectangle and implement its class constructor
 */
class Square extends Rectangle {
    constructor(s){
        super(s);
        this.h = s;
        this.w = s;
    }
}

if (JSON.stringify(Object.getOwnPropertyNames(Square.prototype)) === JSON.stringify([ 'constructor' ])) {
    const rec = new Rectangle(3, 4);
    const sqr = new Square(3);
    
    console.log(rec.area());
    console.log(sqr.area());
} else {
    console.log(-1);
    console.log(-1);
}

</script>
































