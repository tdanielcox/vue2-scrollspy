# vue2-scrollspy

[![Vue 2.x](https://img.shields.io/badge/Vue-2.x-brightgreen.svg)](https://vuejs.org/v2/guide/)
[![npm](https://img.shields.io/npm/v/vue2-scrollspy.svg)](https://www.npmjs.com/package/vue2-scrollspy)
[![npm-downloades](https://img.shields.io/npm/dm/vue2-scrollspy.svg)](https://www.npmjs.com/package/vue2-scrollspy)
[![npm bundle size (minified + gzip)](https://img.shields.io/bundlephobia/minzip/vue2-scrollspy.svg)](https://www.npmjs.com/package/vue2-scrollspy)
[![license](https://img.shields.io/github/license/mashape/apistatus.svg)](https://github.com/ibufu/vue2-scrollspy/blob/master/LICENSE)

Scrollspy, and animated scroll-to, for Vue2, inspired by [vue-scrollspy](https://github.com/kvdmolen/vue-scrollspy).
See https://ibufu.github.io/vue2-scrollspy/ or [Jsfiddle](https://jsfiddle.net/ibufu/nw0zczLx/).

## Installation

### NPM
```
$ npm install vue2-scrollspy --save
```

### CDN
```html
<script src="//unpkg.com/vue2-scrollspy/dist/index.js"></script>
```

## Basic Usage
```js
import Vue from 'vue';
import Scrollspy from 'vue2-scrollspy';
// use default options
Vue.use(Scrollspy);

// or custom options
Vue.use(Scrollspy, options);
```

```html
<ul v-scroll-spy-active v-scroll-spy-link>
    <li>
        <a>Menu 1</a>
    </li>
    <li>
        <a>Menu 2</a>
    </li>
</ul>

<div v-scroll-spy>
    <div>
        <h1>Header 1</h1>
        <p>Content</p>
    </div>
    <div>
        <h1>Header 2</h1>
        <p>Content</p>
    </div>
</div>
```

### Old Browsers
Old Browsers like IE11:
```js
import Scrollspy from "vue2-scrollspy/dist/index";
Vue.use(Scrollspy);
```

## Configuration

### **v-scroll-spy**

Declares container of sections for elements to scrollspy.

1. `v-scroll-spy="{data: 'section'}"`: add a `section` data property in scope Vue instance that is binded to the 
section index.

2. `v-scroll-spy="{allowNoActive: true}"`: allow no active sections when scroll position is outside of the scrollspy 
container. Default behavior is too keep active at least one section in any case.

3. `v-scroll-spy="{offset: 50}"`: add an offset for scroll events.

4. `v-scroll-spy="{menuTriggerOffset: 50}"`: offset to trigger the menu active class (defaults to offset if not provided).

5. `v-scroll-spy="{time: 200, steps: 30}"`: set the animation options.

6. `$scrollTo(index: int)` is provided on scope Vue instance to invoke a scroll to the given section index.

7. `v-section-selector`: set section which should scrollto

### **v-scroll-spy-active**

Set the `active` css class on element that match the index of current scrollspy.

1. `v-scroll-spy-active="{selector: 'li.menu-item', class: 'custom-active'}"`: customize elements selection and class 
name to apply. By default, it will use direct children and apply `active` class.

### **v-scroll-spy-link**

Add click handler on children elements that will scroll to the related section.

1. `v-scroll-spy-link="{selector: 'a.menu-link'}"`: customize elements selection. By default, it will use `a` to
select all links.  

### Bezier animations

Example:
```js
import scrollSpy, { Easing } from 'vue2-scrollspy';

Vue.use(scrollSpy, {
  easing: Easing.Cubic.In
});
```
Easing options:
http://tweenjs.github.io/tween.js/examples/03_graphs.html

## Note

You should have the same number of children elements for `v-scroll-spy`, `v-scroll-spy-active` `v-scroll-spy-link` for 
directives to work properly.

If you need to share multiple scroll-spy in the same page, you can add `data-scroll-spy-id=""` on each element where a 
directive is declared.

If you want to set something else (not body) to scroll container, you could:
```html
<div class="container" v-scroll-spy>
    <div>
        <h1>Header 1</h1>
        <p>Content</p>
    </div>
    <div>
        <h1>Header 2</h1>
        <p>Content</p>
    </div>
</div>
```
```css
.container {
  position: relative;
}
```

## Develop
```shell
npm i && npm run watch 
```
```shell
cd docs-src && npm i && npm run dev
```


## License
MIT
