---
title: "Building accessible websites and apps is a moral obligation"
date: 2019-03-20T10:30:00-04:00
draft: false
categories:
- Accessibility
- Business and Leadership
- Careers
- Code
- CSS
- Design and UX
- HTML
- JavaScript
---

Yesterday, we recorded a [JS Jabber](https://devchat.tv/js-jabber/) episode (I'm a co-host on the show) with [Chris DeMars](http://chrisdemars.com/). (It comes out in a month or two.)

Chris has a strong focus on performance and web accessibility, and at one said something to the effect of:

> Building websites that are accessible is your moral obligation as a web developer.

I expected everyone to nod in agreement, but to my surprise, a few of my co-hosts actually disagreed with this position. At least one of them even said they would *not* want this legally required the way handicapped access is in physical businesses.

## I'm sorry, what?

I don't think I've ever been quite so frustrated by a podcast episode before. Their positions (not mine!) were as follows:

1. What's moral/immoral for me might not be the same for someone else.
2. The beauty of the web is that the friction in starting and growing a business is low, and accessibility adds more friction.
3. Handicapped people bear some of the responsibility in managing their own condition. This isn't entirely on us as developers.

My co-hosts were quick to point out that they think accessibility is a good thing, but not a *moral obligation*.

Today, I want to write some extended thoughts now that I've had more time to think about the episode and some of the things we talked about.

## Morality is not always relative

There's gray area, of course.

Is stealing immoral? What if the person has a starving, desperate family and no other options? Different people would answer that question differently.

But what about, for example, someone who builds homes for a living.

Let's say there are two ways to frame a house. One of them is simpler and faster, but about 20% of the houses randomly collapse after a couple of years. But there's a second approach, a bit slower, a bit more work, that keeps those houses standing for 100 years or more.

Would you say the builder has a moral obligation to *not* build a house that's going to collapse on people? (*If not, by the way, you might be an asshole.*)

So, too, it goes with websites.

You can quickly slap together a website or app in ways that make it unusable for people with physical and mental disabilities (an estimated 20% of the population), or you can take the time to build it right and make sure it works for everyone.

## You're a web *professional*

This is your fucking job.

You won't get it 100% perfect. It's pretty much impossible. But you need to care. You need to try. You need to educate yourself.

You wouldn't tolerate a builder who didn't bother reading the building code or educating themselves on how to properly build a house.

So why is that OK for us a builders of web things?

## The web is accessible out-of-the-box. *We* break it.

An HTML file with no CSS and no JavaScript is accessible by default.

Sometimes we break it by using the wrong HTML elements for the job. Sometimes we break it with CSS. Often, we break it by trying to do fancy stuff with JavaScript that breaks the way things normally work.

But that complaint about "adding friction" and "slowing down the dev process"... you're doing that to yourself with all of the unnecessary stuff you're trying to add, and you're breaking your own website in the process.

If you want to build something quickly, keep it simple.

## It's not on people with disabilities to tell you how you screwed up

One of my co-hosts argued that if a website is inaccessible, it's on the visitor with the disability to call customer service and let them know.

Nope. Fuck that.

It's not *my* responsibility to tell a builder they violated the building code, and it's not a user's job to tell a company their site isn't usable. It's the company's job.

Again, you're a web *professional*.

## It *should* be easier

One common theme was that accessibility should be easier. Here, I agree.

Often times it actually *is* relatively easy. There's tons of low-hanging fruit we get wrong, including...

1. Adding `alt` attributes to images.
2. Using the right elements for things (ex. `button` or link instead of a `span` or `div` for an interactive element).
3. Not removing focus styles from focusable content.
4. Using headings (`h1`, `h2`, etc.) that reflect the content structure, not for style purposes.

But for advanced features, things can get confusing. The proper markup structure, keyboard interactions, and aria attributes and roles for things like tabs, accordions, modals, and so on is tricky to get right.

The specs around these things are *not* written for the average person.

I would love more human-readable documentation on how to accessibility structure advanced components. [Dave Rupert's A11Y Nutrition Cards](https://davatron5000.github.io/a11y-nutrition-cards/) are a great start, but we need more, and it shouldn't be on Dave alone to build stuff like that.

Even better, I'd love to see native components for this stuff.

We've got [one for accordions and disclosures](/javascript-free-accordions/) now, which is awesome. There's the `dialog` element for modals, but it has [lots of implementation and accessibility issues](https://www.scottohara.me/blog/2019/03/05/open-dialog.html). A native tab component would be awesome, too.

## This is our job

Regardless of how easy or not it is, this is our job.

If you build for the web, you have a moral obligation to make sure it works right for everyone. Building code is horrible to read, but builders still have to know it. Same goes for accessibility.

And as we've already discussed, the web is accessible by default. If you break it, you have to fix it.

Let's make 2019 the year we do a better job at this.