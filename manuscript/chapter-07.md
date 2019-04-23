# Control flow statements

Up until now, the computer runs every single line of code written in the text files. But what if we only want to run some lines of code only when certain conditions are matched? For example, we might want to run a console log only when the value of `x` is 10:

```js
let x = 10;
if (x === 10) {
  console.log(`The value of x is ${x}`);
}
```

The code above is an example of a control flow (or conditional) statement. The point of conditional statement is "if condition is true then run some code". That way, we can control what code to run based on the value of a variable.

There are several control flow statements that can be used to control JavaScript code execution, and we'll start by learning the _if statement_.

The syntax of if statement started with the keyword `if` followed by parentheses (`()`) for the condition, and then curly braces (`{}`) for the block of code to be executed when the condition inside the parentheses matches:

```js
if (condition is true) {
  statement here..
}
```

Here is another example of an if statement in action. Imagine you have a carnival ticket admission discount price for children below the age of 10. You can write an if statement like this:

```js
let price = 20
let age = 9
if (age < 10) {
  price = 15;
  console.log(`The price of the ticket for children below 10 is ${price} USD`);
}
```

Try to run the code and then change the value of age to be 10 or higher, and the code inside the curly brackets won't be executed.

## The `else` keyword

You have the discount code setup above, but it could be better if you can have another code block that logs the price of the normal ticket when age is 10 or above. You can write another if statement for that, but let's use this opportunity to learn about the `else` keyword.

The _else statement_ is a part of the control flow that will execute only when the if condition prior to it evaluates to `false`. Here is an example:

```js
let price = 20
let age = 15
if (age < 10) {
  price = 15;
  console.log(`The price of the ticket for children below 10 is ${price} USD`);
} else {
  console.log(`The price of the ticket is ${price} USD`);
}
```

In this case, the age is not below 10, so the if statement evaluates to `false` and the else statement is executed by JavaScript. By using both `if` and `else` statement, you can create multiple conditionals based on the evaluation of the code inside the `if` statement. Let's say you still have another discount for children aged 5 or below. You can write the code like this:

```js
let price = 20
let age = 5
if (age <= 5) {
  price = 12;
  console.log(`The price of the ticket for children aged 5 or below is ${price} USD`);
} else if (age < 10) {
  price = 15;
  console.log(`The price of the ticket for children below 10 is ${price} USD`);
} else {
  console.log(`The price of the ticket is ${price} USD`);
}
```

There you go! JavaScript will execute the right block of code based on the value of the `age` variable. you can create as many else if condition as required, but there must only be one else condition.

## Code exercise

The Byte Shop is offering special discount for customers who bought multiple computers at the following condition:

* Buy 1 computer for 200 USD
* Buy 2 computer for 195 USD each
* Buy 3 computer for 190 USD each

Write a small program that outputs the price of the computer based on the amount of computers being purchased. Here is an example output:

```shell
You bought 3 computers at the price of 190 USD each, so the total is 570 USD.
```