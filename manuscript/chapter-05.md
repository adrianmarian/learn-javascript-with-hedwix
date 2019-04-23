# Type conversion

JavaScript is a weakly and dynamically typed language. That means it doesn't enforce you to use one type of data consistently in a program's lifetime. You can reassign a string variable and make it a number variable:

```js
let a = 'Hedwix';
a = 2345;
```

The code above can produce error in other language, since it changed a string variable into a number variable, but not with JavaScript.

You've also seen how a number value will be converted implicitly when joined together with a string. This kind of behaviour is meant to make data conversion easier, but you can also convert data type **explicitly** by using special keywords for data conversion. They are:

1. String()
2. Number()

`String()` command is used to convert a number variable into a string, and here is how you use it:

```js
let myNumber = 10;
let myString = String(myNumber);
console.log(myString); // 10
console.log(typeof myString); // string
```

And you can convert a string into a number the same way:

```js
let myString = "10";
let myNumber = Number(myString);
console.log(myNumber); // 10
console.log(typeof myNumber); // number
```

## Code exercise

Swap the value of these two variables from string to number and vice versa:

```js
let numberA = 27;
let stringA = "92";
```

Here is the final result:

```js
console.log(numberA) // returns string "92"
console.log(stringA) // returns number 27
```