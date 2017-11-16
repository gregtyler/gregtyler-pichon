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

An example of a Vue Single File Component is shown below. Notice how it uses `require` to use another, smaller component. This file isn't much good on its own, so we want to use Grunt and Browserify to compile it into Vue and make it usable in our application.

```html
<template>
  <div>
    <label for="colour-selector">Select your colour, and click to continue</label>
    <select id="colour-selector" v-model="colour"><option>Red</option><option>Green</option><option>Blue</option></select>
    <ActionButton icon="arrow-right">Continue</ActionButton>
  </div>
</template>

<script type="text/javascript">
const ActionButton = require('./ActionButton.vue');

module.exports = {
  data: () => ({
    colour: 'Red'
  }),
  components: {
    ActionButton
  }
};
</script>
```

As well as your Vue components, you'll also need to have an **entry file**. This is a vanilla JavaScript file which requires and renders whatever your main root component is. This file also needs to require the `vue` NPM package so that all of Vue's functionality is included.

```javascript
const Vue = require('vue');

const App = require('./components/App.vue');

new Vue({
  el: '#app',
  render: (createElement) => createElement(App)
});
```

## The NPM packages
We need four core packages to make this work:
 * grunt
 * grunt-browserify
 * vueify
 * vue

These can be installed through NPM with the command:
```npm install --save-dev grunt grunt-browserify vueify vue```

## The Grunt file
The Grunt file is very simple, just pulling together the various things we've installed. `src/index.js` is the entry file that we described above. Notice that we don't need to specify _any_ component files: since they're required by either the entry file or a component that it requires, browserify will automatically include them in the bundle.

```javascript
module.exports = function(grunt) {
  grunt.initConfig({
    browserify: {
      bundle: {
        src: 'src/index.js',
        dest: 'build/bundle.min.js'
      },
      options: {
        browserifyOptions: {
          debug: true
        },
        transform: [
          ['vueify']
        ]
      }
    }
  });
  
  grunt.loadNpmTasks('grunt-browserify');
  
  grunt.registerTask('build', function() {
    grunt.task.run('browserify');
  });
};
