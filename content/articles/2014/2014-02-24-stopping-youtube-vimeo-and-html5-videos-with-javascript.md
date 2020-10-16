---
categories:
- Code
date: '2014-02-24'
url: /stopping-youtube-vimeo-and-html5-videos-with-javascript/
title: Stopping YouTube, Vimeo, and HTML5 Videos with JavaScript
---

One annoying thing about a few of my content-oriented scripts (like <a href="http://cferdinandi.github.io/slider/">Slider</a>, <a href="http://cferdinandi.github.io/tabby/">Tabby</a>, and <a href="http://cferdinandi.github.io/modals/">Modals</a>) is that if they contained a video, it would continue to play even when the slider was slid, the tab was toggled or the modal was closed.

Well, no more!

## Stopping videos with JavaScript

Those scripts have all been updated with a new function that stops or pauses YouTube, Vimeo and HTML5 videos when the content area is closed. If you're interested in adding something like that to your scripts, here's how it works.

Add this method to your script:

```js
var stopVideo = function ( element ) {
    var iframe = element.querySelector( 'iframe');
    var video = element.querySelector( 'video' );
    if ( iframe !== null ) {
        var iframeSrc = iframe.src;
        iframe.src = iframeSrc;
    }
    if ( video !== null ) {
        video.pause();
    }
};
```

Call the function as needed, passing the container element into the function:

```js
stopVideo( tab );
```

This works in all modern browsers, and Internet Explorer 8 and above.