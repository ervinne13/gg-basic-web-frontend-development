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

To Enable CSS using a separate `.css` file. Create a new file called `style.css` next to your html file and put the style code there:

File `style.css`
```css
h1 {
    color: green;
    font-size: 28pt;
}
```

Finally remove the previous `style` tag and replace it with:

```html
<link rel="stylesheet" href="style.css" type="text/css">
```

Now it should look something like:

File `index.html`:
```html
<html>
    <head>
        <link rel="stylesheet" href="style.css" type="text/css">
    </head>
    <body>
        <h1>I'm a generic header</h1>
    </body>
</html>
```

Note that the `href` attribute of the `link` element is a url. If your site is hosted, make sure you replace this properly with the correct URL. Ex. https://my-website.com/style.css

## Colors

Adding colors to html elements is one of the fundamental things that you will be doing throughout your career.

For example, we can create a box using a div by specifying width and height. Then that box can then be styled so that it's background color is something that we want. For example:

In your css:
```css
div {
    width: 100px;
    height: 100px;
    background-color: green;
}
```

In your markup:
```html
<div />
```

There are three different ways to specify the color.

- by name, like blue, red, green. You can see a complete list of [color names](http://www.w3schools.com/cssref/css_colornames.asp) on the w3schools website.
- using an RGB value like `rgb(255,0,0)`
- using a HEX value like `#ff0000`

## Cheating Nice Colors

Having a good design sense is important. Unfortunately, that's your instructor's weak point. If you're like him and you don't have an idea (yet) of how to create good color combinations for your websites, don't be ashamed to use tools.

The instructor personally uses [colorbook.io](http://colorbook.io/colorschemes). If not enough, take inspirations from popular websites.

## Selectors: Matching Multiple Tags

Suppose we want to have h1, h2, and h3 headers in blue, but h4, h5, and h6 headers in green? We do not have to write a separate rule for each header tag, we can write one rule that looks like this:

```css
h1,h2,h3 {
    color: blue;
}

h4,h5,h6 {
    color: green;
}
```

## Selectors: Element Ids

But what about scenarios where you have multiple elements of the same type, but want them to have different styles.

This is where the id attribute is used. Any html tag can have an id attribute, which serves as a unique identifier for that tag. In fact, the value of the id attribute must be unique throughout the file.

Consider the code below:

```html
<html>
    <head>
        <style>
            p {
                color: blue;
            }

            p#paragraph2 {
                font-size: 18pt;
            }
        </style>
    </head>
    <body>
        <h1>Hello World!!</h1>
        <p id="paragraph1">The paragraph text should be unchanged</p>
        <h2>I am not blue!</h2>
        <h1>Hello Again</h1>
        <p id="paragraph2">This is another paragraph with a different identifier.</p>
    </body>
</html>
```

To match by id, we specify #<id of the element>. The selector `p#paragraph2` means this style will be applied if an element of tag `p` with id = paragraph2 is found.

__Activity 1__

What do you think will happen if you change the second rule so that it sets the color to red? Hint, you may set the css property `color` in your rulesets to change the color of the text of an element.

What do you think will happen if we change the selector and remove p?

(See answers at the end of the lesson)

## Selectors: Classes

The id attribute points to a single element in your markup. But what if you want to match a category of elements instead? This is where classes come in handy. Example, you want a table where the background color is alternating like so:

<html>
    <head>
        <style>
            .odd {
                background-color: grey;
                color: white;
            }
            .even {
                background-color: white;
                color: black;
            }
        </style>
    </head>
    <body>
        <table width="100%">
            <tr class="odd"><td>San Miguel</td><td>50,001</td></tr>
            <tr class="even"><td>Coca Cola</td><td>21,283</td></tr>
            <tr class="odd"><td>Tupperware Phils</td><td>30,124</td></tr>
            <tr class="even"><td>Jollibee Foods Corp.</td><td>76,772</td></tr>
        </table>
    </body>
</html>

You may do this by specifying classes in each row, let's say, `odd` and `even`, then add styling based on class:

```html
<html>
    <head>
        <style>
            .odd {
                background-color: grey;
                color: white;
            }
            .even {
                background-color: white;
                color: black;
            }
        </style>
    </head>
    <body>
        <table width="100%">
            <tr class="odd"><td>San Miguel</td><td>50,001</td></tr>
            <tr class="even"><td>Coca Cola</td><td>21,283</td></tr>
            <tr class="odd"><td>Tupperware Phils</td><td>30,124</td></tr>
            <tr class="even"><td>Jollibee Foods Corp.</td><td>76,772</td></tr>
        </table>
    </body>
</html>
```

To match classes, you specify `.<name of class>`.

__Activity 2:__

If we add the element below outsite the table:

```html
<p class="odd">I'm just a paragraph</p>
```

the webpage should display a paragraph with a gray background. What if we want to make it so that it the "zebra" effect will only apply to the table?

## Selectors: Matching Children

When using the semantic html elements it is sometimes very desireable to match a particular tag, but only if that tag is in the article section. CSS allows us to match tags that are descendants of other tags by using a space after the parent tag. For example:

```css
article h1 {
    color:  purple;
}
```

Will change the color of the h1 but only if they are descendants of the article tag.

Consider the example:
```html
<html>
    <head>
        <style>
            article h1 {
                color: purple;
            }
        </style>
    </head>
    <body>
        <h1>This is outside the article</h1>
        <article>
            <h1>This is inside the article</h1>
            <section>
                <h1>This is in a section of an article</h1>
            </section>
        </article>
    </body>
</html>
```

This will be rendered so that only `h1` elements inside an `article` element is colored purple.

## CSS Property Overload

There are tons of CSS properties out there and we wont make it in time if we discuss all of them in detail (not to mention not much productive). So what do you do if you want to do something but don't know the property for it?

Again, there's no shame in googling.

Consider the example:

```html
<p class="nice-paragraph">I want to change fonts</p>
```

You want to change the font of a specific paragraph. So you will likely google:
"CSS Property for font type"

Which will result in the properties:
|-|-|
|Property|Description|
|-|-|
|font|Sets all the font properties in one declaration|
|font-family|Specifies the font family for text|
|font-size|Specifies the font size of text|
|font-style|Specifies the font style for text|

The correct answer is to use `font-family` but since we are still ignorant, we will likely see `font-style` as a good candidate. Let's click on the link to see more details and possibly samples. The reference link was [here](https://www.w3schools.com/css/css_font.asp).

Now you realize that `font-style` is for specifying italic, oblique, etc. You should be able to see `font-family` though. Bingo!

Now we can set our css to:

```css
.nice-paragraph {
    font-family: "Times New Roman", Times, serif;
}
```

This will change the paragraph's font to `times new roman`. But what if the font is not installed in the client's computer? It will then fall back to the next font `times`, if still not found, back to `serif`.

"Times New Roman" was enclosed in double quotes because it has spaces in it.

## Next Topic: CSS Layouts

Now that we know how to do basic styling, we can now move on to trying to move elements around the page. [Click here](/modules/css/css-layout.md) to go to the next lesson.