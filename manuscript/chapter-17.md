# Handling events

JavaScript can be used to add interactions into HTML page by responding on user's actions. You can write code that listens for specific user actions, like clicking an HTML button or moving mouse over to a text, and then do something when it does happens.

## Adding event listener

Using JavaScript, you can add listener to certain objects by using the `addEventListener` keyword. This keyword will setup a listener for a specific event, and then executes a function when the event is triggered. For example, let's add an event listener that listens when the mouse is being clicked:

```js
document.addEventListener('click', function(event){
  console.log('The mouse is clicked!');
});
```

The code above attached a listener to the document object, which means you can click the mouse anywhere inside the browser content screen to trigger it.

If you want to add a listener to specific element node, you can select the node with query selector first:

```js
let myHeader = document.querySelector('#header');
myHeader.addEventListener('click', function(event){
  console.log('The mouse is clicked on the HEADER!');
});
```

Now the code above will run only when the mouse is clicked inside `myHeader` element. Event listeners in JavaScript can listen to so many events created by the browser. Let's learn about the most common events in this chapter.

## Mouse events

The mouse events are triggered when any input is being send from the user through the mouse. You have learned one of the most common mouse event through the example code from previous section, which is the `click` event. You can also listen when the mouse hovers over a certain element node and then do some style change:

```js
let myBookList = document.querySelector('.book-list');
myBookList.addEventListener('mouseenter', function(event){
  myBookList.style.fontSize = '70px';
});

myBookList.addEventListener('mouseleave', function(event){
  myBookList.style.fontSize = '30px';
});
```

## Keyboard events

A keyboard event is triggered when the keyboard button gets pressed by the user. For example, let's set the listener to listen for when a user press any button by creating a log on the console:

```js
document.addEventListener('keydown', logKey);

function logKey(event) {
  console.log(event.code);
}
```

To listen only for specific keyboard input, you can first check on the value of the code. For example, let's listen to the `Z` button `keydown` event. Using the logger function above, you know that the value of `code` property in `event` object of the `Z` button is `KeyZ`. That means you can create a conditional `if` code block for checking the value:

```js
function logKey(event) {
  if (event.code == 'KeyZ'){
    console.log('The Z Button is pressed!');
  }
}
```

For listening when a keyboard button is released, you can set the listener to listen to the `keyup` event:

```js
document.addEventListener('keyup', logKey);
```

The `logKey` function will work exactly the same way.

## Code exercise

You need to add event handlers for the following HTML page. You can copy and paste the HTML code below:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JavaScript in the Browser</title>
</head>
<body>
  <h1 style='font-size:32px;'>Lorem ipsum dolor sit amet, consectetur adipiscing elit</h1>
  <p>Vestibulum non nibh vel risus molestie vestibulum ac at odio</p>
  <button>Increase header font size</button>
  <button>Decrease header font size</button>
  <script src="index.js"></script>
</body>
</html>
```

Write JavaScript code for the HTML page below with the following functionalities:

* When the mouse is over the header element, change its text color to red.
* When the mouse clicked on a paragraph element, remove the element from the document.
* In the event where button 'L' is pressed on the keyboard, add a new `<p>` element to the page just below the `<h1>`.
* In the new paragraph, write "Vestibulum dictum at quam non tempor"
* Add event handlers to increase and decrease header font size in the respective buttons.

You can add class attributes to the starting page as you see fit.

Note that each time you add a new `<p>` element into the HTML, you need to apply the 'click' event handler into the new element. It might be a good idea to make a function to do just that, and call it from 'L' button event handler.