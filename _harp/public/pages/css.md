<!--

Table of Contents

* Introduction
* LESS as a Framework
	* _explanation_
	* _also support SASS and vanilla CSS if necessary_
* Basics
	* Ruleset Guidelines
		* Basic Syntax
			* _opening brace on same line as selector_
			* _one space before opening brace_
			* _properties and values on the same line_
			* _one space after colon that follows property name_
			* _each property/value declaration on its own line_
			* _each property/value declaration indented_
			* _closing brace on its own line_
		* Supplemental Syntax
			* _in rulesets with multiple selectors, each selector on its own line_
	* Classes and IDs
		* _IDs reserved for JS selectors_
		* ID Naming Conventions
			* _'#js-...'_
		* Class Naming Conventions
			*
* Organization
	* Table of Contents
	* Comments
		* Sectioning Comments
		* Descriptive Comments
	* Meaningful Whitespace
		* Between Rulesets
		* Delimiting Sections
		* Aligning Values of Related Declarations (Optional)
* File Structure
	* Overview
		* _app_
		* _normalize_
		* _tools_
		* _globals_
		* _components_
	* App
		* _table of contents, comments, and imports only&mdash;no rulesets_
	* Normalize
		* _required_
		* _imported first_

In progress...

-->

### Introduction

Cuberis projects typically use Less for CSS pre-processing. Less extends the CSS language, adding features that allow variables, mixins, functions and many other techniques that make CSS more maintainable, themable and extendable. Documentation on Less is available at [lesscss.org](http://lesscss.org).

Projects in vanilla CSS or other pre-processors such as Sass are also supported, if necessary.

Documentation for SASS can be found at http://sass-lang.com/

Cuberis' CSS standards are heavily influenced by (**but differ from**) [Harry Roberts' CSS guidelines](http://cssguidelin.es/).

The most common framework in Cuberis projects is Bootstrap, however, the is history and experience using foundation.

### Rulesets

The following terminology when discussing CSS rulesets is used at Cuberis:

	[selector] {
		[property]: [value];
	}

Property/value combinations are refered to as **declarations**.

### Basic Syntax
Cuberis has strict standards regarding how rulesets are written—for example:

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

<!---
Additionally, properties should ideally be ordered as follows (some properties omitted for brevity):

1. display
2. position
3. [dimensions]
	1. width
	2. max-width
	3. height
	4. max-height
4. [box]
	1. margin
	2. padding
	3. box-sizing
5. [positioning]
	1. top
	2. left
	3. right
	3. bottom
6.
-->

### Basic Selectors

There are six types of selectors: **element selectors**, **IDs***, **classes**, **attribute selectors**, **pseudo-class** and **pseudo-elements**.

#### ID Selectors

Selectors using IDs are not permitted in Cuberis stylesheets in order to avoid specificity issues and ensure the maintanability and extensibility of codebases over time by multiple developers. Existing classes should be used if possible, or a class should be added to the element if no suitable one exists.

IDs are reserved for targeting DOM elements with javascript. View the [javascript standards page](#) for naming conventions and more information.

#### Class Selectors

	.main-navigation {...}

1. Class names should be semantic to their function
2. Classes should be all lowercase
3. Classes needing more than one word should be hyphen delimited
4. Class names should be short, but as long as necessary to convey their purpose

Refer to the [components section](#) below for additional guidelines on class usage.

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

#### Compound Selectors

Compound selectors are selectors comprised of more than one chained selector. Selectors should be ordered by type, in the following sequence: element selectors, IDs*, classes, attribute selectors, pseudo-class and pseudo-elements.

Examples of **incorrectly** combined compound selectors:

	.navigation#main-navigation {...}
	[data-name].orange {...}

Examples of **correctly** combined compound selectors:

	p.footnote.teal {...}
	.person:nth-child(odd)::after {...}

In Less/Sass Syntax

	p {
		&.footnote {
			&.teal{
				...
			}
		}
	}
	.person {
		&:nth-child(odd) {
			&::after {
				...
			}
		}
	}

_*See section above regarding usage of IDs in Cuberis stylesheets_

### Selector Performance

CSS is evaluated from **right to left**, meaning that with a selector

### Components
There are three main types of classes—component classes, element classes and modifier classes.

**component** and **element classes** can be thought of as nouns, targeting specific elements and groups of elements (respectively) based on what they are—their identity and function.

For instance, a leadership page on an organization's website might feature headshots and titles of their leadership:

	<section>
		<header>
			<h1>Leadership</h1>
			<p>Our great leadership.</p>
		</header>

		<figure class="person">
			<img class="person headshot" ... />
			<figcaption>
				<p class="person name">Jean-Luc Picard</p>
				<p class="person title">Captain</p>
			</figcaption>
		</figure>

		<figure class="person">
			<img class="person headshot" ... />
			<figcaption>
				<p class="person name">William Riker</p>
				<p class="person title">First Officer</p>
			</figcaption>
		</figure>

		<figure class="person">
			<img class="person headshot" ... />
			<figcaption>
				<p class="person name">Geordi La Forge</p>
				<p class="person title">Chief Engineer</p>
			</figcaption>
		</figure>

		[...]

	</section>




### Main.scss

Your main.scss file should not contain any explicit attribute definitions. Rather, it should serve as a home for imported component files (e.g. buttons, lists, forms, etc) and merely assigned pre-designed library styles to explicitly-named application usages.

Your Assets directory should contain all .scss files for importing (denoted with an underscore and typically broken into subfolders) and main.scss itself. Globals should contain code written in the most abstract, reusable way possible and be written with language that denotes their visual appearance. Think of globals as your block level elements--buttons, forms, type, etc. Globals should be the only place where explicit CSS is written.

Components should integrate globals as mixins, and be written with language that denotes their "purpose" on the page. Think of components as "sections" or "parts" of a website.

Main.scss contains nothing but import statements that compile your components and globals.

Here's an example of what a \_globals file named \_buttons.scss might look like. Note that modifiers are as descriptive as possible. (Also note the parantheses with .btn, which prevents it from being output to the compiled CSS file. )

	.btn() {
		border-radius: 4px;
		padding: 1em 2em;
		background: $grey;

		&.green {
			background: $green;
		}
		&.red {
			background: $red;
		}
		&.square {
			border-radius: 0;
		}
		&.extra-padding {
			padding: 1.5em 3em;
		}
	}

This would then be used as a mixin within our \_components files. Let's say we have a button associated with a person and a button associated with a product. The person button is green and square, the product button is red and has extra padding. This is our \_person.scss file:

	.person .btn {
		.btn.green.square();
	}

and this is our \_product.scss file:

	.product .btn {
		.btn.red.extra-padding();
	}

Our main.scss file then looks something like this:

	@import("dependencies/...");
	@import("globals/\_buttons.scss");
	@import("components/\_person.scss");
	@import("components/\_product.scss");
	@import("components/\_home.scss");

This system allows for an element's display characteristics to maintain a separation between *what* it is and *how* it looks on a page. This in turn allows for maximum reusability of code because form and function are distinct.

<!--
##Nesting

The only time that nested selectors should be used is with LESS' & operator. This is useful for making modifiers children of their more general counterparts, which keeps "sibling" styles grouped together for maximum legibility and order. This may also be useful for pseudoelements (i.e. :before and :after).
-->
