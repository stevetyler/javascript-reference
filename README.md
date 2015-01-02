Event delegation
------

Event delegation allows you to avoid adding event listeners to specific nodes;  instead, the event listener is added to one parent. The event listener analyses bubbled events to find a match on child elements.

Benefits:

*  Less event handlers to setup and reside in memory leading to better performance
*  No need to re-attach handlers after a DOM update
*  If your page content is generated dynamically, via Ajax for example, you don’t need to add and remove event handlers as elements are loaded or unloaded

Potential problems:

*  There’s a risk your event management code could become a performance bottleneck, so keep it as lean as possible.
*  Not all events bubble. The blur, focus, load and unload events don’t bubble like other events. The blur and focus events can actually be accessed using the capturing phase (in browsers other than IE) instead of the bubbling phase but that’s a story for another day.

You need caution when managing some mouse events. If your code is handling the mousemoveevent you are in serious risk of creating a performance bottleneck because the mousemove event is triggered so often. The mouseout event has a <a href="http://www.quirksmode.org/js/events_mouse.html#link8">quirky behaviour</a> that is difficult to manage with event delegation.

Event bubbling and capturing
------

Event bubbling and capturing are two ways of event propagation in HTML DOM. In bubbling the event is first captured and handled by the inner most element and then propagated to outer elements.

In capturing the event is first captured by the outer most element and propagated to the inner most element. During the time of Netscape browser they were advocates of event capturing and Microsoft was from event bubbling school.

Both are part of the W3C standard. As per the standard first the event will capture it till it reaches the target then it will bubble up to the outer most element. IE uses only event bubbling where as firefox supports both bubbling and capturing.

We can use the addEventListener(type, listener, useCapture) to register event handlers for bubbling and capturing phases. To use the capturing phase event handling pass the third argument as true.

Only event bubbling model is supported by all the major browsers. So if you are going to use event capturing still you need to handle event bubbling for IE. So it will easier to use event bubbling instead of capturing.
<pre>&lt;div&gt;
    &lt;ul&gt;
        &lt;li&gt;&lt;/li&gt;
    &lt;/ul&gt;
&lt;/div&gt;</pre>
If you take this structure and assume that a click event has happened in the li element.

In capturing model the event will be handled by the div first(click event handlers in the div will fire first) then in the ul then at the last in the target element li.

In bubbling model it is the opposite. In this model the event will be first handled by the li first and the ul and at the last by the div element.

Javascript inheritance
------

JavaScript only has one construct: objects and each object has an internal link to another object called its prototype. That prototype object has a prototype of its own, and so on until an object is reached with null as its prototype. null, by definition, has no prototype, and acts as the final link in this prototype chain.

While this is often considered to be one of JavaScript's weaknesses, the prototypal inheritance model is in fact more powerful than the classic model. It is, for example, fairly trivial to build a classic model on top of a prototypal model, while the other way around is a far more difficult task.

AJAX - Asynchronous Javascript and XML
------

With Ajax, web applications can send data to, and retrieve data from, a <a href="http://en.wikipediorg/wiki/Web_server">server</a> asynchronously (in the background) without interfering with the display and behaviour of the existing page. Data can be retrieved using the <a href="http://en.wikipediorg/wiki/XMLHttpRequest">XMLHttpRequest</a> <a href="http://en.wikipediorg/wiki/Object_(computer_science)">object</a>. Despite the name, the use of XML is not required (<a href="http://en.wikipediorg/wiki/JavaScript_Object_Notation">JSON</a> is often used instead), and the requests do not need to be asynchronous.

JSONP and how it's not really AJAX
------

JSONP or "JSON with padding" is a communication technique used in JavaScript programs running in web browsers to request data from a server in a different domain, something prohibited by typical web browsers because of the same-origin policy.

Explain the same-origin policy with regards to JavaScript
------

Two pages have the same origin if the protocol, port (if one is specified), and host are the same for both pages. The following table gives examples of origin comparisons to the URL http://store.company.com/dir/page.html:
<table width="606" border="0" cellspacing="0" cellpadding="2">
<tbody>
<tr>
<td valign="top" width="133">URL</td>
<td valign="top" width="223">Outcome</td>
<td valign="top" width="248">Reason</td>
</tr>
<tr>
<td valign="top" width="133"><a href="http://store.company.com/dir2/other.html">http://store.company.com/dir2/other.html</a></td>
<td valign="top" width="223">Success</td>
<td valign="top" width="248"></td>
</tr>
<tr>
<td valign="top" width="133">http://store.company.com/dir/inner/another.html</td>
<td valign="top" width="223">Success</td>
<td valign="top" width="248"></td>
</tr>
<tr>
<td valign="top" width="133">https://store.company.com/secure.html</td>
<td valign="top" width="223">Fail</td>
<td valign="top" width="248">Different port</td>
</tr>
<tr>
<td valign="top" width="133"><a href="http://store.company.com:81/dir/etc.html">http://store.company.com:81/dir/etc.html</a></td>
<td valign="top" width="223">Fail</td>
<td valign="top" width="248">Different port</td>
</tr>
<tr>
<td valign="top" width="133"><a href="http://news.company.com/dir/other.html">http://news.company.com/dir/other.html</a></td>
<td valign="top" width="223">Fail</td>
<td valign="top" width="248">Different host</td>
</tr>
</tbody>
</table> 


Host objects and native objects
------

Host objects : 

*  Array
*  String
*  Math
*  parseInt
*  eval

Native objects: 

*  window
*  document
*  location
*  history
*  setTimeout
*  getElementsByTagName

Extending built in JavaScript objects
------

This technique is called monkey patching and breaks encapsulation. While used by popular frameworks such as Prototype.js, there is still no good reason for cluttering built-in types with additional non-standard functionality.

A good reason for extending a built-in prototype is to backport the features of newer JavaScript engines; for example Array.forEach, etc.

How 'this' works in JavaScript
------

This always refers to the object that a function is a method of. When we define a function doSomething() in a page, its owner is the page, or rather, the window object (or global object) of JavaScript. An onclick property, though, is owned by the HTML element it belongs to.

http://quickleft.com/blog/jquery-conf-video-understanding-scope-in-javascript

Hashtable
------

In computing, a hash table (hash map) is a data structure used to implement an associative array, a structure that can map keys to values. A hash table uses a hash function to compute an index into an array of buckets or slots, from which the correct value can be found.

Difference between .call and .apply
------

Apply lets you invoke the function with arguments as an array; call requires the parameters be listed explicitly.

<pre><code>theFunction.apply(valueForThis, arrayOfArgs)
theFunction.call(valueForThis, arg1, arg2, ...)</code></pre>

Arity of a function
------

The arity property used to return the number of arguments expected by the function, however, it no longer exists and has been replaced by the <a href="https://developer.mozillorg/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/length">Function.prototype.length</a> property.
 
The Difference between a variable that is: null, undefined or undeclared
------

How would you go about checking for any of these states?

Closures and There Uses
------

Anonymous Functions Use Cases
------

JavaScript Module Pattern
------

clean namespacing.
What if your modules are namespace-less?

Code Organization
------

module pattern, classical inheritance

  
Difference between: function Person(){}, var person = Person(), and var person = new Person()
------

Function.prototype.bind
------

document.write()
------

<p>Most generated ads still utilize document.write() although its use is frowned upon</p>
<hr />

Feature Detection, Feature Inference, and using the UA string
------



document load and document ready event
------

<h4> Difference between == and ===</h4>
If the two operands are of the same type and have the same value, then === produces true and !== produces false.  == and != attempt to coerce the values. These are some of the interesting cases:
<pre>'' == '0'           // false
0 == ''             // true
0 == '0'            // true
false == 'false'    // false
false == '0'        // true
false == undefined  // false
false == null       // false
null == undefined   // true
' \t\r\n ' == 0     // true</pre>
All of the comparisons above produce false with the === operator and it’s recommended to always use === and !==
<h4> Explain how you would get a query string parameter from the browser window's URL.</h4>

<hr />
<h4> Describe inheritance patterns in JavaScript.</h4>
Make this work:

[1,2,3,4,5].duplicate(); // [1,2,3,4,5,1,2,3,4,5]
<h4> Describe a strategy for memoization (avoiding calculation repetition) in JavaScript.</h4>
<hr />
<h4> Why is it called a Ternary expression, what does the word "Ternary" indicate?</h4>
<hr />

 
Advantages and disadvantages to using "use strict"
------

Only compatible with ECMAscript 5.
 
 
Prototypal Inheritance
------

AMD vs CommonJS
------


JavaScript Templating
------

If so, what libraries have you used? (Mustache.js, Handlebars etc.)

Javascript Hoisting
------

Difference between an "attribute" and a "property"
------


 

