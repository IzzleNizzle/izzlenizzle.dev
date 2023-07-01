---
title: Basic JavaScript Vocab List
date: 2019-08-16T13:37:00.000Z
description: A basic vocab list for those getting started.
tag: web development
author: Isaac
---

# JavaScript Fundamentals

Lets clear up some confusion; JavaScript is not the same as Java, these are two seperate programming languages. Now lets jump into some essential fundamentals you need to be familiar with while learning to be a developer.

I will only briefly cover these topics, it will give you good exposure to some of the concepts you will be working with.

## Basic Concepts

### Dev Tools

First things first, as a web developer you MUST become familiar with the developer tools available with your browser.

Major browsers have Developer Tools built into them and they are critical to our work. To open them, simply right click inside of any webpage, and select "Inspect"

![Dev Tools](/images/inspectPage.png "Dev Tools")


For our course we will be mainly developing in Google Chrome. Firefox is also a very good option but their dev tools vary slightly. So in order to avoid confusion, I recommend using Chrome if you don't already.

Once you understand the fundamentals it will be easy to switch later.

#### Console

For the purposes of JavaScript I will only introduce the "Console". Once your dev tools are opened you will see an option for Console. Your colors may look different than mine, that's fine. 

![Dev Tools Console](/images/consoleTab.png "Dev Tools Console")

In this console tab you can run any javascript directly in here. It is essentially a window to the Javascript that the browser tab is using currently.


#### Console Log

![Console Log](/images/consoleLogHelloWorld.png "Console Log")

Commonly when building with Javascript, we may use a ```console.log()``` method to print something to the console. This will be very helpful in troubleshooting our code. 

While a console log is not the only way to debug our code, it is a simple way to find out what is happening if our app is not behaving the way we expected. 


#### Selecting HTML Elements

In the Chrome Dev Tools, you can select an html element, make it blue, then go back into the console and you can play with it

Click this image to go to the youtube video showing this in detail;

[![Select HTML Elements](/images/htmlConsoleThumbnail.png "Select HTML Elements")](https://youtu.be/rydj8dS6qL4 "Youtube")


### Code Comments:

For various reasons, you can leave notes, thoughts, or even plan out your code by using Comments right in your code. There is a certain way to do this without breaking things. Javascript will notice your notes and will not run it as code. 


Single Line Comments:

```js
  // This is a comment, javascript ignores this line
```

Multi-Line Comments:

```js
  /* 
    With this syntax, we can comment
    on several different lines.
  */
```

## Vocab List

### Variables:

```js
let myNewVariable = 1234;
let shirtVariable = "A medium sized t-shirt";
let thisVariableIsAFunction = function() {
    // ... some content
};
```

Variables are things that you can store something in, and reference later. It might help to think of variables like a box with a name on it.

Variables can hold data; names, numbers, or even functions. They can even be empty and then changed later

```js
let emptyVariable;
emptyVariable = "Now it's not empty";
```

In Javascript we use a convention called camelCase when we name them. For example:

```js
let myNewVariable = 1234;
```
Notice how the first word is not capitalized, while all others after it are.


#### Variable Types

Var, Let, Const - They serve different purposes. Ultimately Const is not meant to change after being created, while Var and Let can be changed and manipulated.

#### Var 

```js
var name = "Jim";
```

This is a bit older syntax. It has some properties that make it hard to predict and a bit confusing. We will use Var in the beginning and it's good to be aware that it exists, but when doing your finest coding we should use ```let``` instead.

#### Let

```js
let name = "John";
```

This is the latest syntax for a variable. Let variables only live within the function (or scope) within they are created. 

** More on scope link

[More on "Scope"](#variable-scope)

#### Const

```js
const name = "John";
```

Const variables are meant to be declared once and not changed again. Changing the value of a Const will give you an error. Unless it's an Array or Object, but that complexity is not within the scope of this guide.


### Fundamental Data Types

There are several data types, slightly more emphasized in other programming languages. For our uses I won't touch them all, just the most common ones.

#### String

Strings contain textual content. It can contain any combination of numbers, letters, and special characters. 

```js
let str = "1. Hello W0rld!@#$*)("
```

You can declare strings using single quotes, double quotes, or backticks. (The key to the left of the #1, or above the tab key)

```js
// Notice these are all slightly different
let str1 = '123'
let str2 = "123"
let str3 = `123`
```

#### Converting Variable types

Note that you may need to convert a variable type. If you are working with numbers only and a variable comes in as a string, you may need to convert that string of only numbers to an integer or float.

```js
let firstNum = "123"
let secondNum = 234

let third = firstNum + secondNum
// This would not work accurately because you are adding a string to a number
```

Some simple ways to convert a string to a number are:

```js
let one = parseInt("123")
let two = parseFloat("123")
```

The main difference here is you would be better using ```parseFloat()``` if the number has decimals.

#### Boolean

True or false, that's it. Very useful actually.

```js 
var codingIsFun = true;
var codingIsEasy = false;
```

#### Objects

Objects are more complex.

Basic Object in the wild:

```js
var obj = {}
```


Objects always begin with curly brackets and can contain several different properties. They can contain any data type as values; Arrays, Strings, even more objects. For example:

```js 
var someObject = {
    key: "value",
    prop1: 123,
    prop2: [1,2,3],
    prop3: {
        nestedObj: "wow"
    }
}
```

Be careful! When dealing with multiple properties, ensure that they are coma seperated.

Attention to detail will help you avoid frustrating time spent finding a missing coma, or a missing bracket.

##### Some Object Lingo: 

Objects contain what are referred to as keys or properties.

When in the dev tools, you can always expand an object to see what is inside (assuming it's not empty).

A youtube video to demo this:

[![Exploring JS Objects](/images/htmlConsoleThumbnail.png "Exploring JS Objects")](https://youtu.be/kjuLz2qYl-g "Youtube")


#### Array

A simple array: 

```js
let arr1 = [ 1, 2, 3, "Four" ];
```

Arrays are a special container for multiple variables.

Arrays can have arrays inside of themselves, that is referred to as a multi dimensional arrays.

```js
let arr1 = [ aVariable, [ 1, 2, 3 ], 3, [ 1, 2, 3 ] ];

// An attempt at easier readability:
let arr2 = [ 1, 
    [ 1, 2, 3 ], 
    3, 
    [ 1, 2, 3 ] 
    ];
```

A useful property that is used very often is Array.length.

```js
let arr1 = [ 1, 2, 3 ];
console.log(arr1.length) 
// This would print: 3
```


### Numbers

Numbers have several data types, I won't cover them all. 

This is useful when changing Strings to Numbers. I'll focus on two options:

#### Int

Generally speaking Ints are for whole numbers, no decimals.

#### Float

Floats are for numbers with decimals.

#### What is typeof?

When you want to know what data type a variable is, you can use this command:

```js
let variableName = "This would be a string";
console.log(typeof variableName)
// String
```


## Functions:

A lot could be said about functions. They are amazing, they get stuff done. Although slightly confusing at first, they become a fundamental backbone for modern web development.

Lets look at an example:

```js
function doubleNumber (parameter) {
    return parameter * 2;
}

let argument = 5;

let doubledValue = doubleNumber(argument)
```

Lets break this down:

#### Define

```js
function doubleNumber (parameter) {
    return parameter * 2;
}
```

This is how you define a function. At this point the function has not yet "fired" yet, it has only been defined.

We also gave this function a name, "doubleNumber" this is for when we want to use it later.

#### Parameters

```js
 doubleNumber ( parameter )
```

In between the parenthesis you may have several words, or none. These are called Parameters, they are values that the function may use to do it's job.

Parameters are similar to variables. Available only to the function itself.

So, in this way we can create a function without knowing what information it will be provided with exactly. We will only know the value of the parameters when the function is actually being used.

#### Curly Brackets

```js
{
    return parameter * 2;
}
```

Very important, inside the curly brackets. You can make a function as big as you want, or simple like this one, it's all up to you.

Be careful with your brackets, if you delete one and not the other, you will have a bad time.

It's common practice that your function does one simple task, and does it very well. In my example it takes a number and multiplies it by two. Overly simple? Maybe.

After a function has been called it may, or may not, return a value. 

The function returns the value to whatever called it. 

So, in short this function takes a parameter, times it by two, and returns that value to whoever called it.

#### Firing a Function

```js
let argument = 5;

let doubledValue = doubleNumber(argument)
```

To break this down: 

1. We declare a variable called "argument" giving it a value of 5.

2. We declare another variable called "doubledValue" and assign it the value of whatever the function "doubleNumber" returns with the given argument.

* This may be confusing, but lets take it slow. 

OverView:

```js
let doubledValue = doubleNumber(argument)
```

We already understand:

```js
let doubledValue = 
```

What does this mean? 

```js
doubledValue = doubleNumber(argument)
```

Well, lets look at it this way:

Javascript has created the variable "doubledValue" and will wait to assign it a value. Javascript will wait until the function returns a value.

Ok, then lets focus on the last bit

```js
doubleNumber(argument)
```

We know in this example the value of "argument" is equal to 5, so lets plug that in for our visualization purposes

```js
doubleNumber(5)
```

Now we know the function just takes the number passed to it and doubles it. So, we know the function will return 10.

So after this fires

```js
doubleNumber(5)
```

It will become 

```js
10
```

Which is promptly assigned to "doubledValue"

```js
// Original
let doubledValue = doubleNumber(argument)
// A bit further
doubledValue = doubleNumber(5)
// After function has done it's job
doubledValue = 10
```

#### More about Functions

Functions hold blocks of encapsulated Logic. You can have functions inside of functions.

Be careful when working with functions that you don't mess up your brackets. It will happen, your code will break, no worries just be careful. Make sure you have one starting bracket, and one ending, then put some space in between and get to work.


### Conditional statements

Basic programming logic includes:


If, else

```js
if (iLikePizza) {
    orderPizza()
}
else {
    orderSomethingElse()
}
```

Switch, this is for multiple options:

```js
switch(name) {
  case "johny":
    console.log("Hello Johny")
    break;
  case "Jenn":
    console.log("Hello Jenn")
    break;
  default:
    console.log("Hello Person")
}
```

### Loops

Loops help you go do something multiple times. Loops very well with Arrays for example, if you want to print the contents of an array a for loop would be very helpful.

```js
let arr = [ 1, 2, 3, "Four" ];

for (let i = 0; i < arr.length; a++) {
    console.log(arr[i])
}
```

In this example, this for loop will execute this block of code for each item in the array.

There are different types of loops to be aware of.

```js
let iHaveMoney = true
let money = 9

while (iHaveMoney) {
    goBiking()
    if (money <= 0) {
        iHaveMoney = false
        // "break" tells the loop to quit immediately
        break
    }
    // Biking costs money
    money -- 
    console.log(money)
}
```

"Do while" loops are very similar, instead they ensure that the block of code will at least be ran once, no matter what.

```js
let iHaveMoney = true
let money = 9

do {
    // goBiking()
    if (money <= 0) {
        iHaveMoney = false
        // "break" tells the loop to quit immediately
        break
    }
    // Biking costs money
    money -- 
    console.log(money)
} while (iHaveMoney)
```

### Variable scope

A more advanced topic to be aware of is Variable scope. This boiled down means that variables live in certain spaces, meaning they normally cannot be accessed at all times. 

Usually you will declare a variable inside of a function, and you will only have access to that variable inside that function. In order to avoid unwanted changes to your variables, this is a good thing.

```js
function oneFunction() {
    // "var1" is only available within this function
    let var1 = 123;
    return var1 - 50;
}

function anotherFunction() {
    // This will not work
    // "var1" is not available within this function
    return var1 + 13; 
}
```

If you need, you can declare a variable "outside" of the functions, and then it would be available:

```js
let var1 = 123;

function oneFunction() {
    // This works
    return var1 - 50;
}

function anotherFunction() {
    // This works
    return var1 + 13; 
}
```


#### Reserved Words

There are certain words in Javascript that you can't use to name variables. This is because they are already being used to describe Javascript things, therefore you can't use them again.

```js
let String = "School";
let function = function () { 
    // ... some content
};
```

"String" is actually already being used by Javascript, as well as "function", so we don't want to use these exact names for variables. We'll need to think of something else.

This is not an exhaustive list, just be aware of this. You will receive pretty good error codes hinting at this if you run into this. 



### CDN


### Popup boxes
Alert and confirm. Good ot know, annoying ot use, prefer to use console log to confirm things



### Cache & Cookies




## Principles

### Millions of options

Understand that there  are millions of shorthand code or shortcuts people use to get things done "faster". First focus on the fundamentals, speed will come later.

### Vanilla Javascript

This refers to the use of plain Javascript, without the aid of third party libraries or frameworks.

### Modules, Packages, Libraries and Frameworks

For simplicity; Modules, Packages, Libraries and Frameworks will be referred to as packages for this section. 

There are various ways to pull in other code to aid our Javascript coding. This is very popular as you can bring in good benefits from using other packages. Very smart people/teams have created wonderful tools to help us make awesome web apps!

It's easy to become overwhelmed or go down some rabbit holes. It's good to be aware that there are thousands, even tens of thousands of quality projects out there designed to help make coding easier/better. These are being made at a rapid pace, see https://dayssincelastjavascriptframework.com/. I state this to communicate the need to understand the fundamentals and use tools lightly as you go. Don't waste too much time trying to learn every single package out there, because that's impossible. The better you understand the fundamentals, the easier it will be for you to learn new packages as you go.

Packages also come with a cost. More code means more data for servers to send to devices in order to display your webpage. This can mean for some slow websites, and this matters. Most people turn away from new webpages if it takes longer than 3 seconds to load. 

Be cautious including packages that you may not use or only use lightly, you may be able to build out your own functionality in a lighter way.


Packages, importing objects, what are methods?



### Built in packages

There are some very useful tools that are built in directly to Javascript, no need to import anything. Lets look at a few, Math and Date:

### Math Object
Don’t worry, you don’t need to be a math wiz

Things like random number, square root, absolute value, it can go deeper if you want, but these are the ones I use most 

Devision

Modulus

Addition, subtraction, Basic arithmetic 


When blocks are inside of blocks, think Russion nesting dolls. Be very alert and careful about brackets, they can wreck the whole app if a tiny mistake is made


### Date Object




More to talk about later:


#### More about Objects

Go a bit in depth about what things objects can do, as they are quite rebose

Objects Key/Value Pairs

Properties

##### More about Arrays

A bit more could be written about duplicating arrays cleanly, popping, shifting, splicing, etc. Array methods are useful and confusing at first. Probably good to extract to a different video/article

Strings

String concatenation, interpolation, length


Resources used to compile this list:

https://www.codecademy.com/articles/glossary-javascript
https://sharkysoft.com/archive/1997/jsa/content/039.html
