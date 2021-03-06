DOMPurify
=========

DOMPurify is a DOM-only, super-fast, uber-tolerant XSS sanitizer for HTML, MathML and SVG. It's written in JavaScript and works in all modern browsers (Safari, Opera (15+), Internet Explorer (9+), Firefox and Chrome - as well as almost anything else using Blink or Webkit). DOMPurify is written by security people who have vast background in web-attacks and XSS. Fear not.

### What does it do?

DOMPurify sanitizes HTML and prevents XSS attacks. You can feed DOMPurify with string full of dirty HTML and it will return a string with clean HTML. DOMPurify will strip out everything that contains dangerous HTML and thereby prevent XSS attacks and other nastiness. It's also damn bloody fast. We use the technologies the browser provides and turn them into an XSS filter. The faster your browser, the faster DOMPurify will be.

### How do I use it?

It's easy. Just include DOMPurify on your website. Afterwards you can sanitiize strings by executing the following code:

```javascript
var clean = DOMPurify.sanitize(dirty);
```

### Is there a demo?

Of course there is a demo! [Play with DOMPurify](https://cure53.de/purify)

### What is supported?

DOMPurify currently supports HTML5, SVG and MathML. DOMPurify per default allows CSS, HTML custom data attributes. DOMPurify also supports the Shadow DOM - and sanitizes DOM templates recursively. DOMPurify also allows you to sanitize HTML for being used with the jQuery `$()` method - you know, that case when it's used as a HTML factory: `$("<svg onload=alert(1)>")`.

### Can I configure it?

Yes. The included default configuartion values are pretty good already - but you can of course override them:

```javascript
// Allow only <b>
var clean = DOMPurify.sanitize(dirty, {ALLOWED_TAGS: ['b']});

// Allow only <b> with style attributes (for whatever reason)
var clean = DOMPurify.sanitize(dirty, {ALLOWED_TAGS: ['b'], ALLOWED_ATTR: ['style']});

// prohibit HTML5 data attributes
var clean = DOMPurify.sanitize(dirty, {ALLOW_DATA_ATTR: false});

```

### What's on the road-map?

A lot. We want to support as many safe tags and attributes as possible. Currently, we work on extending the SVG support. Future versions will also allow to pass in a DOM or HTML element, get a DOM or an element back, reliably prevent leakage via HTTP requests, proxy HTTP requests etc. etc.

### Who contributed?

Several people need to be listed here! [@garethheyes](https://twitter.com/garethheyes) for invaluable help, [@shafigullin](https://twitter.com/shafigullin) for breaking the library multiple times and thereby strengthening it, [@mmrupp](https://twitter.com/mmrupp) for doing the same. Thanks also go to [@cgvwzq](https://twitter.com/cgvwzq), [@robbertatwork](https://twitter.com/robbertatwork) and [@giutro](https://twitter.com/giutro)!
