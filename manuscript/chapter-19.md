# Network request and asynchronous programming

In any modern website or web application, there is almost always an interaction that happens between two or more websites, requesting and sending data from one address to another. You might be already familiar with the term API or Application Programming Interface, which is just a fancy name of "how to talk with my web application".

That's right, unless you talk with a website in a certain way specified by the website's developer, the website won't respond properly and just give you errors instead. Let's learn how to talk with other websites in this chapter.

## Making network request

JavaScript has `fetch` method that can be used for requesting data from other internet address. Here is an example of fetch in action:

```js
fetch('https://salty-crow.glitch.me/api/days')
.then(function(response) {
  return response.json();
})
.then(function(myJson) {
  console.log(JSON.stringify(myJson));
});
```

The fetch method takes a URL address as its parameter, and handles the response being send from the URL using the `.then` chain method. What's a `.then` chain method? Good question, and to answer it, you need to learn about Asynchronous programming first.

## Understanding asynchronous programming

Asynchronous (async for short) programming is a code pattern that allows code execution to continue without waiting for the previous separate code execution to finish. To see it in action, run this JavaScript code using Node.js:

```js
function helloWorld() {
  setTimeout( function(){
    console.log('Hello World!');
  }, 2000);
}

helloWorld();
console.log('Learning Promise at the moment...');
```

In the code above, the log `Learning Promise at the moment...` will be printed out first, then `Hello World!` is printed. This is because JavaScript is asynchronous, which means even though the function `helloWorld()` isn't executed completely, the code below the function call is executed regardless.

If you want to make JavaScript "wait" until `helloWorld()` finished executing, and then execute on the second `console.log()`, you need to use the `Promise` object. Now what is a `Promise` object? A promise is a temporary value that will eventually resolve into a real value when code execution reaches its conclusion.

Here is a very simple example of promise that I can think of: imagine that you have a 9 year old kid, and to motivate him to do well in his test, you _promised_ to buy him a new PlayStation console if he gets an A on his English test.

Now your child will take your promise as a value, and if he can get an A, that promise will _resolve_ into a real, tangible, and valuable PlayStation console. If he gets a B or C, though, that promise is _nulled_, resolving into nothing.

This is how promise works in JavaScript. when a `Promise` is being returned by a JavaScript function, JavaScript will stop execution of code until the promise reach its conclusion, whether it is _resolved_ (success condition) or _rejected_ (fail condition). Here is the new `helloWorld()` function that returns a `Promise`:

```js
function helloWorld() {
  return new Promise(function(resolve, reject){
    setTimeout(function() {
      console.log('hello world!');
      resolve();
    }, 2000);
  });
}
  

helloWorld().then(function(){
    console.log('Learning Promise at the moment...')
  }
)
```

With the code above, JavaScript will wait for the `new Promise` object to reach its conclusion, whether it be `resolve()` or `reject()`. Resolve means the promise is a success and , while `reject()` means there is something wrong with the request. In order to run code when a promise ends with `resolve()`, you use the `.then()` chain method.

When a promise ends with `reject()`, you use the `.catch` chain method. Note that the `setTimeout()` function here is not a part of the `Promise` object. It's a special JavaScript function that you can use to delay the execution of code for a specified time in milliseconds. In this case, 2000 milliseconds or 2 seconds.

```js
// setTimeout syntax
setTimeout([function to run], [time to delay in milliseconds]);
```

Now you understand about asynchronous programming and how `Promise` can be used to "wait" until a code block finished executing.

This is what happens when you call on the `fetch` method. It returns a new `Promise` object, and when JavaScript sees that it's a `Promise`, it will wait until that promise reach its conclusion. What to do with the value returned by promise is up to you as the developer. Here is the example code, using the test grade promise:

```js
function buyPlaystation(testGrade) {
  return new Promise(function(resolve, reject){
    console.log('Calculating grade...');
    setTimeout(function() {
      if (testGrade === 'A'){
        resolve();
      }
      reject();
    }, 2000);
  });
}
  

buyPlaystation('A')
.then(function(){
  console.log("You're getting a new PlayStation!");
})
.catch(function(){
  console.log("You didn't get an A, so study better next time!");
})
```

That will be all about async programming and the `Promise` object. And this is what happens when you call on `fetch` method.

## Displaying the result of network request

Now that you understand about `fetch`, it's time to display the result of your API call into your web page display. The common response from an API URL is to return a text of JSON object.

JavaScript has a method to transform this text using the `.json()` method, which returns another `Promise`. This `Promise` object will resolve when `.json()` finished reading the text and parsing it into JSON, returning a JSON object that you can manipulate as you need for your web application.

Let's first create HTML page for making network request:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Fetch Example</title>
</head>
<body>
  <h1>Let's learn about fetch!</h1>
  <ul id='list'>
  </ul>
  <button id='months'>fetch the name of months</button>
  <button id='days'>fetch the name of days</button>
  
  <script src="fetch-example.js"></script>
</body>
</html>
```

Then create a new `fetch-example.js` file with code for making network request on button click. You can use the API address that I have created for this tutorial:

* `https://salty-crow.glitch.me/api/days`
* `https://salty-crow.glitch.me/api/months`

Create a `fetch` request matching the API address and the button id:

```js
document.getElementById("months").addEventListener("click", function(event){
  fetch('https://salty-crow.glitch.me/api/months')
  .then(function(response) {
    return response.json();
  })
  .then(function(data) {
    insertDataToList(data);
  });
});

document.getElementById("days").addEventListener("click", function(event){
  fetch('https://salty-crow.glitch.me/api/days')
  .then(function(response) {
    return response.json();
  })
  .then(function(data) {
    insertDataToList(data);
  });
});
```

Finally, when the data is ready, insert it into the HTML page using `insertAdjacentHTML` method. Since both data send by the API is similar, you can create a single method for both data:

```js
const LIST = document.getElementById('list');

function insertDataToList(data){
  while(LIST.hasChildNodes()){
    LIST.removeChild(LIST.firstChild);
  }
  data.items.map(function(item){
    LIST.insertAdjacentHTML('beforeend', `<li>${item}</li>`);
  })
}
```

You can now fetch data and display it into your HTML page. Go give it a try!

## Code exercise

Create a new web page with a button to fetch data from `https://salty-crow.glitch.me/api/countries` and display its results. You can go to the link and see what data structure is being used by this API.