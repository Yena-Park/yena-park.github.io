---
layout: post
title:  "[React] Component Styling"
author: "Yena Park"
---

3 ways to style react component

## CSS module
A Css Module is a CSS file in which all class names and animation names are scoped locally by default.
```javascript
import React, { Component } from 'react';
import classNames from 'classnames/bind';
import styles from './App.css';
const cx = classNames.bind(styles);

class App extends Component {
  render() {
    const isBlue = true;
    return (
      <div className={cx('box', {
        blue: isBlue
      })}>
        
      </div>
    );
  }
}

export default App;
```

## Sass
app.scss
```javascript
@import "utils";

.button {
  background: $oc-green-7;
  transition: all 0.2s ease-in;
  display: inline-block;
  padding-top: 2rem;
  padding-bottom: 2rem;
  text-align: center;
  color: white;
  position: fixed;
  font-size: 2rem;
  font-weight: 500;
  border-radius: 4px;
  cursor: pointer;

  @include place-at-center();

  width: 1200px;

  @include media("<huge") {
    width: 1024px;
  }

  @include media("<large") {
    width: 768px;
  }

  @include media("<medium") {
    width: 90%;
  }

  &:hover {
    background: $oc-green-6;
  }

  &:active {
    margin-top: 3px;
    background: $oc-green-8;
  }
}
```
utils.scss
```javascript
@import "~open-color/open-color";
@import "~include-media/dist/include-media";

$breakpoints: (
  small: 376px,
  medium: 768px,
  large: 1024px,
  huge: 1200px
);

$size: 100px;

@mixin place-at-center() {
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
```

## Styled-components

