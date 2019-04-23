# Switch case conditional

If statement is great, but if you have more than two if statements, maybe it's time to use **`switch` statement** instead. Just like `if` statement, switch statement is used to control the flow of a program. It evaluates a value, but instead of using `if`, it will use the `case` keyword. Here is an example of switch statement in action:

```js
let age = 15;
switch (age) {
  case 10:
  console.log ('Age is 10');
  break;
  case 20:
  console.log ('Age is 20');
  break;
  default:
  console.log ('Age is neither 10 or 20');
}
```

The `switch` statement takes the variable in the parentheses (in this case, age) and then tries to match it with the provided `case` statements. If the variable value founds a matching `case`, the statements associated with the `case` will be executed.

A `break` keyword is used to break out of the switch evaluation, and it's common to use it at the end of `case` statements to prevent the execution of statements _following a match_. Let's try to omit these `break` keywords so that you understand what I mean:

```js
let age = 10;
switch (age) {
  case 10:
  console.log ('Age is 10');
  case 20:
  console.log ('Age is 20');
  default:
  console.log ('Age is neither 10 or 20');
}
```

Run the code, then change the `age` variable to 20, then 25. JavaScript will execute all statements following the matching case without the `break` keyword.

One thing you might note is that the `case` keyword can only evaluates a very specific value, like `true` or `10`, while `if` statements allow the use of comparison in its conditional, like `age > 10`.

Each control flow statement is situational, but one key point to note is that for **very specific conditional**, use the switch statement. For **conditional that allow comparison**, use the if statement.

## Code exercise

Create a school's first grade test score grading system which give the following rewards:

* Students that got an A will get the Ironman sticker
* Students that got a B will get the Captain America sticker
* Students that got a C will get the Spiderman sticker

Example output:

```shell
You got an A, so here is an Ironman sticker for you!
You got a B, so here is the Captain America sticker for you!
You got a C, study better and here is your Spiderman sticker!
```