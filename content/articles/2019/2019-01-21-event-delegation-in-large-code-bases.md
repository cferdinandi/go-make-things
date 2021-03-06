---
title: "JavaScript event delegation across a code base"
date: 2019-01-21T10:30:00-05:00
draft: false
categories:
- Accessibility
- Art and Science
- Business and Leadership
- Careers
- Code
- CSS
- Design and UX
- HTML
- JavaScript
- Technology
- Web Performance
- WordPress
- Vanilla Framework Demos
---

I'm a big fan of event delegation. [If you're unfamiliar with the concept, here's a quick overview.](/checking-event-target-selectors-with-event-bubbling-in-vanilla-javascript/)

A common follow-up question I get when advocating this approach is how to handle event listeners across several JavaScript modules are components.

For example, let's say you had components for an accordion, toggle tabs, and a modal window. All three use a `click` event listener.

Should you use a single event listener for all three components, or three separate ones---one in each component?

```js
/**
 * All-in-one
 */
document.addEventListener('click', function (event) {

	if (event.target.matches('.accordion')) {
		// Do accordion stuff
	}

	if (event.target.matches('.tab')) {
		// Do tab stuff
	}

	if (event.target.matches('.modal')) {
		// Do modal stuff
	}

}, false);

/**
 * Three Separate listeners
 */

var accordion = function () {

	// All the other code...

	document.addEventListener('click', function (event) {
		if (event.target.matches('.accordion')) {
			// Do accordion stuff
		}
	}, false);

};

var tabs = function () {

	// All the other code...

	document.addEventListener('click', function (event) {
		if (event.target.matches('.tab')) {
			// Do accordion stuff
		}
	}, false);

};

var modals = function () {

	// All the other code...

	document.addEventListener('click', function (event) {
		if (event.target.matches('.modal')) {
			// Do accordion stuff
		}
	}, false);

};
```

The "all-in-one" approach is better for performance.

I personally use the second approach, because I like to keep my listeners with their components and maintain modular code bases.

I think it's more important to delegate events within a component than across your entire code base. That's where you'll see the biggest gains in performance.

Tomorrow, I'm going to share a small helper library I wrote to let you get the best of both worlds.