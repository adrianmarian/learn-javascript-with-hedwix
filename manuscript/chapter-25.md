# The proper guide to semicolon in JavaScript

Semicolons in JavaScript may seem like optional on the surface, but under the hood, they really aren't.

The debate about semicolons in JavaScript has been on going for years. Some people might say that JavaScript is language that does not need a semicolon to end a statement, but that is not true at all. JavaScript has a mechanism to include semicolon in order to end statements automagically when the code is executed. This mechanism is called **Automatic Semicolon Insertion**.

## Rules of automatic semicolon insertion

The JavaScript engine will automatically add semicolons during the parsing of the code, if it finds these specific conditions:

  1. When the next line starts with a closing braces `}` , closing the current block
  2. when there is a `return` statement without a semicolon
  3. when there is a `break` statement without a semicolon
  4. when there is a `throw` statement without a semicolon
  5. when there is a `continue` statement without a semicolon
  6. when the final statement of the code is reached

An example of Automatic Semicolon Insertion can't be seen, since it was added during the parsing, but we can show some example code where it will play a role. Consider the following code:

```js
  let example = true;
  if(example) {
    console.log('B is truthy') // there will be a semicolon insertion here
  }
```

Also be careful with the statements that automatically insert semicolon like return, break, throw and continue. Consider this example:

```js
  return // JS will insert semicolon here, effectively returning undefined
  {
    name : "Hedwix"
  }
  // the object will not be returned
```

In order to return the object, you'll need to add the opening curly bracket `{` in the same line as the return statement. As long as you didn't code in an eccentric fashion, you'll be fine to omit semicolons in your source code entirely. Some people vote for inserting semicolons themselves without depending on the Automatic Semicolon Insertion, and I'd say I agree with them. Adding the mechanic to insert semicolon into the code means that JavaScript need those semicolons. If that's so, I prefer to add it myself rather than depending on the parser.

I also looked at popular open source projects like React and Vue. It turns out that React developers still include semicolon in their source, while Vue developers don't. This clearly shows that you can decide for yourself what style you'd like to adopt for your code. Just be **consistent** about it.

My personal opinion is that it's better to include semicolon, since other languages like Java and Ruby adopts the same convention. This is so that you won't be caught off guard when using a programming language where _semicolon is mandatory_.
