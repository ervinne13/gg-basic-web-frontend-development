# Introduction to CSS

CSS or Cascading Style Sheets are documents to write our styling so that it will not clutter our html code.

In the previous lessons, we've learned how to add styles directly to elements by putting "rule sets" to `style` attribute of a tag. In CSS, we use a "selector" instead.

A basic syntax should look something like:

```css
selector {
    ruleset;
    ruleset;
    ...
}
```

## CSS Selectors

A CSS selector points out which part of the HTML markup will the following rulesets (enclosed in curly braces { ... }) will apply to.

Consider the CSS code below:

```css
h1 {
    color: green;
    font-size: 28pt;
}
```

Extra: [pt vs px](https://graphicdesign.stackexchange.com/questions/199/point-vs-pixel-what-is-the-difference)

And a snippet of HTML code:

```html
<h1>I'm a generic header</h1>
```

This will generate a green header that's `28pt`s big.

## Enabling CSS

CSS can be written at the same file as the HTML code or outside. It's usually acceptable to write CSS on the same HTML code if the CSS is very small anyway. Otherwise, create a separate CSS file for it.

To enable CSS on the same HTML file, consider the example:

```html
<html>
    <head>
        <style>
            h1 {
                color: green;
                font-size: 28pt;
            }
        </style>
    </head>
    <body>
        <h1>I'm a generic header</h1>
    </body>
</html>
```

CSS must be wrapped in `<style>` tags inside the `<head>` to work. THis will then generate a page with a green header. Try it out.