## Introduction

Let's face it, the web is built with HTML and we write a ton of it 👨‍💻. So let's aim write it well! Besides, who wants to wade through a sea of `<div>`s all day!

## Semantics
When writing HTML markup, semantics are very, very important. Semantics actually give meaning to your markup which helps with readability, maintainability, accessibility and other benefits. Elements should be used for their intended semantic purpose, i.e. a `<nav>` element for a menu instead of a `<div>`, a `<button>` for a button, or an `<article>` tag for a blog post. An example of good semantics:

```
<article class="post">
  <header class="post-header">
    <h2 class="post-title">The Title</h2>
    <time class="post-date">April, 26, 2019</time>
  </header>
  <p>The content</p>
</article>
```

An example not using semantics:

```
<div class="post">
  <div class="post-header">
    <h2 class="post-title">The Title</h2>
    <div class="post-date">April, 26, 2019</div>
  </div>
  <p>The content</p>
</div>
```

### Source Order (Mobile first 🙌)
As a general rule, the mobile layout should determine the order of our HTML markup. Then for larger screens, elements get positioned accordingly via floats, flex-order, position, etc. This allows content to flow naturally for mobile and also improves accessibility for screen readers and ensures content is read in a logical fashion.

## Accessibility (A11y)

Simply put, accessibility is the practice of making your websites usable by as many people as possible. This largely includes those with disabilities, but also the average user who simply likes using his keyboard to tab through a form. We believe every project should be built with accessibility in mind. Regardless of if there are any strict project specific requirements, a11y enhancements should be considered to help all users, not just those who are impaired.

### Assistive Technologies

As a general rule of thumb, users should be able to navigate and use a website using only their keyboard or a screen reader without much difficulty.

### Images

All images should have an `alt` attribute. Decorative images or icons are hidden from assistive technologies using either `aria-hidden="true"` or `alt=""`.

### Headings

Pages should use a logical heading structure and should always start with `<h1>` which is typically reserved for the title. Similarly, an `<h3>` heading should never follow an `<h1>`, you would need an `<h2>`. Styling should never be tied directly to the heading tags as there should never be a temptation to use a heading based on how it looks, instead by semantics.

### Other Resources
- [A11y Project](https://a11yproject.com/)
- [Awesome A11y](https://github.com/brunopulis/awesome-a11y)
- [Color Contrast Calculator](https://contrast-ratio.com/)
- [HTML CodeSniffer](https://squizlabs.github.io/HTML_CodeSniffer/)
- [Testing using a Screen Reader](https://webaim.org/articles/voiceover/)

## IDs and Classes

In most cases, classes should be used for styling and IDs should be used for targeting with JavaScript. In the case where you need to target multiple elements on a page with your JS, prefixing the class name with `js-` is recommended.

## Images & Icons

All images should be optimized for web and sized appropriately. For logos and illustrations, we prefer SVG as it is always crisp and clean and if inline, can be easily animated with CSS.

### Responsive Images & Backgrounds

Wherever possible, images (including background images) should be responsive to the screen size they are displayed on. This means that smaller screens should never load the same image size as desktop screens. Whether this is using `srcset` attributes or `<picture>` elements, we leave up to the discretion of the developer.

## Other Recommendations

### Elements with many attributes

For elements that have more than ~3-4 attributes, write each on their own line. Example:

```
<div
  aria-live="polite"
  class="posts-wrapper"
  data-bg="my-image.jpg"
  data-category="my-category"
  data-per-page="10"
  id="postsWrapper"
>
```