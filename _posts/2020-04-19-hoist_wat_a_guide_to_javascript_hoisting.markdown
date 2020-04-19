---
layout: post
title:      "Hoist WAT!? A guide to Javascript Hoisting."
date:       2020-04-19 18:28:12 +0000
permalink:  hoist_wat_a_guide_to_javascript_hoisting
---



When coding in Javascript, **Hoisting** is an important topic to understand when thinking about scope and order of operations in Javascript. But when the topic was first discussed in the JS Learn Tutorials, I was VERY lost. 
"**Hoist** WAT!?" - I said to myself.

![confused](https://media.giphy.com/media/5t9wJjyHAOxvnxcPNk/giphy.gif)

And if you are like me, things just weren't getting very clear.
SO, lets talk about **Hoisting**!

#### Definition

> **Hoisting** is a default behavior of JavaScript where variables and function declarations are moved to the top of their scope before code execution.

Thanks! But what does that mean?
Well, no matter where functions ``` function pizza(){} ``` or variables ``` var pizza ``` are declared, they are moved to the top of the scope, regardless if they were local or globally placed. BUT, their assignment happens back where they were placed ... in other words, only the declarations are "hoisted" to the top of the scope.

#### Javascript Life Cycle
Declaration ----------> Assignment ----------> Usage
``` var pizza ``` | ``` pizza = "8 slices" ``` | ``` console.log(pizza) // Output: "8 slices" ```

Looking at the above life cycle, Javascript will **Hoist** only the *Declaration*, leaving the Assignment and Usage stages where they were in the code.

To further discuss what is happening, we need to go over some visual code examples.
#### Hoisting In Code

##### Global Scope: The use of *"var"* - Correctly
```sh
var pizza = "8 slices"
console.log(pizza) // Output: "8 slices"
```

##### Global Scope: The use of *"var"* - Incorrectly
```sh
console.log(pizza) // Output: "undefined"
var pizza = "8 slices"
```
Here is what the Javascript interpreter sees with *"var"* being **hoisted**:
```sh
var pizza
console.log(pizza) // Output: "undefined"
pizza = "8 slices"
```
You can see in the above code, the *declaration* ``` var pizza ``` is hoisted to the top, where the *assignment* ``` pizza = "8 slices" ``` stays below the *usage of* ```console.log(pizza)```, which then produces an ```undefined``` output.

##### Function Scope: The use of *"var"* in a function - Correctly
```sh
function pizza() {
var message = "8 slices"
console.log(message)
}

pizza() // Output: "8 slices"
```

##### Function Scope: The use of *"var"* in a function - Incorrectly
```sh
function pizza() {
console.log(message)
var message = "8 slices"
}

pizza() // Output: "undefined"
```
Here is what the Javascript interpreter sees with *"var"* being **hoisted**:
```sh
function pizza() {
var message
console.log(message)
message = "8 slices"
}

pizza() // Output: "undefined"
```
Notice in the above code, the *declaration* ``` var pizza ``` is hoisted to the top of the function, where the *assignment* ``` pizza = "8 slices" ``` stays below the *usage of* ```console.log(pizza)```, again producing an undefined output.

##### Additional Function Scope: *using* a Function before *declaring* it
```sh
pizza()

function pizza() {
var message = "8 slices"
console.log(message)
}
```
What does the above code output? If you guessed ```"8 slices"```, you would be correct!
But why does this happen?

Here is what the Javascript interpreter sees with the *function declaration*  being **hoisted**:
```sh
function pizza() {
var message = "8 slices"
console.log(message)
}

pizza() // Output: "8 slices"
```

Now we know why functions can be *called to use* in various points of code before they are *defined* and still work!

#### What doesnt get Hoisted?
Javascript follows the rules of hoisting on functions and variables, so functions defined as variables do not get hoisted.
Javascript version ES6 introduced new features such as ```let``` and ```const``` variables, along with ```class```es. These new standard features change the way we think about scope, and have their own set of rules when it comes to hoisting. Generally, they require us to *declare* and *assign* them before *usage*.

Below are some examples.

##### Expression Functions: *declaring* a Function with *"var"*
```sh
pizza() // Output: "undefined"

var pizza = function () {
var message = "8 slices"
console.log(message)
}
```

The Javascript interpreter sees this as:
```sh
var pizza
pizza // Output: "undefined"

pizza = function () {
var message = "8 slices"
console.log(message)
}
```

##### Global Scope: The use of ES6 *"let"*
```sh
console.log(pizza) // Output: "ReferenceError: pizza is not defined ..."
let pizza = "8 slices"
```
Above we notice that instead of ```undefined```, we get an output of ```ReferenceError: pizza is not defined```. This is because ```let pizza``` is not hoisted to the top, but instead stays where it is *defined* in the code.

##### Global Scope: The use of ES6 *"const"*
```sh
function pizza(slices) {
  console.log(extraSlices * slices)
  const extraSlices = 2
}

pizza(4) // ReferenceError: extraSlices is not defined
```
In the code above, we get an ```undefined``` response because like ```let```, ```const``` does not get hoisted to the top of the function scope.

##### Global Scope: The use of ES6 *"class"*
Like a function, a class *declaration* DOES get hoisted to the top of scope, but unlike a function, the class remains uninitialized until evaluation. This generally means you have to *declare* a class before *usage*.

###### Incorrect *Class* Usage
```sh
var Margareta = new Pizza();
Margareta.sauce = "red";
Margareta.topping = "cheese";
console.log(Margareta); // Output: ReferenceError: Pizza is not defined

class Pizza {
  constructor(sauce, topping) {
    this.sauce = sauce;
    this.topping = topping;
  }
}
```

###### Incorrect *Class* Usage
```sh
class Pizza {
  constructor(sauce, topping) {
    this.sauce = sauce;
    this.topping = topping;
  }
}

var Margareta = new Pizza();
Margareta.sauce = "red";
Margareta.topping = "cheese";
console.log(Margareta); // Output: { sauce: "red", topping: "cheese" }
```
In the two above examples, you can see how if a *class* is *declared* before a *usage call*, it will not return the desired output!


#### Conclusion 
Hopefully the above examples help clear up the WAT!? in **Hoisting**. Javascript always follows protocol with it's order of operations, and having a better understanding of **Hoisting** when writing Javascript code will leave you with a much happier camper.

![happycamper](https://media.giphy.com/media/xTEvYwzGarSU4J4FiM/giphy.gif)

###### Some Additional Resources:
  - https://www.w3schools.com/js/js_hoisting.asp
  - https://scotch.io/tutorials/understanding-hoisting-in-javascript# Enter your title here

The content of your blog post goes here.
