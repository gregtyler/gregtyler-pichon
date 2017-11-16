Published: xxx
Author: Greg Tyler <greg@gregtyler.co.uk>
Standfirst: A quick tutorial of how to build Vue's Single File Components with Grunt and Browserify

# Building Vue Single File Components with Grunt and Browserify

[Vue.js's](https://vuejs.org/) Single File Components are great: they're easy to use, easy to share and satisfying to work with. There are lots of tutorials online about how to use them, and plenty too about how to build them using various build tools (Webpack, Rollup, Gulp...). However, I struggled to find a good guide to building Single File Components with Grunt and Browserify, so I thought I'd write one.

I should start by saying that I wouldn't necessarily recommend using Grunt and/or Browserify. There's nothing wrong with them, but they wouldn't be my first choice. However, they're what we use in my current job so they're what I implemented Vue with.

I'm also going to assume that you're familiar with Vue and its Single File Components.

## The tools

[Grunt](https://gruntjs.com/) is a programmable task runner that automates common processes. In the context of this tutorial, it automates the process of combining all of your component files into one to put them onto a server.

[Browserify](http://browserify.org/) is a build tool that allows you to use the `require` function (common in Node.js) to import other JavaScript files into the one you're currently using. In the context of Vue, it allows you to specify which other components are used within your current component.

## The files

An example of a Vue Single File Component is shown below. Notice how it uses `require` to use another, smaller component.



## The NPM packages

## The Grunt file
