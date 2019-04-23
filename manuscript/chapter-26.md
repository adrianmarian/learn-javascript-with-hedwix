# The Math object {#math-object}

The `Math` object is a special JavaScript object designed to perform mathematical tasks on number data type.

For example, let's say you want to round a number with floating point like `7.7` to `8`. You can do so using `Math.round()` function:

```js
let myNumber = Math.round(7.7);
console.log(myNumber); // 8
```

And that's really everything there is to the `Math` object. It has methods that you can call to perform mathematical tasks like rounding a number, getting a random number, calculating the square root of a number, and so on.

Here are some of the most commonly used Math methods:

To round a number up to its nearest integer, use `Math.ceil()`

```js
let myNumber = Math.ceil(5.1);
console.log(myNumber); // 6
```

To round a number down, use `Math.floor()`:

```js
let myNumber = Math.ceil(5.9);
console.log(myNumber); // 5
```

To random a number between 0 and 1, use `Math.random()`:

```js
console.log(Math.random()); // can be like 0.2536996216083194
```

Now this random method will need some extra explanation. Since it returns a number between 0 and 1, how can you use it to random between, say, 50 to 100?

In order to random integer number using the `Math.random()` method, you have to scale the result of the method to the desired range by calculating the range between the maximum range and the minimum range, then add the numbers up to the minimum, and finally use `Math.floor()` to round the number down.

```js
// return random number between 50 - 99
let randomBetweenFiftyAndHundred = Math.floor(Math.random() * (100 - 50)) + min;
console.log(randomBetweenFiftyAndHundred);
```

Note that `Math.random()` is exclusive of 1. That means it will return a random number from 0 to 0.99 maximum, but will never return 1. Thus the random between 50 - 100 will never return 100. If you want to include the maximum range into the random, you can add a `+1` between the range:

```js
// inclusive of 100 with +1
let randomBetweenFiftyAndHundred = Math.floor(Math.random() * (100 - 50 + 1)) + min;
console.log(randomBetweenFiftyAndHundred);
```

Here is the full explanation of [getting random number](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math/random#Getting_a_random_integer_between_two_values_inclusive) between two integers.

For the full list of available Math constant and methods, refer to [this](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Math#Description) documentation.