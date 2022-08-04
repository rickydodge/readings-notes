Read: 06 - Dynamic web pages with JavaScript

JavaScript
JavaScript (JS) is a lightweight, interpreted, or just-in-time compiled programming language with first-class functions. While it is most well-known as the scripting language for Web pages, many non-browser environments also use it, such as Node.js, Apache CouchDB and Adobe Acrobat. JavaScript is a prototype-based, multi-paradigm, single-threaded, dynamic language, supporting object-oriented, imperative, and declarative (e.g. functional programming) styles. Read more about JavaScript.

This section is dedicated to the JavaScript language itself, and not the parts that are specific to Web pages or other host environments. For information about APIs that are specific to Web pages, please see Web APIs and DOM.

The standards for JavaScript are the ECMAScript Language Specification (ECMA-262) and the ECMAScript Internationalization API specification (ECMA-402). As soon as one browser implements a feature, we try to document it. This means that cases where some proposals for new ECMAScript features have already been implemented in browsers, documentation and examples in MDN articles may use some of those new features. Most of the time, this happens between the stages 3 and 4, and is usually before the spec is officially published.

Do not confuse JavaScript with the Java programming language. Both "Java" and "JavaScript" are trademarks or registered trademarks of Oracle in the U.S. and other countries. However, the two programming languages have very different syntax, semantics, and use.

Input Output in plain JavaScript
  
 PrevNext 
In the first article we saw how to change the DOM to display something, and then we saw how to handle user events. This time we are going to see how to get input from the user and combine that with the other two, to create a simple page that can great you.

examples/js/pure_js_greating.html

<html>
<head>
  <title>Hello World</title>
</head>
<body>
 
First name: <input id="first_name">
Last name: <input id="last_name">
<button id="say">Say hi!</button>
 
<hr>
<div id="result"></div>
 
<script>
function say_hi() {
    var fname = document.getElementById('first_name').value;
    var lname = document.getElementById('last_name').value;
 
    var html = 'Hello <b>' + fname + '</b> ' + lname;
 
    document.getElementById('result').innerHTML = html;
}
 
document.getElementById('say').addEventListener('click', say_hi);
</script>
 
</body>
</html>
 
Try!
In this example we have a bit more HTML than earlier. In addition to having a button, and a div element where we'll show our results, we also have two input elements. Each one with its own ID.

If you click on the Try link, you'll see two input boxes and a button:

Input form

In the JavaScript code we have a function called say_hi. It used the getElementById we have already seen to locate the DOM element representing the input element with the id first_name. The object returned has a method value that will return the text the user has typed in that field.

We use this technique to retrieve the content of both input fields and assign their content to two variables: fname and lname.

Then, using these variable we create an HTML snippet and assign it to a new variable called html.

Then we set the innerHTML attribute as earlier to show the HTML we generated. The result might look like this:

Input form and output
