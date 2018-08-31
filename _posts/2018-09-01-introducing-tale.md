---
layout: post
title:  "[React] Component Styling"
author: "Yena Park"
---

3 ways to style react component.

## CSS module
A Css Module is a CSS file in shich all class names and animation names are scoped locally by default.
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


## Styled-components

