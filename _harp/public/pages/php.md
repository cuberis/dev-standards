## Introduction

Since Cuberis primarily builds on WordPress, our PHP standards, for the most part, follow the [WordPress Coding Standards](https://codex.wordpress.org/WordPress_Coding_Standards). PHP code should be well documented and easy to read so that code is easily debugged, extended and maintained.

## Documenting

### PHP code should be self documenting

For ease of readability, variable names should visually represent their purpose. Do not use abbreviations or letters for variable names without good reason.

```
// Good
$background_image = '/path-to-my-image.jpg';

// Bad
$bi = '/path-to-my-image.jpg';
```

Well written PHP should almost read as easy as reading a sentence.

```
// Good
foreach ( $images as $image ) {
  $background_is_enabled = $image['has_bg'];
  if ( $background_is_enabled ) {
    $class_name = 'bg-enabled';
  }
}

// Bad
foreach ( $a as $b ) {
  $bg = $image['has_bg'];
  if ( $bg ) {
    $c = 'bg-enabled';
  }
}
```

### Doc Blocks

Every function must be documented with a doc block. The more descriptive the better.

```
/**
 * My function name.
 * Any helpful notes about what this function can
 * go here. Line length should be kept relatively short
 * to avoid line breaks on smaller screens.
 *
 * @param  string $var_one Description goes here.
 * @param  array  $var_two Description goes here.
 * @return string          What gets returned.
 */
function my_function_name( $var_one, $var_two ) {
```

_Notice how everything lines up!_ 💪

## PHP In HTML

When writing HTML in PHP blocks, close your php and indent HTML on a new line. This way, if you need to adjust the markup, you don't have to shift your PHP around. PHP blocks should be indented to match the surround HTML code. Closing PHP blocks should match the same indentation level as the opening block.

```
// Good
<?php if ( boolean ) : ?>
  <div class="col">
    <?php foreach ( $things as $thing ) : ?>
      <div>
        <h2>Hello World</h2>
      </div>
    <?php endforeach; >
  </div>
<?php endif; ?>


// Bad
<?php if ( boolean ) { ?>
  <div class="col">
    ...
  </div>
<?php } ?>


// Bad
<?php
if ( boolean ) {
  echo '<div class="col">';
  foreach ( $things as $thing ) {
    echo '<div>';
    echo '<h2>Hello World</h2>';
    echo '</div>';
  }
  echo '</div>';
} ?>


// Avoid doc syntaxes all-together
echo <<<HTML
<div class="test {$a}">test</div>
HTML;
?>
```

## Naming Things

Function names should be all lowercase and classes should be Pascal cased, both with underscores between words. Class methods and vars should also be all lowercase with underscores. Additionally functions and methods should be descriptively named according to what they do.

```
// A function
function get_background_image_url() {
  ...
}

// A class
class My_Awesome_Class {

  public $my_var;

  public function my_method() {
    ...
  }

}
```

Variables should be named in such a way that makes it easy to understand what it contains. In the below example, if we have a variable named `$post_id`, it is immediately clear this is the id of a post. Whereas, if it was just named `$p`, you could not be sure if it was the entire post object or just the id itself. In long complex code structures, this becomes incredibly important for readability and debugging.

```
// Good
$post_id = get_the_ID();

// Bad
$p = get_the_ID();
```

## Other Best Practices

```
// Declare your variables close to where they are first used
$var = '';
if ( boolean ) {
  $var = 'string';
}


// Ternary operators are preferred over if/else or switch where possible
$body_class = ! empty($array) ? 'my-class' : '';
```

## Never, ever...

```
// Never use PHP short tags. These have to be explicitly enabled
// for the server to correctly parse them. If not enabled, this
// code can produce a fatal error.
<? echo 'something'; ?>
```