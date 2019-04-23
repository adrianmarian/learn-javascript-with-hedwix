# Operators

Operators are unique symbols that tells the computer to perform specific operations and produce a result. An example of operators are arithmetic operators, like additions `+` and multiplication `*`. There are 4 types of operators that is used widely in JavaScript code, they are:

1. Arithmetic operators
2. Assignment operators
3. Logical operators
4. Comparison operators

Let's see what they're all about

## Arithmetic operators

Arithmetic operators take numerical values and then produce a new number out of the operations being done. There are 10 arithmetic operators you can use to operate on number data types. They are:

|Name                      |Operation example        |Description                                                          |
|--------------------------|-------------------------|---------------------------------------------------------------------|
|Addition (`+`)            | `5 + 10`                | Returns the sum of the operands                                     |
|Subtraction (`-`)         | `7 - 2`                 | Returns the difference between two operands                         |
|Multiplication (`*`)      | `2 * 10`                | Returns the value of the multiplication between two operands        |
|Division (`/`)            | `15 / 3`                | Returns the value of the left operand divided by the right operand  |
|Remainder (`%`)           | `9 % 2`                 | Returns the remainder of the left operand after being divided by the right operand |
|Increment (`++`)          | `3++`                   | Returns the operand plus one           |
|Decrement (`--`)          | `10--`                  | Returns the operand minus one          |

All right, let's give JavaScript some real math quiz then, shall we?

```js
console.log(2 + 3 * 6 / 2);
```

Can you guess the answer? Now JavaScript prioritize arithmetic operations just as we do in real life. The priority ranks like this:

1. `*` Multiplication is done first
2. `/` Then division
3. `%` Remainder comes after
4. `+` Then addition
5. `-` Finally subtraction

So yes, the answer to the equation above is _11_. We also can separate concerns from the equation using round brackets `( )` once again, just like in maths.

```js
console.log((2 + 3) * (6 / 2));
```

This will make the answer becomes _15_.

Another thing to note: the increment and decrement operators can't be used.....

## Assignment operators

Assignment operators assign a value to the left operand from the value of the right operand. The simple assignment operator is the equal sign (`=`) that is commonly used to assign value to variable. Advanced assignment operators can combine assignment and arithmetic operations. They are called **shorthand operators**. Here are some of the most commonly used operators:

|Name                      |Operation example        |Meaning      |
|--------------------------|-------------------------|-------------|
|Assignment                | `x = y`                 | `x = y`     |
|Addition assignment       | `x += y`                | `x = x + y` |
|Subtraction assignment    | `x -= y`                | `x = x - y` |
|Multiplication assignment | `x *= y`                | `x = x * y` |
|Division assignment       | `x /= y`                | `x = x / y` |
|Remainder assignment      | `x %= y`                | `x = x % y` |

For the full list of assignment operators available in JavaScript, please visit the [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Expressions_and_Operators#Assignment_operators)

## Logical operators

Logical operators are used to find the `true` or `false` value between two or more values. They are described as follows:

|Name                      |Operation example        |Description                                                             |
|--------------------------|-------------------------|------------------------------------------------------------------------|
|Logical AND (`&&`)        | `true && true`          | Returns `true` if all operands are `true`, else returns `false`        |
|Logical OR (`||`)         | `false || true`         | Returns `true` if one of the operands are `true`, else returns `false` |
|Logical NOT (`!`)         | `!false`                | Reverse the result: returns `true` if `false`, and vice versa          |

These operators can be used on more than two values:

```js
console.log( true && true ) // returns true
console.log( true && true && false ) // returns false
console.log( false && true && false ) // returns false
console.log( false || true ) // returns true
console.log( false || true || false ) // returns true
console.log( false || false || false ) // returns false
console.log( !false ) // returns true
console.log( !true ) // returns false
```

Logical operators can be used outside of Boolean values, for example:

```js
console.log('Bird' && 'Owl') // returns Owl
```

But since the purpose of these operators are to find logical solution, it's very rare to see it being used for non-Boolean values.

## Comparison operators

Comparison operators compare the value of its operands. It then returns Boolean value `true` or `false` based on the result of the comparison. You can compare strings, numbers or objects with this operator type.

|Name                          |Operation example        |Description                                                             |
|------------------------------|-------------------------|------------------------------------------------------------------------|
|Equal (`==`)                  | `'know' == 'know'`      | Returns `true` if all operands are equal                               |
|Not equal (`!=`)              | `3 != 5`                | Returns `true` if the operands are not equal                           |
|Strict equal (`===`)          | `3 === 3`               | Returns `true` if all operands are equal and of the same type          |
|Strict not equal (`!==`)      | `3 !== '3'`             | Returns `true` if the operands are of the same type but not equal, or are of different type |
|Greater than (`>`)            | `4 > 2`                 | Returns `true` if the left operand is greater than the right operand              |
|Greater than or equal (`>=`)  | `'12' >= 10`            | Returns `true` if the left operand is greater than or equal to the right operand  |
|Less than (`<`)               | `2 < 10`                | Returns `true` if the left operand is less than the right operand                 |
|Less than or equal (`<=`)     | `3 <= 3`                | Returns `true` if the left operand is less than or equal to the right operand     |

The comparison operators will try to convert the operands into compatible type before doing the comparison. The strict comparison will allows you to compare two values without converting them first. Most of the time, comparison operators are used to compare between numbers, strings or Boolean value. It's almost never used for object comparison.

## Code exercise

Guess the result of these operators in action!

```js
console.log(19 % 3);
console.log(10 == 3);
console.log(10 !== '10');
console.log(2 < '10');
console.log('5' > 2);
console.log( false && true || false )
```