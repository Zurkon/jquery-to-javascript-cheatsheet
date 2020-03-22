# jQuery to Javascript Cheat sheet
A Cheat sheet for moving from jQuery to vanilla Javascript

# Description
jQuery is still a useful and pragmatic library, but chances are increasingly that you’re not dependent on using it in your projects to accomplish basic tasks like selecting elements, styling them, animating them, and fetching data—things that jQuery was great at. With broad browser support of ES6 ([over 96% at the time of writing](https://caniuse.com/#feat=es6)), now is probably a good time to move away from jQuery.

# Note
This repository is just a copy from the blog page [move from jquery to vanilla javascript](https://tobiasahlin.com/blog/move-from-jquery-to-vanilla-javascript/) writed by [Tobias Ahlin](https://twitter.com/tobiasahlin) which means that i don't deserve any credits for this repo. I just put here for my personal and practical use but feel free to use on your own too.

# Cheat sheet
* [Selecting Elements](#selecting-elements)
* [Events](#events)
* [CSS](#css)
* [Document Ready](#document-ready)
* [Classes](#classes)
* [Ajax](#ajax)
* [HTML & Text](#html-&-text)

# Selecting Elements
Selecting one or several DOM elements to do something with is one of the most basic elements of jQuery. The equivalent to $() or jQuery() in JavaScript is [querySelector()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelector) or [querySelectorAll()](https://developer.mozilla.org/en-US/docs/Web/API/Document/querySelectorAll), which, just like with jQuery, you can call with a CSS selector.

```javascript

// jQuery, select all instances of .box
$(".box");

// Instead, select the first instance of .box
document.querySelector(".box");

// …or select all instances of .box  
document.querySelectorAll(".box");

```

## Running a function on all elements in a selection
`querySelectorAll()` returns a [NodeList](https://developer.mozilla.org/en-US/docs/Web/API/NodeList) containing all of the elements matching the query. Whereas you can run a function with jQuery on the entire selection of elements simply by calling the method on the jQuery object, however, you’ll have to iterate over the NodeList of elements using [NodeList.forEach()](https://developer.mozilla.org/en-US/docs/Web/API/NodeList/forEach) in vanilla JavaScript:

```javascript

// with jQuery
// Hide all instances of .box
$(".box").hide();

// Without jQuery
// Iterate over the nodelist of elements to hide all instances of .box
document.querySelectorAll(".box").forEach(box => { box.style.display = "none" }

```

## Finding one element within another

A common jQuery pattern is to select an element within another element using `.find()`. You can achieve the same effect, scoping the selection to an element's children, by calling `querySelector` or `querySelectorAll` on an element:

```javascript

// With jQuery
// Select the first instance of .box within .container
var container = $(".container");
// Later...
container.find(".box");

// Without jQuery
// Select the first instance of .box within .container
var container = document.querySelector(".container");
// Later...
container.querySelector(".box");

```

## Traversing the tree with `parent()`, `next()`, and `prev()`

If you wish to traverse the DOM to select a subling or a parent element relative to another element, you can access them through `nextElementSibling`, `previousElementSibling` and `parentElement` on that element:

```javacript

// with jQuery
// Return the next, previous, and parent element of .box
$(".box").next();
$(".box").prev();
$(".box").parent();

// Without jQuery
// Return the next, previous, and parent element of .box
var box = document.querySelector(".box");
box.nextElementSibling;
box.previousElementSibling;
box.parentElement;

```

# Events

There's a myriad of ways to listen ti events in jQuery, but whether you're using `on()`, `.bind()`, `.live` or `.click()`, you'll make do with the Javascript equivalent `.addEventListener`:

```javascript

// With jQuery
$(".button").click(function(e) { /* handle click event */ });
$(".button").mouseenter(function(e) {  /* handle click event */ });
$(document).keyup(function(e) {  /* handle key up event */  });

// Without jQuery
document.querySelector(".button").addEventListener("click", (e) => { /* ... */ });
document.querySelector(".button").addEventListener("mouseenter", (e) => { /* ... */ });
document.addEventListener("keyup", (e) => { /* ... */ });

```

## Event listening for dynamically added elements
jQuery's `.on()` method enables you to work with "live" event handlers, where you listen to events on objects that get dynamically added to the DOM. To accomplish something similar without jQuery you can attach the event handler on an element as you add it to the DOM:

```javascript

// With jQuery
// Handle click events .search-result elements, 
// even when they're added to the DOM programmatically
$(".search-container").on("click", ".search-result", handleClick);

// Without jQuery
// Create and add an element to the DOM
var searchElement = document.createElement("div");
document.querySelector(".search-container").appendChild(searchElement);
// Add an event listener to the element
searchElement.addEventListener("click", handleClick);

```

## Triggering and creating events

The equivalent to manually triggering events with `trigger()` can be achieved by calling [dispatchEvent()](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/dispatchEvent) , The `dispatchEvent()` method can be invoked on any element, and takes an `Event` as the first argument:

```javascript

// With jQuery
// Trigger myEvent on document and .box
$(document).trigger("myEvent");
$(".box").trigger("myEvent");

// Without jQuery
// Create and dispatch myEvent
document.dispatchEvent(new Event("myEvent"));
document.querySelector(".box").dispatchEvent(new Event("myEvent"));

```
