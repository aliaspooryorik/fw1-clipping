ColdFusion + FW/1 Example Application
---------------------------------------------------

This app can be used to store clippings and news articles and was created as an exercise to learn the awesome [FW/1 Framework](https://github.com/framework-one/fw1) (it has been tested with versions 3.0 and 3.1).

For detailed explanations, checkout [this series of articles](http://dezoito.github.io/2015/03/26/fw1-example-app-released.html) on the topics I tried to cover:

### 1- Project Structure
I decided to use subsystems, so the main app's logic is inside the **/home** folder (which is the default subsystem).

Notice that I added these folders to the project's root:

**/customtags** - It stores the few custom tags used in this project (I made one to handle pagination)

**/lib** - Stores User Defined Functions and UDF libraries

**/setup** - Contains the SQL script for database creation (I used mySQL, but it's simple enough to run on other DBs)

**/static** - This is where I keep JS, CSS and Image files

**/tests** - Self explanatory (But probably one of the most interesting parts in this project)


### 2- Forms and Validation Patterns
The app uses the same view to display Create or Update forms,
the same methods to validade and save objects, and performs CSRF verification with _CSRFVerifyToken()_ to stop Cross Site Request Forgery.

Validation errors and messages are displayed next to their respect form fields.

Also, note how validation rules and attribute sanitizing code are kept within the model definition.


### 3- Use of UDF Libraries
The _/lib_ folder contains _functions.cfc_, a library of commonly used functions
that is saved in the **application** scope so they can be easily accessed anywhere.


### 4- Accessing an External Service
The app can display a summary of articles in a modal window (using the [flask-Summarizer App](https://github.com/dezoito/flask-Summarizer)).
I used this as a way to see how to make Ajax calls and also access an external service.


### 5- BDD Testing
The folder _/tests_ contains the spects for tests that run using [testBox](http://wiki.coldbox.org/wiki/TestBox.cfm) and [CFSelenium](http://cfselenium.riaforge.org/).

I start with some very simple tests that escalate to CRUD tests that save data to a testing database.
**_/tests/specs/Test_6_Integration_Selenium.cfc_** contains full integration tests using Selenium.

To run these tests, you must have CFSelenium and testBox installed on your server.

### 6- Running

If you have commandbox installed you can do:

```
$ box install
$ box start
```

This will start up a lucee server on http://localhost:8080 with a datasource configured using user 'root' and password ''. You can change the username and password in the `CFConfig.json` file.

###

### References
Aside from the Official Documentation, I am thankful to these authors and resources:

[**Raymond Camdem's QBall Sample Application**](https://github.com/framework-one/fw1/tree/master/examples/qBall)

[**Simon Bingham's Xindi CMS**](https://github.com/simonbingham/xindi)

[**Joe Steinbring's Pagination Gist**](https://gist.github.com/steinbring/4315198)


