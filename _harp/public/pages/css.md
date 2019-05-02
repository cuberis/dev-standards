## Introduction

Our preferred method of writing CSS is using [Sass](https://sass-lang.com/), a CSS pre-processing language that allows you to use variables, nested rules, functions and more. This helps keep large stylesheets well-organized in smaller files as well as improving maintainability for the life of a website.

## Frameworks

We use [Bootstrap](https://getbootstrap.com/) for our framework of choice. New projects start out on version 4+, however, we have a number of older sites that run [version 3](https://getbootstrap.com/docs/3.4/).

### Utility Class Frameworks

For some projects, it makes sense to adopt a utility-class-first approach. In those instances, our go-to is [Tachyons](https://tachyons.io/) 🔥!

## CSS & Sass Guidelines

### General Guidelines

1. Avoid complex nesting. A good rule of thumb is do not nest more than 3-4 levels deep). While it is convenient when writing, often times it is trickier to maintain and debug.
2. Avoid long blocks of nested rules. If a block extends past the length of your editor's window for instance, you lose context of what the parent selector was since you can no longer see it.
3. While we do not enforce a strict naming methodology (i.e. BEM, OOCSS, SMACSS, etc.), be specific with your class names so it is clear what they are for.
4. Don't feel forced to name everything! In a lot of cases utility classes work just fine!

### Rulesets

The following terminology is used when referencing CSS rulesets:

	[selector] {
		[property]: [value];
	}

Property/value combinations are refered to as **declarations**.

### Basic Syntax

Rulesets are written as follows:

	.feature-story,
	.blog-post {
		display: inline-block;
		position: relative;
		width: 25%;
		margin: 2rem 0;
		background: url("../images/durham.jpg");
	}

You'll notice the example above follows these guidelines:

1. In rulesets with multiple, comma-delimited selectors, each selector is on its own line
2. The opening bracket is on the same line as the last selector, separated from the last selector by a single space
3. Property/value declarations each appear on a single line
4. Each property/value declaration is indented once
5. The closing brace is on its own line
6. The closing brace is at the same indent level as the selector(s)
7. Double quotes are used for strings

### Basic Selectors

There are six types of selectors: **element selectors**, **IDs***, **classes**, **attribute selectors**, **pseudo-class** and **pseudo-elements**.

#### ID Selectors

ID selectors are discouraged in order to avoid specificity issues. Existing classes should be used if possible, or a class should be added to the element if no suitable one exists.

IDs should generally be reserved for targeting DOM elements via JavaScript. View the [JavaScript page](#) for naming conventions and more information.

#### Class Selectors

	.main-navigation {...}

1. Class names should be semantic to their function
2. Classes should be all lowercase
3. Classes needing more than one word should be hyphen delimited
4. Class names should be short, but as long as necessary to convey their purpose

#### Attribute Selectors

	[data-region^="local"] {...}

1. If attribute an attribute selector has a value, the value should be in double quotes

#### Pseudo-Class

	selector:hover {...}

1. Pseudo-class should be delimited by a single colon
2. If a pseudo-class has a value, the value (even if it is a string, such as "odd") should **not** be wrapped in quotes

#### Pseudo-Elements

	selector::after {...}

1. Pseudo-elements should be delimited by **two** colons

## main.scss

Our typical project structure includes one `main.scss` file that contains nothing but import statements to compile your partial Sass files. Partial files are prefixed with an underscore and typically broken into subfolders.

Our `main.scss` file then looks something like this:

```
// Variables (i.e. colors, fonts, etc.)
@import("base/variables");

// Global styles
@import("base/global");

// Layout specific styles
@import("layouts/person");
@import("layouts/product");
@import("layouts/home");
```

## Other Resources

- [Harry Roberts' CSS guidelines](http://cssguidelin.es/)
- [Sass Basics](https://sass-lang.com/guide)