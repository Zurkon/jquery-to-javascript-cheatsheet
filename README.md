# jQuery to Javascript Cheat sheet
A Cheat sheet for moving from jQuery to vanilla Javascript

# Description
jQuery is still a useful and pragmatic library, but chances are increasingly that you’re not dependent on using it in your projects to accomplish basic tasks like selecting elements, styling them, animating them, and fetching data—things that jQuery was great at. With broad browser support of ES6 (over 96% at the time of writing), now is probably a good time to move away from jQuery.

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
