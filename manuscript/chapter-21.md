# Accessing Node.js's API

Although you have ran many scripts using Node.js in Part 1 of this book, you haven't learned anything at all about what makes Node.js such a great invention. Can Node.js do something more than simply running JavaScript code? The answer is absolutely yes! Node.js comes with JavaScript modules that you can use to build a web server.

In fact, the `live-server` package that you have installed before for creating a local web server makes use of Node.js's modules. This collection of modules are better known as Node.js's API, and it is documented at Node.js documentation [site](https://nodejs.org/api/documentation.html).

Rather than trying to cover all of Node.js's capabilities, some of which are too advanced and unnecessary for creating web applications, I'm going to cover the most essential part for creating a simple API endpoint that you can use to get information for your website.

You have learned how to use APIs in part two of this book. Now let's create one!

## Creating Node.js server with HTTP module

In order to create a web server that you can send HTTP request to, you will need to use Node.js's `http` module. This module allows you to create a server and then send response based on the request URL. Here is how you create a server with Node.js and `http` module:

```js
const http = require('http');

const server = http.createServer((req, res) => {
  res.setHeader('Access-Control-Allow-Origin', '*');
  if (req.url === '/api') {
    let data = {
      data: [
        {
          id: 1,
          title: 'Learning JavaScript',
          description: "Let's learn JavaScript programming language!",
        },
        {
          id: 2,
          title: 'Learning React',
          description: "Let's learn React library!",
        },
      ]
    };
    let response = JSON.stringify(data);
    res.end(response);
  }

  if (req.url === '/api/test') {
    console.log('sending the data now..');
    let data = {
      data: [
        {id: 1, title: 'Test Driven Development'},
        {id: 2, title: 'Unit Testing'},
      ]
    };
    let response = JSON.stringify(data);
    res.end(response);
  }
});

server.listen(3000);
console.log('Node.js server is up at port 3000');
```

The code above creates two different response based on the URL of the HTTP request. If it is `http://127.0.0.1:3000/api`, you will get the `data` array as response. If it's `http://127.0.0.1:3000/api/test`, you will get the `test` array as response. To test this server, you can use the browser and go to the specified URL above.

Now that you have a server ready to send response, let's create HTML document with JavaScript code that will request data from this server.

## Fetching data from Node.js server

Let's add two HTML buttons and add event listeners for click events. When a button is clicked, the event listener will respond by fetching the data from the server and insert it as HTML `<li>` element into your web page:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Node API Example</title>
</head>
<body>
  <button id='btn-load'>Load API data</button>
  <ul id='response'></ul>
  <button id='btn-load-test'>Load API <code>/test</code> route</button>
  <ul id='response-test'></ul>
  
  <script src="index.js"></script>
</body>
</html>
```

```js
let btnLoad = document.querySelector('#btn-load');
let responseList = document.querySelector('#response');
let btnLoadTest = document.querySelector('#btn-load-test');
let responseListTest = document.querySelector('#response-test');

btnLoad.addEventListener('click', function() {
  fetch('http://127.0.0.1:3000/api').then(function(res) {
    res.json().then(function(response) {
      console.log('This is the array of JSON objects: ', response.data);
      response.data.forEach(element => {
        responseList.insertAdjacentHTML(
          'beforeend',
          '<li>' + JSON.stringify(element) + '</li>'
        );
      });
    });
  });
});

btnLoadTest.addEventListener('click', function() {
  fetch('http://127.0.0.1:3000/api/test').then(function(res) {
    res.json().then(function(response) {
      console.log('This is the array of JSON objects: ', response.data);
      response.data.forEach(element => {
        responseListTest.insertAdjacentHTML(
          'beforeend',
          '<li>' + JSON.stringify(element) + '</li>'
        );
      });
    });
  });
});
```

And there you have it. When the `fetch` method returns a response, you can then call on the `json()` method to transform the string response into an array of objects. Then you insert `stringified` object into HTML document `forEach` element in the array.

## Sending a POST request

In order to send a post request with `fetch`, you need to add a second argument to your `fetch` call which contains an object of request options. For example, you can add the `method`, the `body` request which commonly store the data, and the `headers` of the request:

```js
fetch('http://127.0.0.1:3000', {
  method: 'POST',
  body: JSON.stringify(data),
  headers:{
    'Content-Type': 'application/json'
  }
}).then(function(res) {
  res.json()
  .then(function(response){
    console.log('Success:', JSON.stringify(response)
  })
  .catch(function(error){
    console.log('Error:', error)
  });
})
```

You can then check for a request with `POST` method in your Node.js HTTP server:

```js
// Handling a CORS POST request
const http = require('http');

const server = http.createServer((req, res) => {
  res.setHeader('Access-Control-Allow-Origin', '*');

  if(req.url == '/'){
    res.end('Server is up and ready');
  }

  if(req.method === 'POST'){
    let response = { data: 'POST request OK' };
    res.end(JSON.stringify(response))
  }
});

server.listen(4000);
console.log('Node.js server is up at port 4000');
```

This should work, but a POST request in web application will always trigger a [preflight request with OPTIONS method](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS#Preflighted_requests_in_CORS) to the server first. This OPTIONS method is sent so that the server can see what data or structure that the request wants to send and decide to accept it or not. The POST request will not be send by the browser until it accepts a response from the server for the OPTIONS request.

This means that unless your Node.js server send a response to the preflight OPTIONS request, the POST request will never reach the server. To handle this, you need to add another `if` conditional for a request with OPTIONS method. You don't need to send any data back to the browser, just a header with 200 OK response is enough:

```js
// Handling a CORS POST request
const http = require('http');

const server = http.createServer((req, res) => {
  res.setHeader('Access-Control-Allow-Origin', '*');

  if(req.url == '/'){
    res.end('Server is up and ready');
  }

  // add a condition for request with OPTIONS method

  if (req.method === 'OPTIONS') {
    // from https://gist.github.com/nilcolor/816580
    var headers = {};
    headers["Access-Control-Allow-Origin"] = "*";
    headers["Access-Control-Allow-Methods"] = "POST, GET, PUT, DELETE, OPTIONS";
    headers["Access-Control-Allow-Credentials"] = false;
    headers["Access-Control-Max-Age"] = '86400';
    headers["Access-Control-Allow-Headers"] = "X-Requested-With, X-HTTP-Method-Override, Content-Type, Accept";
    res.writeHead(200, headers);
    res.end();
  }

  if(req.method === 'POST'){
    let response = { data: 'POST request OK' };
    res.end(JSON.stringify(response))
  }
});

server.listen(4000);
console.log('Node.js server is up at port 4000');
```

This way, the Node.js server will know how to respond to a request with OPTIONS method, which enable the browser to send a POST request.

## Code exercise

Create a simple Node.js server that returns a random string from the following array. This array is a list of puns taken from the following Reddit [thread](https://www.reddit.com/r/dadjokes/comments/76jfme/a_giant_list_of_puns/).

* The Node.js server has one route: the `/api` route and returns a single pun from the array as a response
* Use the [Math object](#math-object) to help you in sending a random pun from the array
* Your HTML page need to have a single button that fetch another request to get another pun from the server

Here is the array that you can use in your Node.js server:

```js
const PUNS = [
  "Why did the cookie cry? Because his father was a wafer so long!",
  "I used to work in a shoe recycling shop. It was sole destroying.",
  "What do you call a belt with a watch on it? A waist of time.",
  "I cut my finger chopping cheese, but I think that I may have greater problems.",
  "My cat was just sick on the carpet, I don’t think it’s feline well.",
  "Why did the octopus beat the shark in a fight? Because it was well armed.",
  "How much does a hipster weigh? An instagram.",
  "What did daddy spider say to baby spider? You spend too much time on the web.",
  "Atheism is a non-prophet organisation.",
  "There’s a new type of broom out, it’s sweeping the nation.",
  "Did you hear about the guy who lost the left side of his body? He's alright now.",
  "A cross eyed teacher couldn’t control his pupils.",
  "After the accident, the juggler didn’t have the balls to do it.",
  "I used to be afraid of hurdles, but I got over it.",
  "To write with a broken pencil is pointless.",
  "I read a book on anti-gravity. I couldn’t put it down.",
  "I couldn’t remember how to throw a boomerang but it came back to me.",
  "What should you do if you are cold? Stand in the corner. It’s 90 degrees.",
  "How does Moses make coffee? Hebrews it.",
  "The energizer bunny went to jail. He was charged with battery.",
  "What did the alien say to the pitcher of water? Take me to your liter.",
  "Why shouldn’t you trust atoms? They make up everything.",
  "What’s it called when you have too many aliens? Extraterrestrials.",
  "Want to hear a pizza joke? Nevermind, it’s too cheesy.",
  "What do cows tell each other at bedtime? Dairy tales.",
  "Why can’t you take inventory in Afghanistan? Because of the tally ban.",
  "Why didn’t the lion win the race? Because he was racing a cheetah.",
  "What’s america’s favorite soda? Mini soda.",
  "Why did the tomato turn red? Because it saw the salad dressing.",
  "What kind of car does a sheep drive? Their SuBAHHru.",
  "What do you call a french pig? Porque.",
  "What do you call a line of rabbits marching backwards? A receding hairline.",
  "Why don’t vampires go to barbecues? They don’t like steak.",
  "How do trees access the internet? They log on.",
  "Why should you never trust a train? They have loco motives.",
  "Is your refrigerator running? Better go catch it.",
  "The future,the present and the past walked into a bar. Things got a little tense.",
  "I saw an ad for burial plots, and thought to myself this is the last thing I need.",
  "I wondered why the baseball was getting bigger. Then it hit me.",
  "Read enough of our funny puns, and you'll be punstoppable.",
  "Yesterday a clown held the door for me. It was a nice jester.",
  "The wedding was so emotional even the cake was in tiers.",
  "Imagine if alarm clocks hit you back in the morning. It would be truly alarming.",
  "Why is a skeleton a bad liar? You can see right through it.",
  "What do you receive when you ask a lemon for help? Lemonaid."
];
```