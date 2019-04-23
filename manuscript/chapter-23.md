# The old `var` keyword

Before the release of ES6, JavaScript declares a variable by using the `var` keyword instead of `let` and `const`:

```js
var myVariable = 'hereisastring';
```

So what does ES6 want to fix by releasing `let` and `const` keyword to replace `var`? It's because the `var` keyword declares a variable on a global level instead of a block level. Let me explain through an example:

```js
if(true) {
  var name = 'Hedwix';
}
console.log(name);
```

The code above will run just fine, but it really should not, because the variable `name` is declared inside the `if` block. It works because when you declare a variable with `var`, JavaScript will create the variable on a global scope, while it should be on the block scope.

But why bother with the scope of a variable? That's because when you have hundreds and hundreds code lines, it can become very frustrating to trace where the variable's value is being modified. There's a principle in software development called "principles of least exposure", which means you don't really expose any part of the software that is unnecessary. Block scoping a variable means ensures that the variable is exposed and accessible only from parts of your code lines that needs the variable to run properly.

This is the problem that JavaScript tries to solve with `let` and `const`. A variable declared with `let` keyword is almost identical in every way with `var`, except for the scope level. A `let` variable can't be accessed from outside of the block it was declared:

```js
if(true) {
  let name = 'Hedwix';
}
console.log(name); // throws error
```

The `const` keyword is short for _constant_, and variables declared with it can never be reassigned. Although if you assign an object or array with `const`, you can still assign new values its properties:

```js
const name = 'Hedwix';
name = 'Nathan'; // TypeError: Assignment to constant variable
```

```js
const myObject = {};
myObject.name = 'Nathan';
console.log(myObject.name);

const myArray = [];
myArray.push('Nathan');
myArray.push('Sebhastian');
console.log(myArray);
```

Since the release of ES6, JavaScript developers tend to avoid using `var` keyword from their codebase. The general convention is to declare a variable with `const` first. When you code your application and realize halfway that you need to reassign your constant value, then change `const` declaration into `let`.