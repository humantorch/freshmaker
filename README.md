# Freshmaker

On July 26, 2008 Stoyan Stefanov published his seminal blog post [location=location](http://www.phpied.com/locationlocation) which listed 535 ways to refresh a page using JavaScript. At the time I was just learning how to JavaScript (by hacking about with the at-the-time flagship [Prototype JS](http://prototypejs.org)) and legitimately used this page as a resource when I needed to learn how to trigger a full-page refresh.

In a fit of whiskey-fueled madness I thought (as any sane person would) "Why not bundle all 535 of these into one object and build a script that will pick one at random when a refresh is needed?" 

And here we are. To be clear: **this is the worst thing anyone's ever made.** Nobody in their right mind should use this in their project.

That said, if you really really _really_ want to, here's how!

## howto.txt

First off, you need to include ```freshmaker.js``` into your page (maybe someday I'll put this up as a bower package or something equally time-wasting). Any time you need to trigger a page refresh just call ```_fm();``` and Bob's your uncle.

Freshmaker has no dependencies other than possibly your own lack of self-respect and a stiff drink.

### options (because why not)

If you're curious to know which one of the 535 options is being used on any given refresh, just pass a number as an argument to the function. It will delay for that many seconds _and_ log the function being used to the console! I know! ```_fm(5);``` will wait for 5 seconds before firing and ```console.log()``` the refresh method being used. Any argument passed that's not a number is ignored.