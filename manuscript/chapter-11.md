# Object data type

An object is one of JavaScript data type that allows you to store more than just one value at any given time. Think of a book, a person or a car.

A book usually have more than just one properties, it has a title, an author, and a selling price. If you write a book using regular variable, it would look like this:

```js
let bookOneTitle = 'Learn JavaScript With Hedwix';
let bookOneAuthor = 'Nathan Sebhastian';
let bookOnePrice = 10;

console.log(bookOneTitle);
console.log(bookOneAuthor);
console.log(bookOnePrice);
```

It's not the best way, and certainly need better organization! This is where object comes to the rescue. By using object, you can declare a single book object with multiple properties, each one to store the attribute of your book. Here is the same book but written using object:

```js
let book = {
  title: 'Learn JavaScript With Hedwix',
  author: 'Nathan Sebhastian',
  price: 10,
}

console.log(book.title);
console.log(book.author);
console.log(book.price);
```

The syntax for creating an object starts with curly braces, followed by property name, then property value. You can use a comma (`,`) to separate object that has more than one property.

```js
{
  [property name] : [property value],
}
```

## Object dot notation

An object property is accessed by using a _dot notation_. The syntax starts with the object variable name, then a dot (`.`) followed by the object property name. Here is an example of changing the book's title property:

```js
let book = {
  title: 'Learn JavaScript With Hedwix',
}

book.title = 'React Distilled';

console.log(book.title); // React Distilled
```

If the dot notation comes with a new property name that hasn't been assigned to the object, JavaScript will simply assign that new property name into the object:

```js
let book = {
  title: 'Learn JavaScript With Hedwix',
}

// adding price into the book
book.price = 10;

console.log(book.price); // 10
```

## Removing object property

You can remove an object property by using the `delete` keyword:

```js
let book = {
  title: 'Learn JavaScript With Hedwix',
  author: 'Nathan Sebhastian',
  price: 10,
}

delete book.price;

console.log(book.price); // undefined
```

You can add the same property name back into the object after you `delete` it just fine.

## Adding function to object and `this` keyword

An object property can also hold a function as its value, which you can call later using the same dot notation, but with parentheses because it's a function call.

```js
let car = {
  name: 'Mercedes-Benz',
  type: 'C-Class',
  start: function() {
    console.log (`The car engine is starting...`);
    console.log (`${this.name} is ready for a run!`);
  },
}

car.start();
```

The `this` keyword is commonly used in a function created inside an object to refer to the object in which the function is created, so in this case `this` equals the `car` object.

## Code exercise

Create a bird object with the following properties:

* name property - string
* species - string
* age - number
* address - string
* tweet - function to make the bird chirps with console log
* describe - console log the name, species, age and address of the bird

Here is an example of the result:

```js
bird.describe();
// prints "Hedwix is a 4 years old Eurasian Eagle Owl that lives in Fridian Forest"

bird.tweet();
// prints "Hoo-hoo-hoo!"
```