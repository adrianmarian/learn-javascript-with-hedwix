# Data types

A variable's value is a data, a piece of information to be used by the program. A variable can hold one type of data at any given moment, and the data type will define what operations you can do with the variable.

## Number types

The number type represents data of numerical value, both integer and floating point numbers.

```js
let radius = 5; // integer five
const PI = 3.14; // floating point number
```

With number data types, you can perform mathematic operations using operators such as addition `+`, subtraction `-`, division `/` and multiplication `*`.

```js
let a = 4;
let b = 10;
let c = a * b; // 40
```

There are also two special numeric values that belong to number data type: `Infinity` and `NaN`.

`Infinity` represents anything larger than the natural number in [science](https://en.wikipedia.org/wiki/Infinity). This value behaves the same way as infinity in mathematics: any positive number multiplied by `Infinity` equals `Infinity`, and any number divided by `Infinity` equals 0.

```js
let d = Infinity;
let e = 5;
let f = d * e; // Infinity
```

`Nan` is a value that represents anything that is not a number, and is usually a result of incorrect mathematic operation:

```js
let g = 'this is a string';
let h = 3;
let i = g * h; // NaN
```

Because `NaN` is already "not a number", any further operation on it will return `NaN` as well:

```js
console.log( Nan + 5 ); // NaN
```

## String Types

String data type represents data of character value, which consists of alphabet characters and must be enclosed between quotes. You can use both single quotes and double quotes to create a string:

```js
let name = "Hedwix";
let species = 'Eurasian Eagle Owl';
```

JavaScript treats both string the same way. One unique thing about string is that you can join two or more strings by using the addition operator `+`. This is called string concatenation:

```js
let name = "Hedwix";
let species = 'Eurasian Eagle Owl';

console.log ( 'My pet owl is called '+ name +' and he is an ' + species );
```

When a string variable is joined with a number variable, the number variable will first be converted into string and then concatenated into the string:

```js
let name = "Hedwix";
let age = 3;

console.log ( name +' is ' + age + ' years old' ); // it becomes a string
```

This is called implicit conversion, in which the number type automatically converted into a string.

### Template Strings

When creating a string using the backtick, you can embed JavaScript code into the string by using the dollar sign `$` followed by curly braces `{}`. For example:

```js
let name = 'Hedwix';
let sentence = `My pet owl is called ${name}`;
```

This is called template string, and it has been used widely for string interpolation since its release.

## Boolean

The Boolean data type is the logical type with only two values: `true` and `false`. This data type is widely used for information that can only contain a "yes" or a "no".

```js
let isAmericanCitizen = true;
```

One thing to note is that Boolean variables has its own convention. It uses some kind of prefix before the actual variable name:

```js
isFemale
hasDoctorateDegree
canSwim
```

Boolean is commonly used to control the flow of program, as you will learn later in the conditionals chapter.

## Null

Null is a data type that represents empty, or nothing.

```js
let x = null;
```

## Undefined

Undefined is a data type indicating that there is no value assigned. A simple example of undefined is when you initialize a variable without value:

```js
let a;
console.log(a); // undefined
```

It's a lot like null, but in this case there is no value assigned at all. Null is an assigned value, it's just happen that the value is empty.

## Object

Object is a special data type that can store many type of data. An object can hold more than just one values by using what is called **properties**. You will learn all about object data type in its own chapter about Object later.

## Checking Type by Using `typeof`

In order to know what data type a variable currently hold, you can use the `typeof` keyword with `console.log()`:

```js
console.log(typeof 42); // number

console.log(typeof 'bubble'); // string

console.log(typeof true); // boolean

let a = undefined;
console.log(typeof a); // undefined
```

## Code exercise

Write a program with three variables, each with the following value:

1. The first variable contain your first name
2. The second variable contain your last name
3. The third variable contain your age

Then print the variables by using a single `console.log()` statements. Example output:

```shell
Hello! I'm Nathan Sebhastian and I'm 27 years old Software Developer
```

You can use both template string or string concatenation.
