# Part 1 project and summary

## Part 1: A Cash Register Machine

Let's build a cash register machine that can accept add items to shopping cart, calculate total price, calculate discount and accept payment by cash.

The currency is assumed in USD but you don't have to worry about it.

The cash register has 3 items for sale:

* iPhone 6 for 300
* iPhone 7 for 400
* Samsung Galaxy S7 for 150

There's a 10% discount when the _total price is higher than 500_

Here's some hint for you. The Cash Register machine is an object with _3 properties_ and _3 methods_.

The 3 properties are:

* store name - string, has default value of the shop name
* items for sale - array of objects, store the name and price of items
* shopping cart - empty array

The 3 methods are:

* `addItem` - for adding items into the shopping cart. Accept one parameter `name`, and will use that `name` for looking up the item
* `calculateTotalPrice` - return the sum of price from the shopping cart. Accept no parameter
* `pay` - Accept one parameter for `amount` of cash given by the buyer. Use the amount from calculateTotalPrice and calculate the discount and the change

Here's an example of the cash register in action:

```js
cashRegister.addItem('iPhone 6'); // Adding iPhone 6 to your shopping cart
cashRegister.addItem('iPhone 7'); // Adding iPhone 7 to your shopping cart
console.log(cashRegister.calculateTotalPrice()) // 700
cashRegister.pay(700);

// Console log from pay method
// You get a 10% discount and your total price is 630
// Here's your 70 change
// Thanks for your purchase! Hope you come again
```

Use what you have learned about object, array, conditional and loop to build this project.

Good Luck!

## Part 1 summary

You have just finished the first part of learning JavaScript language. Congratulations! Now that you're familiar with JavaScript basics. Let's take your skills to the next level by learning how JavaScript interacts with web pages.

Since its inception, JavaScript was a language meant to add interactivity into web applications, so let's finally take all that you have learned about JavaScript into the real playground: the browser.