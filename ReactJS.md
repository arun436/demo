#### ########################################################################################
21 - Jan
#### ######################################################################################
#####   React   #######
-> React is a library created by Facebook.
-> It is a view part from MVC pattern


-> Model is a place where we place variables etc.,
-> View -> display that data
-> controller is a way to make changes to that data.

Difference b/n react and JS
# React
-> Syntax totally different.
-> It is not the language that browser understands.
-> For understanding react is converted to Javascript by some tools.
# Ex - 1
<script>
    const node = document.getElementById("root");
    const element = document.createElement("div");
    element.innerHTML = "HELLO WORLD"
    node.appendChild(element);
</script>

## CDN - Content Delivery Network
-> Let us consider a server and it has many data systems(servers)
-> If a user needs a data then there is no need to contact directly the main server we can collect the data from the nearest data center which acts as a server.
-> So that much work load will be reduced by main server
-> This is called CDN.
-> Netflix uses CDN.

# writing Ex - 1 in React
<script>
    const node = document.getElementById("root");
    const element = React.createElement("div",{
        className: "hello",
        children: "Hello World",  // Hello world will be in div
    },"We can write children here also to print");
    // React.createElement(typeOfElement,props,children).
    ReactDOM.render(element,node); // first argument is element which you want to render.
    // second argument is for which node we want to render.
</script>
-> Key is nothing but a property which we can identify the element uniquely
-> Key is used in React and Id is used in JS


## JSX - Javascript Extensible ( Javascript + XML )
<script>
    const node = document.getElementById("root");
    const element = <div className = "container">Hello World</div>;
    ReactDOM.render(element,node)
</script>
-> Babel is a tool which converts react or anything to JS code i.e., we can see the line 51.

-> When you want a dynamic name try using it in curly braces
<div id="root">Hello World</div>
<script>
    const node = document.getElementById("root");
    const children = "Hello world"
    const myClassName = "container";
    const element = <div element={myClassName}>{children}</div>
</script>
-> to place js code in html code we use them curly braces.
-> These are interpolation tags

# self - closing tags
-> Have you had self closing div in html ? NO !!!
<script>
    const element = <div classname={myClassName} children={children}/>;
</script>

# spread operator
Note - This is Javascript not React
# ex
<script>
    const children = "Hello World";
    const className = "container";
    const obj = {
        children,
        className,
    }
    console.log({...obj,className:"Some other"});
    const element = <div id="app-root" {...obj} className="not-container"/>
</script>
-> Spread means go to each and every property and spread it out.
...obj = children="Hello world",className="something"


<script>
    const node = document.getElementById("root");
    // Render two element side by side
    const helloElement = React.createElement("span",null,"Hello");
    const worldElement = React.createElement("div", "World");
    </script>

    -> Here we can only render only one element but we need to render two elements span and div
    so we wrap them in a single unit.

    <div>
        <span>
        </span>
    </div>
    -> By using this one div is a block level element so we cannot use this one we need to get an alternative which satisfy two conditions
        -> should not occupy extra space in DOM.
        -> Can contain children.
<script>
    const element = React.createElement(
        "div",  // type of element
        null, // props
        helloElement, // child 1
        worldElement, // child 2
    );
</script>

-> Here div occupies some space so we use React.Fragment

<script>
    const element = React.createElement(
        React.Fragment,  // type of element
        null, // props
        helloElement, // child 1
        worldElement, // child 2
    );
    ReactDOM.render(Fragment,node)
</script>

-> In JSX.
-> We always use below code rather than above code.
<script>
    const element = {
        <>
        <span>Hello world</span>
        <span>Good BYe World</span>
        </>
    };
    ReactDOM.render(element,node);
</script>

# Example - 1
<script>
    const element = {
        <div className = "container">
        <div className="message">Hello WOrld</div>
        <div className="message">Hello WOrld</div>
        </div>
    }
</script>

-> we are using same thing two times so we use shortcut

<script>
    const message = <div className="message">Hello WOrld</div>;
    const element = (
        <div className = "container">
        {message}
        {message}
        </div>
    );
</script>

-> Let's say both should render different content (parameterized function)

<script>
    const message = (props) => (
    <div className="message">
        {props.msg} {name}
    </div>;
    );
    const element = (
        <div className="container">
            {message({msg:"Hello world", name: "Ram"})}
            {message({msg:"Good Bye World", name: "Vinay"})}
        </div>
    );
</script>

-> In JSX

<script>
    const Message = (props) => {    // M should be capital in Message for sure.
        return (
            <div className="message">
                {props.msg} {props.name}
            </div>;
        );
    };
    const element = (
        <div className="container">
            <Message msg="Hello world" name="ARun"/>
            <Message msg="Good Bye World" name="Kumar"/>
        </div>
    );
    console.log(Message);
</script>

-> So we can reuse easily in JSX as above program.

# Character count
-> To find no of characters in a string program in JSX.
<script>
    const CharcterCount = (props) => {
        return (
            <div>
            The text has {props.text.length} characters
            </div>;
        );
    };
    const element = (
        <>
            <CharacterCount text="Hello"/>
            <CharacterCount text=""/>
        </>
    );
</script>

-> If length > 0 then print number of characters 
-> else print no characters

<script>
    const CharacterCount = (props) => {
        return (
            <div>
            The text has{" "}
            <strong>{props.text.length > 0 ? props.text.length : "No"}</strong>{" "}
            Characters.
            </div>
        );
    }
    const element = (
        <>
            <CharacterCount text="Hello"/>
            <CharacterCount text=""/>
        </>
    );
</script>

### ########################################################################################
25 - Jan
### #######################################################################################


-> Consider you are printing time using javascript
-> Using javascript the whole DOM will be re-rendered while changing the time second by second
-> While in React only the div which contains only be re-rendered again to update time
# Virtual DOM
-> This is done by virtual DOM in React
-> It creates two copies the one exact copy what was before and the one after the change
-> React compares these two trees and if any node changed it keeps track it.
-> If any node has changed it will re-render only that node.
-> Two type of comparisions - DFS - BFS.
-> If any node is found to be changed then react skips the sub tree and renders the whole sub-tree.
-> i.e., If parent is changed then subtree will not be visited because we should re render them again.

-> Now react identifed the node to be re-rendered
-> But virtual DOM is not a part of browser so it cannot make changes to browser .
-> DOM only can makes changes to browser and to the DOM to make changes React is the only who tells to DOM to make changes.
-> These changes are informed to actual DOM and DOM re-renders only changed nodes as informed by react.

<script>
    function tick(){
        const time = new Date.toLocaleTimeString();
        const element = (
            <>
            <div>{time}</div>
            <div>Static content</div>
            </>
        );
        ReactDOM.render(element,document.getElementById("root"));
    }
    setInterval(tick, 1000);
    }
</script>




-> At one particular time the browser parallely can handle only 6 requests at a time.
-> 


## JS Preprocessing
-> Processing javascript before it is used by browser.
-> First thing that can be used in pre-processing is minification.
# Minification
-> Removing all the white spaces.
www.javascript-minifier.com
# Uglification
-> suppose i have a variable name which is very long
suppose 
var ticTacToeSomethingElse = 2
as
var t = 2;

-> And with minification and uglification combines it becomes difficult to read and some people use it as security purpose
-> Third one is bundling
# Bundling
-> Combines multiple files into less number of files.

-> Where does this pre-processing happen 
     -> Developer machine.
     -> Browser.

-> Browser is the place where js executes.
-> But not preprocessing


1. -> We have source code and we process that on Browser.
2. -> I need a tool which understands JS.
-> That tool is NODE JS


-> Let's compare Node Js with JAVA

# JAVA

JRE - It executes Java

JDK - Set of libraries which help to develop in java.

JVM - Resonsible to run program

Maven / Gradle - To install libraries

# Node

-> Node is the combination of JDK and JRE i.e., libraries to write and execute JS.

-> Apart from Node browser it the one which provides these two.

-> V8 engine is like JVM.

-> like Maven in Java and NPM in Node.

3. -> some tool or library which can do preprocessing for me i.e, Babel.


-> When i type 
npm install bootstrap
-> It downloads whole source code of that module.
npm init 
-> It creates react project
-> npm install.

### ##########################################################################
26 - Jan
### ##########################################################################
-> Consider we have two file of javascript
-> and have two variables of two of it
-> If you want to use one variable in another file we should export it

Ex - 1
# file - 1
<script>
    const teslaBatchStartingYear = "2020";
    export default reslaBatchStartingYear;
</script>

# file - 2
<script>
    import anything from "./file-1";

    const teslsBatchEndingYear = "2021";
    console.log(anything);
</script>

# Output = 2020.

-> Whenever your export is not default
    -> The variable name should be same and
    -> That should be wrapped in curly braces.

# file - 1
<script>
    import {teslsBatchEndingYear, otherVariable} from "./file-2"; 
    const teslaBatchStartingYear = "2020";
    console.log(teslaBatchEndingYear);
    console.log(otherVariable);
</script>

# file - 2
<script>
    export const teslsBatchEndingYear = "2021";
    export const otherVariable = "2022";
</script>

-> If we are exporting only one variable or only one function or anything that is only one then we use default otherwise we use normal export.

## If we want to use react in JS file

we use
-> We are importing react libraries here.
<script>
    import React from "react";
    import ReactDOM from "react-dom";
    import "./styling.css"; // importing css files 

    function tick(){
        const time = new Date.toLocaleTimeString();
        const element = (
            <>
            <div className = "br-red">
                <div>{time}</div>
            </div>
            <div>Static content</div>
            </>
        );
        ReactDOM.render(element,document.getElementById("root"));
    }
    setInterval(tick, 1000);
    }
</script>

# In Styling.css

.br-red{
    background: red;
}

-> Here you want to import whole css file then we use import "./styling.css";
-> And this is called external styling.

# Inline styling

<script>
    import React from "react";
    import ReactDOM from "react-dom";

    function tick(){
        const time = new Date.toLocaleTimeString();
        const styles = {  // Inline styling
            backgroundColor: "green",
            fontSize: 20, // by default considered as pixels.
        }
        const element = (
            <>
            <div className = "br-red">
                <div>{time}</div>
            </div>
            <div style={styles}>Static content</div>
            </>
        );
        ReactDOM.render(element,document.getElementById("root"));
    }
    setInterval(tick, 1000);
    }
</script>

-> We can write code also as 

<script>
    import React from "react";
    import ReactDOM from "react-dom";

    function tick(){
        const time = new Date.toLocaleTimeString();
        const element = (
            <>
            <div className = "br-red">
                <div>{time}</div>
            </div>
            <div style={{  // first brace for JSX and second is to indicate it as object.
                backgroundColor: "green",
                fontSize: 20,
            }}
            >Static content</div>
            </>
        );
        ReactDOM.render(element,document.getElementById("root"));
    }
    setInterval(tick, 1000);
    }
</script>

-> In the above code at line 462 we have two curly braces i.e., the first brace indicates the JSX and second one indicates that it is an object.

-> We have Babel to compile React JS to vanilla JS.
-> We have Sass,Less to convert some framework of css to plain css. etc,..

-> But we need a tool to run all those things or processors
# and that tool is  "Web Pack".
-> Web pack is a tool which is used to run all the programs in your source code.
and we can write settings for webpack.

-> There are some people who wrote all the settings of webpack.
-> but where do we find them 
# -> And here we get the term "create-react-app".
-> By using this command web pack is set which compiles react js etc.,, to vanilla js and other things you want to 

-> npx gives the functionlity of create-react-app
## npx and npm
-> Npm is a tool that use to install packages.
npm install bootstrap
-> Npx is a tool that use to execute packages.
-> Packages used by npm are installed globally you have to care about pollution for the long term.-> Packages used by npx are not installed globally so you have to carefree for the pollution for the long term.
-> NPX uses cache and npm doesnot use cache.

-> In the created app
-> In public there is index.html and a div which has id="root"
-> there your code will be appended.

## React uses composition and not inheritence
(subclass is a parentclass)
class Engine
class Car extends Engine

class Person
class Student extends Person

-> Above statement-504,505 are syntatically correct but semantically not correct.
-> We can write it as 
    Car has a engine

    -> Whenever there is a "has a" relationship we use composition.

-> In statements-508,509 are correct syntatically correct and semantically also
-> i.e.,
    Student is a person

    -> Whenever there is a "is a" relationship we use inheritance.

-> In react definitely we have "has a" relationship so that's why we use composition.

### ###############################################################
27 - Jan
### ###############################################################
# Project
App is a component
    -> Class component
    -> functional component
# Class components
-> class "name of the class" extends React.component
-> Every class component has a render method





-> To change state variable function we use a function called setState function.

this.setState({
    counter: this.state.counter + 1,
});
-> this.state.counter is the previous value.

-> props cannot be changed and 
-> states can be changed.
-> When ever we change state render function will be called again
-> So don't use it in render function so that it will go into infinite loop.



### ##########################################################################
2 - Feb
### ##########################################################################


-> We can only pass props to childs
-> Parent can pass props only to immediate children

-> If you have two siblings in the project counter value and incrmentbutton

-> We cannot change the value of props so we keep the increment function in the app.js
instead of using it in incrementbutton of index.js

-> We can copy the prop and store it in state and then we can do increment but it is not available to the app.js and incrementValue.


# Component life cycle

-> How does a component get rendered ?
    First thing is Mounting - Means adding to virtual DOM
    -> First thing that will be called is constructor.
    -> Second thing that will be called is render.
    -> render will try to add the component or Mounted to virtual DOM 
    -> Mounting means adding to virtual DOM.

    Second thing is updating but when we need to consider 
    -> When props or states changes then render will be called.
    -> Then componentDidUpdate method called

    Third thing is unmounting when it is called
    -> Means removing from virtual DOM.
    -> componentWillUnmount is called here.

# useState Hook
-> Method provided by React.
-> It is used to store state variables.
-> useState returns an array and that array contains two items.
    -> Variable name.
    -> A method to change the state of the variable.

# use effect hook
-> dependency array
-> If any of the array variable changes then the function will be executed.

### ######################################################################
4 - Feb
### ######################################################################

-> Let  us  consider we have input component.
-> Whenever the page loads the input component should focused.
-> We have componentDidMount.

<script>
import React, { Component } from 'react';

class Input extends Component {
    constructor(props){
        super(props);
        this.inputElement = React.createRef();
    }
    componentDidMount() {
        const element = this.inputElement.current;
        console.log("Element is",element, element.id);
        element.focus();
    }
    render() {
        return (
            <input
            id="Some Value"
            placeholder="Some Value"
            style={{margin: 10}}
            ref={this.inputElement}
            />
        );
    }
}

export default Input;
</script>

<script>
import React, { useEffect, useRef } from 'react';

const Input = () => {
    const inputElement = useRef(null);             // define ref

    useEffect(() => {
        const element = inputElement.current;  // use ref
        element.focus();
    }, []);

    return ( // assign ref
        <div>
            <input placeholder="Some Value" ref={inputElement} />  
        </div>
    );
};

export default Input;
</script>


-> When ever state or props changes re-render occurs

const Input = (props) => {
    const [count,setCount] = useState(0);
    return <div></div>
}

-> When we change props then re-render occurs and state will be zero only as we are assingning it

-> But when we change state the problem occurs.

<script>
    const Input = (props) => {
        const [count, setCount] = useState(0);

        const handleIncrement = () => {
            setCount(count + 1);
        };
        return <button onClick={handleIncrement}>Increment</button>
    }
</script>

-> Here after every re-render the count should be zero as we are re-assigning 
-> But we didn't got it yesterday.
-> Here useState comes in to picture.

-> React internally maintains a table
-> It assigns the previous value to it.

<script>
    import React, { useEffect, useState } from 'react';

const Timer = () =>{
    const [time, setTime] = useState(new Date());

    useEffect(()=>{
        const id= setInterval(()=>setTime(new Date()), 1 * 1000); // useEffect Body
        console.log("Component Did Mount/Component Did Update with value of",id);

        return () => {
            console.log("Use Effect as component Un Mount value of ",id); // cleanup function
            clearInterval();
        }
    });
    return (
        <div>
        </div>
    );
};

export default Timer;
</script>
# Output will be

            Component Did Mount/Component Did Update with value of 1   // Execute useEffect Body
index.js:11 Use Effect as component Un Mount value of  1     re-render // Execute stored cleanup()
index.js:8 Component Did Mount/Component Did Update with value of 2
index.js:11 Use Effect as component Un Mount value of  2
index.js:8 Component Did Mount/Component Did Update with value of 3
index.js:11 Use Effect as component Un Mount value of  3
index.js:8 Component Did Mount/Component Did Update with value of 4
index.js:11 Use Effect as component Un Mount value of  4
-> It will mount and unmount again and again but why???
#

return JSX -> VDOM (converts) -> DOM

-> return function is stored as cleanup function.
steps:-
# Render
    -> JSX is mounted(renders) in VDOM and VDOM mounts(renders) to DOM.
    -> Execute UseEffect body.
    -> Store cleanup function.
# Re-render
    -> JSX is mounted in VDOM and VDOM mounts to DOM.
    -> Execute the stored cleanup function.
    -> Execute UseEffect body.
    -> Store cleanup function.

### ###########################################################################
5 - Feb
### ###########################################################################
# Revise previous class

-> We have

useEffect(fn)
fn()=>{
    // Body of the function
    return cleanup function.
}

-> But there was a problem
-> This code was executed everytime state changed.

1. JSX is rendered in VDOM which then renders to actual DOM
2. Execution of stored cleanup function (if stored initially that is in subsequent re-renders)
3. Execution of useEffect function
4. store Cleanup function.

-> It will execute again and again.
-> We need some tool to tell react when to execute useEffect (or) make useEffect conditional.
-> That is called Dependency Array.
<script>
    useEffect(()=>{
        const id= setInterval(()=>setTime(new Date()), 1 * 1000); // useEffect Body
        console.log("Component Did Mount/Component Did Update with value of",id);

        return () => {
            console.log("Use Effect as component Un Mount value of ",id); // cleanup function
            clearInterval();
        }
    },[]);
</script>
-> Whatever you mention in the dependency array that is stored somewhere.
-> Let us say I have a variable

let someVariable = "Some".
<script>
    useEffect(()=>{
        const id= setInterval(()=>setTime(new Date()), 1 * 1000); // useEffect Body
        console.log("Component Did Mount/Component Did Update with value of",id);

        return () => {
            console.log("Use Effect as component Un Mount value of ",id); // cleanup function
            clearInterval();
        }
    },[someVariable]);
</script>
-> Whenever useEffect tries to fires it stores the value of someVariable.
-> Due to somereasons re-render occurs and value of the variable becomes changes.
-> If the previous of the variable of the variable and current value of the variable doesnot match then only the useEffect will be fired.

-> When useEffect is fired first time
useEffect(()=>{}, [undefined])
-> It will be undefined and then undefined will be compared so that's why useEffect is always fired atleast once.

-> If you want to execute only once then we should keep an empty array.
-> If it is empty for the first time it will be
useEffect(()=>{},[undefined]).
-> For the first time setInterval will be fired and if we try for re-render
-> The previous value of dependency array is Previous Value = []
-> The current value of dependency array is Current Value = []
-> It is executed only once because it is not varied.
-> So it is similar to componentDidMount.
-> If useEffect has many items like
useEffect(()=>{},[1,2,3]).
-> If atleast one value changes then useEffect will be fired again.
### ################################################################################
8 - Feb
### ################################################################################
Doubt class
### ############################################
React rendering process :-

-> Whatever code we write in react they get translated to react elements which get mounted on the real DOM.

-> React team split the process in two
    1. Render phase
    2. Commit phase

1. Render phase

     Root
      |
      |
      A
      |
      |
      B
-> Root will render a component called A and that renders another component called B.
-> All these things will come under Render phase.
-> React will start from root component and goes down.
-> While going down we know that each component is in JSX form and while at every component react will call a createElement() function in which JSX is passed as an input to the function and then it gives the output in react elements or plane javascript objects.
-> i.e., rendered output is react elements

     JSX
      |
      |  createElement()
      |
React Elements

2. Commit phase

-> Whatever the rendered output is there i.e, all the react elements will be applied to the DOM.

     JSX
      |
      |  createElement()
      |
React Elements  --->    DOM(Real DOM)

-> This is what occurs in initial render.
-> In re-render the changes that occur only will change later.
-> Babel is used to some kinds
    -> All the JSX will be converted into normal JS
    -> Whatever ES6 and beyond you will write it converts into ES5 and lesser also , it is transpiler also.
# Example
<!-- JSX Syntax -->
<script>
    return <SomeComponent a={42} b="testing">Text here</SomeComponent>
</script>
is converted to
<!-- React elements -->
<script>
    return React.createElement(SomeComponent, {a:42, b:"testing"},'Text here')
</script>
<!-- returns plane javascript object or react element -->
{ type: SomeComponent, props: {a: 42, b: "testing"}, children: ["Text here"]}

# In re-render phase


     JSX                    previous Render
      |                           |         changes
      |  createElement()          |         -------->     DOM
      |                           |
React Elements                 New Render


-> Previous Render and New render will be compared and then changes will be applied to the real DOM.
-> Mounting means let us consider a component is rendering for the first time and this is called Mounting.

                                           (Re-rendering)
      Root                            
       |            JSX                    previous Render
       |             |                           |         changes
       A  ------>    |  createElement()          |         -------->     DOM
       |             |                           |
       |         React Elements               New Render
       B             |
                     |
                     | initial Render
                     ------------------> DOM



-> Let us consider B component is flagged as needing update i.e., it needs to update
-> React will ignore or discard all the components which are not flagged as needing update and it will only re-render the process only on the components which are flagged as needing update.
-> In class component the lifecycle method that we use to avoid unnecessary re-render is shouldComponentUpdate(nextProps, nextState).
-> It will return boolean value , if it returns true it will re-render if false it will not
-> In function component it will be React.memo.

-> Example of a doubt
<script>
    import { useState } from "react";
    import "./styles.css";

    export default function App() {
    const [count, setCount] = useState(0);
    const handleClick = () => {
        setCount(c => c + 1);
        console.log(count);
    }
    return (
    <div className="App">
      <button onClick={handleClick}>Increment</button>
      <p>Count: {count}</p>
    </div>
  );
}
</script>
-> In browser if we click increment button we can find the count in the browser will be incremented from zero to one
-> But on the console we can find it will be zero only because the setCount will be executed at last after all the statements are executed in the function because it is asynchronous.
-> Think of setCount as setTimeout in eventLoop similar to that it has callstack if call stack is empty then it will run setState function.
### ######################################
Normal class
### ######################################
# Doubt - why to change reference
-> In reactJs of useState
-> We first copied and state was assigned to newArray
[] --> []
      (state: newArray)
-> In react if a state updates react compares to two VDOM's the previous one and new one
-> How VDOM come to know the state has changed.
-> It compares previous and new Array if found any difference it will re-render.

-> suppose it is very very nested array
[[[[][][]]]]
-> If there is no change is at level 1 and then it will go level2 and then to level3 and so on until it finds changes.
-> If we change the array reference it does not need to go to depth to find that the state is changed.

# Doubt - How useState is async

<script>
    const [counter, setCounter] = useState(0);
    useEffect(()=>{
        setCounter(counter + 1);
        console.log("This is some log");
    },[counter])
</script>

-> when i do setCounter(counter + 1) what is suppose it happen --> re-render..!
-> Does it re-render as soon as this statement is encountered   --> No .. so when does this re-render?
-> It first completes all the steps remaining and then it will be re-rendered as state is changed.
-> because if it does re-render immediately then the code below will not be executed.

### #########################################################################
9 - Feb
### #########################################################################
-> New Project - feb9
# Question
-> Let us consider you have two links Home and about
-> When Home is clicked it should show Home is clicked and if about is clicked it should show about is clicked. ???
-> What we think is
[aboutButtonClicked,setAboutButtonClicked]
[homeButtonClicked,setHomeButtonClicked]
->
aboutButtonisClicked?<About>:<Home>
-> It will become really tricky for a whole website. How do i manage this
-> i.e., as soon as you click anything you can find that url will be changed
-> Taking differents url's when a component is clicked is efficient.
/about   - url   then show  <About/>
/home    - url   then show  <Home/>
-> Url's in react are not defined by themselves for this you have to understand Single Page Apps.
-> Whatever the apps we make in react are single page applications
-> i.e., whenever browser starts downloading, it downloads the whole code.

-> What happens when we click a thing in a website
    1. Browser will download the code related to My Timeline
    or
    2. Browser will execute the piece of code responsible for my timeline
-> Yes Browser will download whole code(bundle) and execute the piece of code when clicked on it.

-> Bundling is the reducing the filesize.
-> i.e., if home and about are in same page when the page is opened the whole bundle of code is downloaded.
-> When we click home it will go to home or else about
-> If we want to download only home or about other than downloading the whole bundle then we should go for other languages other than react.

-> There must be a functionality in react that allows to make url's 
-> No there is not there.
-> For that we need to use a third party library
#
npm install react-router-dom
#
-> now i downloaded but how to use this library
check out documentation - reactrouterdom

<script>
    import {
    BrowserRouter as Router,
    Switch,
    Route,
    Link
    } from "react-router-dom";
</script>

-> this should be inserted above the functional component or class component
-> "as" means we are changing name of BrowserRouter.

<script>
        <>
      <Router>
        <div style={{display: 'flex', justifyContent: "space-evenly"}}>
          <Link to="/">Home</Link>
          <Link to="/about">About</Link>
        </div>
        <Switch>

        <Route path="/" exact>
            <Home />
          </Route>

          <Route path="/about" exact>
            <About />
          </Route>

        </Switch>
      </Router>
    </>
</script>

-> The whole code should be in <Router> element and we use Link tags instead of anchor tags for faster rendering and re-rendering
-> And we enclose paths in <Switch> element and it should be in particular manner where Home should be last otherwise it will not be displayed . It we want to display exactly as shown in the js file then we use keyword exact in the Route element as shown above.

-> For deployment of project we have vercel.com so that everyone can access it.

### ##############################################################################
10 - Feb
### ##############################################################################
-> We know that Js is a single threaded language
-> Promises are used to handle asynchronous code.
-> Suppose there is some code which is asynchronous...what is asynchronous? -->not in the same flow
-> Suppose we need a code that should not happen sequently.
-> If it is synchronous the performance will be decreased because it will take alot of time to execute.
-> At some later point whenever CPU is free it will to do the task that is remaining this is done using promises.

                            Single Threaded language
                                        |
                                        |
                                        |  --- > 5 sec
                                        |
                                        |
                                ------------------
                                        |
                                        |
                                        |  --- > Blocked
                                        |
                                        |
-> Let us consider the async code depends on the solution of the code that takes time to execute then we use promises.
-> We need a method to do the code to wait.
# syntax
<script>
    const customPromise = new Promise((resolve,reject) =>{
        resolve("Got this message after resolving")
    })
</script>
-> To make a variable as promise we do like above here promise is a function which accepts two parameters.
-> resolve means successfully executed.
-> Reject means could not execute.

-> Through syntax we are trying to learn how to make things asynchronous.

-> By resolving or by rejecting we are executing the task.
-> What if some code is depend on the other code for that we have .then() method

.then() :-
    -> Execute the function when particular promise has been resolved.
<script>
    const customPromise = new Promise((resolve,reject) =>{
        resolve("Got this message after resolving")
    });
    customPromise.then(()=>{
        console.log("Completed this task");
    });
</script>
-> Here .then() is executed then customPromise is done after execution.
<script>
    const customPromise = new Promise((resolve,reject) =>{
        // Did some complex computations
        const result = 40;
        resolve(result)
    });
    customPromise.then((res)=>{
        // Whatever the result was add 2 to it.
        console.log(res + 2);
    });
</script>
-> Here we need the result of the customPromise and need to supply it to the .then() function
-> so we should write resolve(result).
-> That particular data we are sending in resolve so that we can use later.
-> .then() recieves whatever the data that is sent by the resolve.
-> i.e., if it finds first resolve then it goes to the .then() method.

# Nested promise
<script>
    const customPromise = new Promise((resolve,reject) =>{
    // Did some complex computations
        const result = 40;
        resolve(result)
    });
    const anotherPromise = customPromise.then((res)=>{
        // Whatever the result was add 2 to it.
        const response = res + 2;
        return new Promise((resolve,reject)=>{
            resolve(`some custom message ${response}`);
        });
    });
    anotherPromise.then((result)=>{
        console.log(result);
    });
</script>

-> Here instead of returning data we are returning promise so that we can use it by using .then()
-> So we can have multiple .then() functions.

-> .then() is called when resolved

## .catch()
-> .catch() is called when rejected
<script>
    const customPromise = new Promise((resolve,reject) =>{
        // Did some complex computations
        const result = 40;
        resolve(result)
    });
    const anotherPromise = customPromise.then((res)=>{
        // Whatever the result was add 2 to it.
        const response = res + 2;
        return new Promise((resolve,reject)=>{
            reject(`some custom message ${response}`);
        });
    });
    // anotherPromise.then((result)=>{
    //     console.log(result);
    // });
    anotherPromise.catch((err)=>{
        console.log("Error is",err);
    });
</script>
# Output
Error is some custome message 42

-> As soon as an error is encountered then .catch() is executed.
-> It will find the catch only below it i.e.,
.then(code1)
    |
.then(code2)
    |
.catch(err)
    |
.then(code5)
-> If we encounter an error in .then(code5) then it will check the .catch() below it but not the
catch that are executed before.

## fetch()

-> We have two things frontend and backend.
-> Frontend demands data from backend i.e., client demands data.
-> server connects to the database and returns the data to the client.
-> we(Frontend) demands the data from server using fetch().

# syntax
fetch('http://example.com/movies.json')
.then(response => response.json())
.then(data => console.log(data));

-> we give url of the server from where we need to fetch the data.
-> So this fetch returns a promise ---- but why??
-> Because fetching data from server taking lots of time.
-> If it returns a promise then we use .then()
-> Here in the second line of the syntax response converted to json which is again a promise and json() is an inbuilt method which returns a promise.
-> Then we use .then() again and then we can do whatever we want to do with the data.

### ####################################################################
11 - Feb
### ####################################################################
-> taking one input - city
-> Based on that we have to show the weather of the city

-> How we know the weather of that city we have api's for that current weather api's.

npm install react-bootstrap bootstrap

-> Installs bootstrap and react-bootstrap

-> In order to work it to whole app we can include it into index.js and app.js of src

-> Normally we did not used the statement 
import React from "react"

-> Due to version 17 it automatically imports react in the project.

-> type ------ rsc ------ for functional component snippet.

-> Whenever I click on submit field should not be empty and get weather data from city.


### ##############################################
15 - Feb
### ###############################################

component with Redux

-> Read some values from the storex












































