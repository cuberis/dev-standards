The purpose of this style guide is to promote clean, efficient, and most importantly, readable code. Cuberis uses ES6 as a standard for writing JavaScript.

## Variables

### Naming
Variables should be camel-cased and descriptively named.

Cuberis uses build tools to minify, concatenate, and transpile JavaScript. The result is that all variable names will be replaced with single characters in production. This provides an advantage in that we can be very clear about function and variable names when writing JavaScript. For this reason single-letter variables, such as `i`, should be reserved for writing loops.

### Declarations
Variables should be declared with the `let` or `const` keywords rather than `var`. Declare all variables required for a given scope level at the same time. Removing unnecessary uses of the word `let` is better for performance.

```
// This is preferred
let artworkTitle,
    artworkYear,
    artworkMedium;

// Not preferred
let title;
let year;
let medium;
```

For data that should not be reassigned, use the `const` delcaration. Constants, unlike variables, should be formatted as uppercase.

```
let searchQuery = '';
const API_URL = '/api/json/example';
```

### Booleans
Booleans should be written as `isCondition` or `hasProperty` so that they can be immediately recognized as booleans.

```
// This is preferred
hasCorrectName = true;
isCorrectlyNamed = true;

// Not preferred
correctName = false;
```

### Arrays & Objects
TBD...

## Functions
```
// ES5
function prefersReducedMotion() {
  return window.matchMedia("(prefers-reduced-motion)").matches ? true : false;
}


// ES6
const prefersReducedMotion () => {
    return window.matchMedia("(prefers-reduced-motion)").matches ? true : false;
}
```

Single line arrow functions with an implicit return are also acceptable. However, they should be used sparingly, if at all. Sometimes the shorter and sweeter syntax is not worth the decreased readability.
```
const prefersReducedMotion () => window.matchMedia("(prefers-reduced-motion)").matches ? true : false;
```

### Modules
It is recommended to break out smaller, reusable functions into their own modules. This helps reduce the length and complexity of a main script file.

```
// './util/prefersReducedMotion.js'

/**
 * Check user settings for reduced motion preferences, if available.
 * @return {boolean}
 */
const prefersReducedMotion () => {
    return window.matchMedia("(prefers-reduced-motion)").matches ? true : false;
}

export default prefersReducedMotion;
```

```
// main.js

import prefersReducedMotion from './util/prefersReducedMotion.js'

if (!prefersReducedMotion) {
    // Run this block of code.
}
```

## Libraries
JavaScript libraries must be carefully considered before they are added to any project. While they help achieve a final product, there is always an import cost associated with each library.

If possible, only import the parts you need rather than the entire library.

```
import { debounce, throttle } from 'lodash';
```

### jQuery
jQuery is a powerful library that makes performing DOM manipulation much easier. WordPress and many WordPress plugins with front-end output rely on jQuery as a dependency.

### React
React is a JavaScript library for building user interfaces. For complex and stateful interfaces, such as a collection or dynamic filtering, using React is preferred over jQuery.
