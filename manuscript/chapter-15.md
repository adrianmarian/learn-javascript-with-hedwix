# Use of JavaScript in the browser

There are 3 main technologies used to create web pages. They are HTML, CSS and JavaScript.

HTML is a markup language consisting of tags that gets rendered in the browser. It is used to describe the structure of a web page.

CSS is used to make the web page rendered by the browser more attractive. It enables you to change the font style and size, adding space between texts, resize pictures and create borders, and many more.

JavaScript, on the other hand, enables web page to request information from the user, render dynamic content and "talk" to other web application. In this second part of the book, you will learn how to use JavaScript to do just that.

Let's continue with setting up a local web server in order to code JavaScript in the browser.

Oh, and a note for the browser: All examples and exercise in this book will use Google Chrome browser, because I personally use it for development and testing. Although it should be okay to follow along using Safari and Firefox, I'd like to recommend you to use Chrome too. There might be some features that are not available in another browser, such as typing autocomplete in the browser console.

## Setting Local Web Server Using Node

To run a local web server in your computer, let's install the `live-server` package from NPM registry. Open a command line window and type the following command:

```shell
npm install -g live-server
```

Create a new directory so that you can put all of your new web application files in one place:

```shell
mkdir chapter-15 && cd chapter-15
```

Inside the directory, create a new HTML, CSS and JavaScript file. You can use the template below:

```shell
touch index.html && touch index.css && touch index.js
```

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>JavaScript in the Browser</title>
  <link rel="stylesheet" href="styles.css">
</head>
<body>
  <h1 id='header'>Hello World!</h1>
  <p id='tagline'>This is my HTML page</p>
  <div id='content'>
    <h2 id='series-name'>The Harry Potter Series</h2>
    <p id='series-description'>The list of Harry Potter Book Series.</p>
    <ul class="list">
      <li class="list-item">The Sorcerer's Stone</li>
      <li class="list-item">The Chamber of Secrets</li>
      <Li class="list-item">The Prisoner of Azkaban</Li>
      <Li class="list-item">The Goblet of Fire</Li>
      <li class="list-item">The Order of the Phoenix</li>
      <li class="list-item">The Half Blood Prince</li>
      <li class="list-item">The Deathly Hallows</li>
    </ul>
  </div>
  <script src="index.js"></script>
</body>
</html>
```

```css
body {
  background-color: #ffeedd;
  font-family: sans-serif;
}

#header {
  font-size: 32px;
}

#tagline {
  font-size: 14px;
  font-style: italic;
}

#content {
  background-color: #ffffee;
}
```

```js
console.log('Hello World!');
console.log('Studying JavaScript in the Browser...');
```

To run the `live-server`, simply type `live-server` followed by the name of the directory:

```shell
live-server chapter-15
```

The server will run on `http://127.0.0.1:8080` and your browser will automatically open the address.

## Running JavaScript in the Browser

Open Chrome Browser Debugger by pressing F12 in the active tab. Once up and running, click on the _Console_ tab.

Your `index.js` is running in the browser. Great!

This Console tab is the browser console, from which you can type JavaScript code to manipulate the appearance of a website. Unlike the first part where you code in a `.js` file and run it using Node.js, you're going to type JavaScript code into the browser from here.

## Refresher on HTML and CSS

I'm confident that you will have no problem with HTML and CSS knowledge needed to continue learning JavaScript in this book. But in case you need a refresher, there is a great HTML and CSS introduction tutorial available for free here:

* [HTML Basic Web Pages](https://internetingishard.com/html-and-css/basic-web-pages/)
* [Hello CSS](https://internetingishard.com/html-and-css/hello-css/)

When you're ready, Let's move into the next chapter to learn about the DOM.