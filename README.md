# me-swiper

[![npm version](http://badge.fury.io/js/me-swiper.svg)](http://badge.fury.io/js/me-swiper)
[![Download Count](http://img.shields.io/npm/dm/me-swiper.svg?style=flat)](http://www.npmjs.com/package/me-swiper)

> Focus on mobile, lightweight Swiper native js plugin (3kb gziped)

> Fork of original [Swipe](https://github.com/thebird/Swipe), implement custom swipe width, offset, infinite carousel and other functions for a smoother experience

[中文文档](https://github.com/SimonZhangITer/me-swiper/blob/master/README.CN.md)

# Preview
<img src="https://p0.meituan.net/dpgroup/21b2252b405605a068f19c97b9d7c96b16823.png" width=120>

[Preview](https://simonzhangiter.github.io/me-swiper/)

# Install

```bash
npm install me-swiper
// or
yarn add me-swiper
```
or script tag

```javascript
<script src="./swiper.min.js"></script>
```
and now you can use the global variable `meSwiper`

## Usage

Swipe only needs to follow a simple layout pattern. Here is an example:

```html
<div class="me-swiper">
  <div class="swiper-wrap">
    <div class="swipe-item"></div>
    <div class="swipe-item"></div>
    <div class="swipe-item"></div>
    <div class="swipe-item"></div>
  </div>
</div>
```

Above is the initial required structure – a series of elements wrapped in two containers. Place any content you want within the items. The containing div will need to be passed to the Swipe function like so:

```js
import Swiper from 'me-swiper'

const mySwiper = new Swiper(document.querySelector('.me-swiper'));
```

Also Swipe needs just a few styles added to your stylesheet:

```css
.me-swiper {
  overflow: hidden;
  position: relative;
}

.swiper-wrap {
  overflow: hidden;
  position: relative;
}

.swipe-item {
  float: left;
  width: 100%;
  position: relative;
}
```

## Config Options

Swiper can take an optional second parameter– an object of key/value settings:

| parameter       | description                                                                            | type     | default            |
| --------------- | -------------------------------------------------------------------------------------- | -------- | ------------------ |
| width           | customize the width of a single swipe                                                  | int      | -                  |
| offset          | Swipe's distance to the left of the offset                                             | int      | -                  |
| startSlide      | index position Swipe should start at                                                   | int      | 0                  |
| speed           | speed of prev and next transitions in milliseconds                                     | int      | 300                |
| auto            | begin with auto slideshow (time in milliseconds between slides)                        | int      | -                  |
| continuous      | create an infinite feel with no endpoints                                              | boolean  | false              |
| disableScroll   | stop any touches on this container from scrolling the page                             | boolean  | false              |
| stopPropagation | stop event propagation                                                                 | boolean  | false              |
| callback        | runs at slide change                                                                   | Function | (index, currentEl) |
| transitionEnd   | runs at the end slide transition                                                       | Function | (index, currentEl) |
| swiping         | invoked while swiping with the percentage (0-1) of the full width that has been swiped | Function | (percent)          |

### Example

```js
const mySwiper = new Swiper(document.querySelector('.me-swiper'), {
  width: 310,
  offset: 30,
  startSlide: 2,
  speed: 400,
  auto: 3000,
  continuous: true,
  disableScroll: false,
  stopPropagation: false,
  callback: function(index, elem) {},
  transitionEnd: function(index, elem) {}
});
```

## Swipe API

Swipe exposes a few functions that can be useful for script control of your slider.

`prev()` slide to prev

`next()` slide to next

`getPos()` returns current slide index position

`getNumSlides()` returns the total amount of slides

`kill()` destroy the current swiper instance
