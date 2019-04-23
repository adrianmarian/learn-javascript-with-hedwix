# JavaScript lexical guide

This chapter attempts to describe JavaScript's building blocks: the importance of semicolons, how to comment, its encoding, case sensitivity, literals, reserved words and the significance of white space.

For most of JavaScript routines you will do, these things won't have big impact. They are just nice to know in some cases.

## JavaScript encoding

ECMAScript mentioned that the source code text of the language is expressed using Unicode[^1] . What this means for developers like you and I is that JS do support using other language character like Chinese or Japanese. For example:

```js
var あたし = "hello world"
console.log(あたし)
// will print hello world
```

## Use of semicolons

This is perhaps one of the most confusing part about JavaScript simply because of the ECMAScript specification it adheres to. I can go and make one long post about this problem, but for now suffice to say that semicolons in JavaScript is used for terminating statement, but it's never mandatory. So if you're coming from a language that do not use semicolons (like Python) to end statements, then you can avoid them in JavaScript. Just make sure you don't do strange things like writing a statement on multiple lines:

```js
var string =

"hello"

return

string

// please don't.
```

Unless you used a really queer language before learning JavaScript, you’ll be fine 99% of the time.

Personally I still use semicolons in my JS source code, since JSHint warns me to

## Case sensitivity

JS is a case sensitive language. A variable named `string` is different from `String`.

## Comments

You can use two types of comments in JavaScript:

```js
// this is single line comment

/* This comment span multi-line
You can put anything inside this comment
Just don't forget to close it
*/

/* but you can also use it for single line comment */
// you can comment your code to disable it from running, useful for debugging

function greeting (){
  // console.log('Hello There !')
}
greeting();
```

## White spaces

JavaScript doesn't give any special significance to white spaces, unlike other language like Python which will throw error when an if block statement is not followed by indent. Spaces and line breaks can be added to your codebase in whatever style your organization or software follows. If you don't have an established coding style, then you can use linter or beautifier to make your code nice to look at.

## Literals

In a programming language, a literal is what you get "literally". Meaning it isn't representing something, and its content will always be the literal itself. An example will explain this best[^2]:

```js
foo = bar(42)
^     ^   ^
|     |   |--- literal, 42 is *literally* 42
|     |------- function, also represents "something" in memory
|------------- variable, named "foo", and the content may vary (is variable)
```

JavaScript had several literals, in here I will cover only 6 basic literals that will be used frequently. They are:

```js
// string literal
'Hello there'
// boolean literal
true
false
// number literal
25
// array literal
['a', 'b', 'c']
//object literal
{name: 'Johnson', age: 23, gender: 'male'}
// null
null
```  

## Identifiers

An identifier is used to name things you write for your application — they can be variables, functions, classes, modules, etc. You will make them up as you design your application. In JavaScript, the first character must be a letter, an underscore (_), or a dollar sign ($). Numbers are not allowed as the first character. You can use:

```js
// Don't use them, 'kay? they are just examples. Please use clear and specific names in practice.
$variable
variable
_variable
VARIABLE
$function
$FUNCTION
MODULES
CLASS
```

## Reserved words in JavaScript

Reserved keywords may not be used as variable names in JavaScript. For optimal backwards compatibility with older JavaScript engines, it’s best to avoid using the keywords on this page as variable names or property names — even the old ECMAScript 2 ones like `char` and `default`[^3] . In ECMAScript 2 and 3, here is the following reserved words:

```js
do
if
in
for
int
new
try
var
byte
case
char
else
enum
goto
long
null
this
true
void
with
break
catch
class
const
false
final
float
short
super
throw
while
delete
double
export
import
native
public
return
static
switch
throws
typeof
boolean
default
extends
finally
package
private
abstract
continue
debugger
function
volatile
interface
protected
transient
implements
instanceof
synchronized
```

### ES5 / 5.1 reserved words

```js
do
if
in
for
let
new
try
var
case
else
enum
eval
null
this
true
void
with
break
catch
class
const
false
super
throw
while
yield
delete
export
import
public
return
static
switch
typeof
default
extends
finally
package
private
continue
debugger
function
arguments
interface
protected
implements
instanceof
```

### ES6 / 2015 reserved words

```js
do
if
in
for
let
new
try
var
case
else
enum
eval
null
this
true
void
with
await
break
catch
class
const
false
super
throw
while
yield
delete
export
import
public
return
static
switch
typeof
default
extends
finally
package
private
continue
debugger
function
arguments
interface
protected
implements
instanceof
```

[^1]:[http://www.ecma-international.org/ecma-262/6.0/#sec-conformance](http://www.ecma-international.org/ecma-262/6.0/#sec-source-text)
[^2]:[Literals vs Variables](https://stackoverflow.com/a/16116487)
[^3]:[JS Reserved Keywords](https://mathiasbynens.be/notes/reserved-keywords)