# Handling forms

A form is an HTML element that contains different type of input elements. It is the point where the user can take action and send information into your website. The most commonly used form example is a login form, where users can put their username and password for logging into a website, granting more access to the website's features (think of Facebook and Twitter.)

A regular HTML form sends data into the link defined in its `action` attribute, creating a reload sequence where form data is first validated and then return a response. On the other hand, an HTML form powered by JavaScript can do validation, send data into the defined location and return a response without a reload sequence. This way, the server have no need of sending the web page data again to the client.

Therefore JavaScript can save a bit of time with each form submit.

## Form submit event

Let's write a small form example for use in this chapter. It will be a simple login form, with input text for email and password:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="utf-8">
  <title>Form Example</title>
</head>
<body>
  <form id='login-form'>
    <div>
      <label>E-mail:</label>
      <input type="email" name="email">
    </div>
    <div>
      <label>Password:</label>
      <input type="password" name="password">
    </div>
    <div>
      <button type="submit">Login</button>
    </div>
  </form>
  
  <script src="index.js"></script>
</body>
</html>
```

Now let's write an event listener that listens to the submit event. You can get the form using the id `login-form`:

```js
document.getElementById("login-form").addEventListener("submit", function(event){
  event.preventDefault();
  console.log(event.target.elements.email.value);
  console.log(event.target.elements.password.value);
});
```

The code `event.preventDefault()` is used to cancel the default action run by the browser when a certain event is triggered. In case of a form, the browser will perform a request to the location specified in the `action` attribute, and will simply reload the same location if there is no `action` attribute defined.

If you don't use it, the page will reload on submit, and the rest of your JavaScript code inside the event function won't be able to execute because of that reload.

Now with JavaScript having control of the form using event listener above, you can write any code necessary for validating and processing the form. Let's learn a bit about validating the form values next.

## Validating form values

A form data needs to be validated before being sent into the processing location. After having control of the form, JavaScript can validate the data being send by the user before sending it to the location. Continuing from the previous example, let's validate the `email` and `password` data that are being put inside the `event` object:

```js
document.getElementById("login-form").addEventListener("submit", function(event){
  event.preventDefault();
  let email = event.target.elements.email.value;
  let password = event.target.elements.password.value;
  if (!email){
    alert('Email must not be empty!');
    return;
  }
  if (!password) {
    alert('Password must not be empty!');
    return;
  }
  // replace this code with actual submit process
  alert(`Your input values: \n
          email: ${email} \n
          password: ${password}`);
});
```

This way, the form values won't be submitted until it pass the validation. Once the data is validated, you can send it to the proper destination using JavaScript network request.

## Other types of input

There is a slight different on how the value of input is retrieved depending on what type of input you implement into your form.

A `checkbox` input will only have Boolean `true` or `false` value. In order to get the value of a `checkbox` input, you need to get the `.checked` property instead of `.value`:

```html
<form id="sample-form">
  <div>
    <input type="checkbox" name="agreement" id="agreement">
    <label for="agreement">I agree to the terms and conditions</label>
  </div>
  <div>
    <button type="submit">Submit</button>
  </div>
</form>
```

```js
document.getElementById("sample-form").addEventListener("submit", function(event){
  event.preventDefault();
  let agreement = event.target.elements.agreement.checked;
});
```

For a `radio` input, you can use the same `.value` property from the element object:

```html
<form id="sample-form">
  <div>
    Gender
    <input type="radio" name="gender" id="male" value="male"/>
    <label>Male</label>
    <input type="radio" name="gender" id="female" value="female"/>
    <label>Female</label>
    <input type="radio" name="gender" id="unidentified" value="unidentified"/>
    <label>Unidentified</label>
  </div>
  <div>
    <button type="submit">Submit</button>
  </div>
</form>
```

```js
document.getElementById("sample-form").addEventListener("submit", function(event){
  event.preventDefault();
  let gender = event.target.elements.gender.value;
  console.log(gender);
});
```

For dropdown / `select` element, you also use the same `.value` property from element object:

```html
<form id="sample-form">
  <div>
    <label for="education">Education level</label>:
    <select name="education" id="education">
      <option value="primary" selected>Primary school</option>
      <option value="senior">Senior school</option>
      <option value="bachelor">Bachelor degree</option>
      <option value="doctorate">Doctorate degree</option>
    </select>
  </div>
  <div>
    <button type="submit">Submit</button>
  </div>
</form>
```

```js
document.getElementById("sample-form").addEventListener("submit", function(event){
  event.preventDefault();
  let education = event.target.elements.education.value;
  console.log(education);
});
```

## Code exercise

Create a registration form using the following diagram as reference:

* First Name text field, mandatory
* Last Name text field, not mandatory
* Email address, mandatory
* Age number field, not mandatory, must be higher than 17 if not empty
* Gender radio input with 3 options: Male, Female and Unidentified, mandatory
* City select field is mandatory with four options: 'New York', 'New Delhi', 'Tokyo' and 'Other'

Don't forget to add the default empty city value into the `City` select field.