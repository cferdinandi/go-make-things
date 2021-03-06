---
title: "Event delegation and multiple selectors with vanilla JS"
date: 2019-11-26T10:30:00-05:00
draft: false
categories:
- Code
- JavaScript
- Web Performance
---

[I'm a big fan of event delegation.](/why-event-delegation-is-a-better-way-to-listen-for-events-in-vanilla-js/)

Today, we're going to look at approaches for using event delegation with multiple selectors.

## How it works

If you're not familiar with the approach, here's how it works. Instead of attaching events to specific elements, you listen for that event on a parent element (often the `document` or `window`).

Any event of that type that happen inside the parent element *bubble up*, and you can filter out the ones that don't match the element you're looking for.

```js
document.addEventListener('click', function (event) {

	// Check for the .click-me class
	// If the clicked element doesn't have it, do nothing
	if (!event.target.matches('.click-me')) return;

	// The code you want to run goes here...

});
```

If you're listen for events on more than one element with the same selector, this approach is actually better for performance because it uses less memory in the browser.

## Multiple selectors

When I share this approach, I often have students ask me how to implement it when you need to listen for the same type of event for multiple different selectors, and do different things based on which selector the element has.

For example, let's say you have show/hide content buttons that have a `.show-me` class on them, and another set of buttons with the `.save` class that save the content of a form for reuse later.

How do you parse which actions to run based on the selector?

### Option 1: separate event listeners

The most obvious approach is to use two separate event listeners, one for each selector.


```js
document.addEventListener('click', function (event) {
	if (!event.target.matches('.show-me')) return;
	// Reveal the hidden content...
});

document.addEventListener('click', function (event) {
	if (!event.target.matches('.save')) return;
	// Save the form content...
});
```

This approach works well if your scripts are kept in separate, modular files.

While you're using two event listeners instead of one, this is still far better for performance than attaching a listener to every single matching button.

### Option 2: `if...else`

If both pieces of code are in the same file, you can combine them into a single event listener and use an `if...else if` statement.

```js
document.addEventListener('click', function (event) {

	if (event.target.matches('.show-me')) {
		// Reveal the hidden content...
	} else if (event.target.matches('.save')) {
		// Save the form content...
	}

});
```

This gives you a small performance bump.

### Option 3: `if` and `return`

A lot of people find `if...else if` statements unwieldy, especially if you have more than just a couple of checks. They can quickly grow out of hand.

For that reason, I prefer to use sequential `if` statements, with a `return` inside the curly brackets to end the function when a match happens.

```js
document.addEventListener('click', function (event) {

	if (event.target.matches('.show-me')) {
		// Reveal the hidden content...
		return;
	}

	if (event.target.matches('.save')) {
		// Save the form content...
		return;
	}

});
```

This approach is, to me, easier to read. It also means I can move my checks around without worrying about breaking anything.

### Option 4: handler functions

If you enjoy *functional programming*, this approach provides a nice structure.

Inside the event listener callback, you call separate *handler functions* for each selector, and pass in the `event` object. In each handler function, you run your selector check and run code accordingly.

```js
var showMe = function (event) {
	if (!event.target.matches('.show-me')) return;
	// Reveal the hidden content...
};

var saveMe = function (event) {
	if (!event.target.matches('.save')) return;
	// Save the form content...
};

document.addEventListener('click', function (event) {
	showMe(event);
	saveMe(event);
});
```

This approach provides a nice balance of performance and maintainability.

It's a little less performance than options 2 and 3, because the `saveMe()` function will run even if `showMe()` finds a match (the other two approaches stop as soon as a match is found). But its still better than have separate event listeners, and provides a clean, readable code structure.

## Which approach should you use?

Ultimately, it depends on your project.

I use option 1 a lot, because I tend to keep my scripts in modular files. But when code is all in one, file, option 4 is my favorite.