# Class

The `class` syntax of JavaScript is inspired from object oriented programming paradigm, in which a class is an abstract concept that is used to create one or more objects that have similar data and functions. For example, let's take two Human objects: a male named 'Eric' and a female named 'Susan'.

Eric and Susan are both an `object` of class `Human` with similar properties, but different values. For example, the `gender` property in object Eric is `male`, while for Susan it's `female`. The same can be said of the property `age`. Both humans have `age` property, but their value can be different.

With object syntax, we can create these two human objects like this:

```js
const eric = {
  name: 'Eric',
  age: 25,
  gender: 'male',
  greeting: function() {
    console.log(`Hello! I'm a ${this.age} years old human ${this.gender} and my name is ${this.name}.`);
  }
}

const susan = {
  name: 'Susan',
  age: 17,
  gender: 'female',
  greeting: function() {
    console.log(`Hello! I'm a ${this.age} years old human ${this.gender} and my name is ${this.name}.`);
  }
}
```

While this example works, you can see how these two humans are very similar, and the code is very repetitive. Programming language has loop statement to avoid repeating code over and over again. Is there a way to avoid repeating object creation? Sure there is. This is where `class` keyword comes in.

First, let's create a `class` named `Human`. A `class` name starts with a Capital letter and then followed by CamelCase format:

```js
class Human {
  constructor(name, age, gender) {
    this.name = name;
    this.age = age;
    this.gender = gender;
    this.species = 'human';
  }

  greeting() {
    console.log(`Hello! I'm a ${this.age} years old human ${this.gender} and my name is ${this.name}.`);
  }
}
```

A `constructor` is an optional method, but when it is added to a class, it will be called every time an object is created from the class. Any argument passed into the object creation will be received by the `constructor`. To create an object from the `Human` class, use the `new` keyword followed by class name and parentheses containing its arguments (if any):

```js
const eric = new Human('Eric', 25, 'male');
const susan = new Human('Susan', 17, 'female');

console.log(eric.name);
console.log(eric.age);
console.log(eric.gender);
eric.greeting();
susan.greeting();
```

Now both `eric` and `susan` variable is an object created from the `Human` class. These new human objects have access to their own properties (`name`, `age`, `gender`, `species`) and methods (`greeting`).

Notice that the species property is slightly different than the rest. While `name`, `age` and `gender` properties get their values from the arguments passed into the class, `species` property is assigned the string `human` by the class code itself. This is perfectly okay.

And that's what `class` concept is all about. It creates an abstract representation of objects that can be used over and over again _to create objects that has similar properties and methods, but different in values_.

## Creating A Child Class

A child class of a `class` can be created by using the `extends` keyword:

```js
class Doctor extends Human {

  examine() {
    console.log ("I'm examining the patient...")
  }

}
```

The class that `extends` another class is called a subclass or a child class, whichever you liked best. In the example above, the `Doctor` class is the child class of `Human` class. That makes `Human` a parent class to the `Doctor` class. A child class has all the methods its parent class has. This means the object created from `Doctor` class can also call on `greeting` method, even though there is no `greeting` method in the `Doctor` class:

```js
const eric = new Doctor('Eric', 25, 'male');

eric.greeting();
```

If the child class `Doctor` has the same `greeting` method as the `Human` class, the object created from `Doctor` will run the `greeting` method of `Doctor` class instead of `Human` class. This process is called _method overriding_:

```js
class Doctor extends Human {

  greeting() {
    console.log(`Hello! I'm a ${this.age} years old Doctor and my name is ${this.name}.`);
  }

}
```

The `this` keywords in `Doctor` class works because the `Human` class `constructor` method is executed when the new Doctor object is created. In the same way you override `greeting` method, you can also override the `constructor method`:

```js
class Doctor extends Human {

  constructor(name, age, specialty) {
    super(name, age);
    this.specialty = specialty;
  }

  greeting() {
    console.log(`Hello! I'm a ${this.age} years old ${specialty} and my name is ${this.name}.`);
  }

}

const eric = new Doctor('Eric', 25, 'Dentist');
eric.greeting();
```

The `constructor` method in the `Doctor` class changed the parameters from `name, age, gender` into `name, age, specialty`. This act of creating a child class is known as [Class Inheritance](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Objects/Inheritance) concept.

## Code exercise

Create a new class named `Robot` with the following 2 properties and 2 methods.

The properties of `Robot` class are:

* name - for the robot's name.
* remaining energy - remaining energy for the robot to do something. Starts at 15.

The methods of `Robot` class are:

* `doWork` - do a work and reduce energy by 1
* `doRecharge` - recharge its energy by 2

Then create a new class `Android` that `extends` from `Robot` class with a new property called `tasks`, which is an array of string for storing available tasks to get done.

Two methods will be added to this class:

* `addTask` - add a new task to the `tasks` array. Accept one parameter `taskName` for adding the task.
* `doTask` - complete the task and reduce energy level by 1. This method also remove a task from the `tasks` array.

Here's an example of an object created from `Android` class:

```js
const kara = new Android('Kara', ['Do the dishes']);

kara.addTask('Do the dishes'); // The task Do the dishes is already saved in the task list
kara.addTask('Clean the bedroom'); // Clean the bedroom is added to the tasks list
kara.doTask('Do the dishes'); // Do the dishes has been done! One energy is being used for work
console.log(`Remaining energy: ${kara.remainingEnergy}`); // Remaining energy: 14
kara.doRecharge(); // Energy is recharged by 2
console.log(`Remaining energy: ${kara.remainingEnergy}`); // Remaining energy: 16
```

For the methods `addTask` and `doTask`, you will need to use array special methods. Can you guess the methods you need for it?