# Loop statements

In creating a computer program, there are bound to be code that needs to be executed repeatedly. Loop statement is a code statement that executes again and again until (or while) a certain condition is met.

Let's say you want to write a program that "prints number 1 to 10 into the console". You can do it by using `console.log` 10 times:

```js
console.log(1);
console.log(2);
console.log(3);
console.log(4);
console.log(5);

// and so on..
```

It works, but there is a better way to write this kind of repetitive code. With the loop statement `for`, you can write it like this:

```js
for ( x = 1; x < 11; x++) {
  console.log(x);
}
```

There you go! A `for` statement is followed by a parentheses (`()`) which contains 3 expressions:

* Initialization expression, where you declare a variable to be used as the source of the loop condition
* Condition expression, where the variable in initialization will be evaluated for a specific condition
* Arithmetic expression, where the variable value is either incremented or decremented by the end of each loop

After these expressions, the curly brackets (`{}`) will be used to mark the code that will be executed as long as the condition expression is `true`. You can identify which expression is which by paying attention to the semicolon (`;`) which ends the statement.

```js
for ( [initialization]; [condition]; [arithmetic expression]) {
  // begin execution ..
}
```

The arithmetic expression can be an increment (`++`) or a decrement (`--`) or a shorthand arithmetic operators like `+=` and `-=`. It is run once each time the execution of the code inside the curly brackets end:

```js
// for statement with decrement expression
for ( x = 10; x >= 1; x--) {
  console.log(x);
}

// divider just for easier reading in the console
console.log('===============');

// for statement with shorthand arithmetic expression
for ( x = 1; x < 20; x+=3) {
  console.log(x);
}
```

## The `while` loop

The `while` statement is an alternative loop statement that can be used to execute repetitive task, and the syntax goes like this:

```js
let x = 1;
while (x < 11) {
  console.log(x);
  x++;
}
```

A `while` statement is followed by a parentheses (`()`) for the condition, and while the condition is `true`, it will run the code inside the curly brackets (`{}`).

Please note that inside the `while` statement block there is an increment operation executed

```js
x++
```

This is so that the while condition evaluation can return `false` and stop the while statement from executing forever.

## The do..while loop

Sometimes, you want to execute a code at least once regardless if the while condition evaluates to `true` or `false`. A Do..While loop statement ensures that a code will be executed once before checking on the conditional:

```js
let i = 2;
do {
  console.log(i);
  i++;
} while ( i < 1);
```

The above example will execute the code block inside `do` statement once, even though the condition is already `false` because the variable `i` is `2`, which is already greater than `1`.

## Code exercise

Write a small piece of program that prints all even numbers from 1 to 50

Then write another program to print a half triangle using the asterisk (`*`). Here is the result:

```shell
*
**
***
****
*****
```

Then print a reversed half triangle next:

```shell
*****
****
***
**
*
```

Hint: for both cases, the number of the loop is _5_.