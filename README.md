# Freshmaker

On July 26, 2008 Stoyan Stefanov published his seminal blog post [location=location](http://www.phpied.com/locationlocation) which listed 535 ways to refresh a page using JavaScript. At the time I was just learning how to JavaScript (by hacking about with the at-the-time flagship [Prototype JS](http://prototypejs.org)) and legitimately used this page as a resource when I needed to learn how to trigger a full-page refresh.

In a fit of whiskey-fueled madness I thought (as any sane person would) "Why not bundle all 535 of these into one object and build a script that will pick one at random when a refresh is needed?" We have since added 31 more because the web has not stood still and neither has our poor judgment, bringing the total to 566.

**Update, 2026**: In a brief moment of clarity, it was discovered that the original implementation passed JavaScript strings to `window.setTimeout`, which evaluates them as code. This is `eval`. A previous "fix" had switched to `new Function`, which is also `eval`. Both approaches were 3 `eval`s in a trench coat. The ~~536~~ **566** strings have since been replaced with actual JavaScript functions, which is the correct way to do this and feels profoundly out of place here.

And here we are. To be clear: **this is the worst thing anyone's ever made.** Nobody in their right mind should use this in their project.

That said, if you really really _really_ want to, here's how!

<img src="https://media0.giphy.com/media/v1.Y2lkPTc5MGI3NjExMXl4M2t2bGUyMzI0cTM3azkzbDB6Z2N2NnBpc2Q3anA5OWhta2pycSZlcD12MV9pbnRlcm5hbF9naWZfYnlfaWQmY3Q9Zw/NRz7qKRkrgIWsQsjba/giphy.gif" width="150" title="y tho">

## howto.txt

First off, you need to include ```freshmaker.js``` into your page (maybe someday I'll put this up as a bower package or something equally time-wasting). Any time you need to trigger a page refresh just call ```_fm();``` and Bob's your uncle.

Freshmaker has no dependencies other than possibly your own lack of self-respect and a stiff drink. It originally required ECMAScript 5 for ```Object.keys```, but we've since added ```Reflect``` (ES2015) and the Navigation API (Chrome 102+, 2022), so the honest answer is that not all 566 methods will work in all browsers. This is fine. This is a feature. If you're still on IE 8 you've got bigger problems to deal with than not being able to use this stupid thing. You might also possibly have a time machine, in which case please go back to 2018 and stop me from writing this (also while you're at it tell me to buy NVIDIA stock).

### options (because why not)

If you're curious to know which one of the 566 options is being used on any given refresh, just pass a number as an argument to the function. It will delay for that many seconds _and_ log the function being used to the console! I know! ```_fm(5);``` will wait for 5 seconds before firing and ```console.log()``` the refresh method being used. Any argument passed that's not a number is ignored.

