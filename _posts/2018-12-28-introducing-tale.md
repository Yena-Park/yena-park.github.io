---
layout: post
title:  "[React] Named Export vs Default Export in ES6"
author: "Yena Park"
---

ES6 provides us to import a module and use it in other files. Strictly speaking in React terms, one can use stateless components in other components by exporting the components from their respective modules and using it in other files.

ES6 provides two ways to export a module from a file: named export and default export.

Named Export: (export)
----------------------
With named exports, one can have multiple named exports per file. Then import the specific exports they want surrounded in braces. The name of imported module has to be the same as the name of the exported module.
```javascript
// imports
// ex. importing a single named export
import { MyComponent } from "./MyComponent";
// ex. importing multiple named exports
import { MyComponent, MyComponent2 } from "./MyComponent";
// ex. giving a named import a different name by using "as":
import { MyComponent2 as MyNewComponent } from "./MyComponent";
// exports from ./MyComponent.js file
export const MyComponent = () => {}
export const MyComponent2 = () => {}
```
Import all the named exports onto an object:
```javascript
import * as MainComponents from "./MyComponent";
// use MainComponents.MyComponent and MainComponents.MyComponent2
here
```

Default Export: (export default)
--------------------------------
One can have only one default export per file. When we import we have to specify a name and import like
```javascript
// import
import MyDefaultComponent from "./MyDefaultExport";
// export
const MyComponent = () => {}
export default MyComponent;
```
The naming of import is completely independent in default export and we can use any name we like.

Preference: [Medium](https://medium.com/@etherealm/named-export-vs-default-export-in-es6-affb483a0910)
