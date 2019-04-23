# Functions

Function in programming allows you to call and execute a block of code many times without repeating yourself. Function is useful to organize your code to avoid repetition

Declaring a function statement starts with typing the `function` keyword followed by function name. The function name can be anything, but it's important to select a good name that reflects what a function does. A function name's common convention is to use camelCase format.

```js
function myFunction() {
  // execute code here
  console.log('Hello from myFunction!');
}

// call on myFunction
myFunction();
```

You can then call on a function already declared by typing its name followed by parentheses, which can be used to send function parameters.

## Function parameters

A function can accept any kind data you passed into it by using parameters. Parameters are declared inside the function parentheses (`()`) and separated by comma. Then when the function is called, you can provide arguments for the parameters inside the parentheses:

```js
function myFunction( firstParameter, secondParameter) {
  console.log(`My first parameter ${firstParameter}`);
  console.log(`My second parameter ${secondParameter}`);
}

// call on the function and provide arguments for parameters
myFunction('Hedwix', 'Brown owl');
```

Parameters can be any valid data type that JavaScript understands, like number, string, or Boolean.

When a function with parameters is called without arguments provided, the value of the parameters on execution will become `undefined`:

```js
function myFunction( firstParameter, secondParameter) {
  console.log(`My first parameter ${firstParameter}`); // undefined
  console.log(`My second parameter ${secondParameter}`); // undefined
}

myFunction();
```

You can also declare a default value for parameter, in case there is no argument given when the function is called:

```js
function myFunction( firstParameter = 'Hedwig', secondParameter = 'Snowy White Owl') {
  console.log(`My first parameter ${firstParameter}`);
  console.log(`My second parameter ${secondParameter}`);
}

// call on the function and provide arguments for parameters
myFunction();
```

## Function With `return` statement

A function can optionally have `return` statement that will cause the function to return value to its caller. A return statement stops the execution of the code block inside the function and continues the execution of code after the function call:

```js
function returnExample() {
  console.log('Returning value to the function caller');
  return 'Hedwix';
}

// Store the return of the function in a variable
let functionResult = returnExample();
console.log(functionResult);
```

When you create a function with a `return` statement, make sure you put the statement in the last line of the function code block.

```js
function returnExample() {
  return 'Hedwix';
  // the line below return will not be executed
  console.log('Returning value to the function caller');
}

// Store the return of the function in a variable
let functionResult = returnExample();
console.log(functionResult);
```

If the statement is put before the last line, JavaScript will exit the function and ignore the code below `return`. You can also use return as it is without any expression to exit the function before the last line is executed.

## Function and variable

A variable can be declared inside a function code block, but its uses are limited inside the block it is declared:

```js
function printName() {
  let name = 'Hedwix The Owl'
  console.log(name);
}

printName();
console.log(name); // name is not defined
```

A function can also access variable declared outside of the code block:

```js
let x = 'Touch The Sky';

function playSong() {
  console.log(`Playing the song: ${x}`);
}

playSong();
```

## Code exercise

Write a function to count the area and perimeter of a square shape. They accept one parameter for the size of square side

* The formula for area is side*side
* The formula for perimeter is side*4

Then call on the functions and pass the size of square side as argument.

Here is an example output:

```shell
The square side is 8
The area of the square is 64
The perimeter of the square is 32
```