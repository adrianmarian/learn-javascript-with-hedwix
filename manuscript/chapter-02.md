# Code Structure

A computer program is a series of code written in a text file. These text files are then run through software that is designed specially for running code (in the case of JavaScript, we can use Node.js)

In this chapter, we will learn about the building blocks of a code.

## Statements

A statement is a single instruction for the computer to run. Think of it like a sentence, but for computers. We can end a statement by using a semicolon `;` just like we can end a sentence by using a dot `.`

You can write multiple statements in a single line, but the convention is to write one statement per line:

```js
// This makes it hard to read
console.log("Hello, World!"); console.log("I'm learning JavaScript");
```

## Comments in JavaScript

In coding, comments are used to explain code in plain human language and to disable some code from being run by the runner, without deleting the code.

For example, let's create a new `chapter-02.js` file with more console logs:

```js
// This will print two lines of statements
console.log("Hello, World!");
console.log("I'm learning JavaScript");
```

The first line is a comment because it's being started with the `//` sign, which is interpreted as comments in JavaScript. Running the code above will print two lines of sentences into the console. To disable the first line, you can comment it like this:

```js
// This is two lines of statements with the first being commented
// console.log("Hello, World!");
console.log("I'm learning JavaScript");
```

The `//` sign is interpreted as comments in JavaScript, and Node will not run the line that is being commented.

Now when you run `node chapter-02.js`, you will only see the second line being printed into the console.

## Execution flow

A computer executes the statements in a top-down approach. That means the statement written first will be executed before the second statement, and so on.

```js
// Testing execution flow
console.log("Hello, World!");
console.log("I'm learning JavaScript");
console.log("This is a statement");
// Printing number
console.log(10);
console.log(20);
```

## Code exercise

Try to write your name, age and occupation, then print it to the console. The output would look like the following:

```shell
Nathan Sebhastian
Software Developer
27
```