# Part 3 project and summary

## Currency Converter API

Let's make a simple web application to convert currencies. You will need to create an HTML form with the following inputs:

* One number input element for the amount
* Two select element: one for the currency of the amount and one for the currency you'd like to be converted into
* A submit button that triggers a POST request to Node.js server, sending the user inputs into the server

The Node.js server will have to read the data being sent and then do conversion according to the table of conversion.

You can use this data for the currency conversion in the server:

|Currency   |USD     |EUR     |GBP     |CAD     |AUD     |
|-----------|--------|--------|--------|--------|--------|
|USD        |1.00000 |0.88929 |0.76919 |1.33886 |1.39888 |
|EUR        |1.12442 |1.00000 |0.86519 |1.50656 |1.57156 |
|GBP        |1.29962 |1.15581 |1.00000 |1.74131 |1.81642 |
|CAD        |0.74636 |0.66379 |0.57427 |1.00000 |1.04319 |
|AUD        |0.71546 |0.63631 |0.55050 |0.95860 |1.00000 |

The live application can be seen [here](https://elegant-production.glitch.me/).

Hint: Remember that you need to handle the preflight OPTIONS request. Do you remember how to do it? Also, you can represent the currency conversion table as object to make it easier for the conversion process in the POST request.

Good Luck!

## Part 3 summary

You have learned the basics of using Node.js modules and created a simple server to serve network requests from HTML web page. Great job! With this new knowledge, you are ready to learn more about backend stack that makes use of Node.js modules to store permanent data record using a database software and create authentication (login / logout process).

I will write another book to cover about Node.js and using its APIs. If you'd like to be notified when it is released, you can sign up to my newsletter here.