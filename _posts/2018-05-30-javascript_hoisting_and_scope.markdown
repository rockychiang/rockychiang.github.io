---
layout: post
title:      "Javascript Hoisting and Scope"
date:       2018-05-31 03:34:06 +0000
permalink:  javascript_hoisting_and_scope
---


Javascript is a popular and fundamental programming language for web developers, however, it can be difficult and confusing to learn as a newcomer. And much this confusion is due to the concept of scope and hoisting. For example, do you know what will be logged into the console by the following code?

```
var fruit = "apple";

function logFruit() {
      console.log(fruit);        // first log
			
      var fruit = "orange";
      console.log(fruit);        // second log
};

logFruit();
```

The correct answer is "undefined" and "orange" for the first and second one respectively. This happens because of hoisting and scoping. When the above code is run, javascript actually reads it like this: 

```
var fruit = "apple";

function logFruit() {
      var fruit;                 // fruit variable is declared but nothing is assigned
      console.log(fruit);        // This will log "undefined"
			
      fruit = "orange";          // "orange" is assigned to fruit
      console.log(fruit);        // This will log "orange"
};

logFruit();
```

Notice that inside the function, the *fruit* variable declaration is moved to before the first console log, but nothing is assigned to it. This is what **hoisting** is in javascript, it is the movement of all variable and function declaration (not the assignment) to the top of the containing **scope** (in this case the scope is the *logFruit* function). 

### Hoisting Functions


Another example of hoisting is as follows: 

```
dog();                           // first function
cat();                           // second function

function dog() {
      console.log("dog");
}

var cat = function() {
      console.log("cat");
}
```

In this example the first function will run successfully and log "dog" into the console, however, the second function will not run and instead it will give a TypeError. This might be confusing at first but it is made clear when we see how javascript actually reads the above code in the following way:  

```
function dog() {                 // function declaration is hoisted along with the function body
      console.log("dog");
}

var cat;                         // variable declaration is hoisted but not the function definition

dog();                           // This will log "dog"
cat();                           // This will return a TypeError

cat = function() {               // function definition stays in the same place and not hoisted
      console.log("cat");
}
```

Here we see one of the differences between function declaration and function expression. When **function declaration** are hoisted the function body is also hoisted to the top of the scope (as seen with the *dog* function above). Whereas in **function expression** only the variable declaration is hoisted but the function definition stays in the same place (as seen with the *cat* function).

### ECMAScript 2015 (ES6)


ES6 introduces two new ways for developers to declare their variables in javascript: `let` and `const`. These two keywords behave similarly to `var` in that they will get hoisted to the top of the scope when the code is executed. However, one of the key difference between them appears when they get hoisted. When `var` is hoisted it is initialized with the value "undefined" whereas `let` and `const` are uninitialized. Therefore when variables that were declared using `let` and `const` are referenced prior to the declaration they will return a "ReferenceError" instead of "undefined" (as shown in the code snippet below). 

```
(function trio() {
     console.log(human);         // This will log "undefined"
     console.log(elf);           // This will return "ReferenceError: elf is not defined"
     console.log(dwarf);         // This will return "ReferenceError: dwarf is not defined"
		 
     var human = "Aragorn";
     let elf = "Legolas";
     const dwarf = "Gimli";
})();
```

Another difference between `var` and `let`/`const` is illustrated below:

```
var human = "Isildur";           // first var declaration
let elf = "Elrond";              // first let declaration
const dwarf = "Durin";           // first const declaration

if (true) {
     var human = "Aragorn"       // second var declaration
     let elf = "Legolas"         // second let declaration
     const dwarf = "Gimli"       // second const declaration
		 
     console.log(human);         // This will log "Aragorn"
     console.log(elf);           // This will log "Legolas"
     console.log(dwarf);         // This will log "Gimli"
};
		 
console.log(human);              // This will log "Aragorn"
console.log(elf);                // This will log "Elrond"
console.log(dwarf);              // This will log "Durin"
```

Here we see the difference in **scope** between `var` and `let`/`const`. The scope of `var` variable declaration is global, which is why we see the second var declaration, the one inside the `if` block, overwrites the first one resulting in "Aragorn" getting logged twice in the console but not "Isildur". On the other hand, the scope of both `let` and `const` is local. This essentially means that the first `let`/`const` declaration are separate variables from the second `let`/`const` variables resulting in both "Legolas", "Elrond" and "Gimli", "Durin" being logged to the console.  

Hopefully, this article helped clear some confusion regarding hoisting and scope in javascript. If you think that this article contains any errors, please let me know. Once again thank you for reading and until next time.
