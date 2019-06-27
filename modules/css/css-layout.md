# CSS Layout

Remember the semantic elements?

![](https://www.w3schools.com/html/img_sem_elements.gif)

To be able to pull something like this off, we need to be able to understand how the CSS box model works first.

## CSS Box Model

![](https://helpx.adobe.com/content/dam/help/en/dreamweaver/how-to/make-website-pt5-css-style/_jcr_content/main-pars/image_1080546963/fig01.jpg)

Every HTML element can be visualized like a "box". Each box has its own width and height. Additionally, elements have `padding`, `border`, and `margin`.

The different parts of the box model are defined as follows:

- Content: The actual text or image content of an html tag
- Padding: The space between the content and the border.
- Border: This can be an actual drawn border or it can be invisible
- Margin: The space outside the border between this box and the boxes next to it in each direction.

Let's try a simple example:

```html
<html>
    <head>
        <style>
            section {
                width: 250px;
                background-color: green;
                padding: 25px;
                border: 10px solid blue;
                margin: 25px;
            }
        </style>
    </head>
    <body>

        <section>Hello World</section>
        <section id=b>Hello World</section>

    </body>
</html>
```

As a bit of review, add a rule to the example above to make the margin for the second Hello world to be 5px. What does this tell you about how margins work?

The size of content area itself can also be controlled using the following properties:

- height
- max-height
- min-height
- width
- max-width
- min-width

Each of these properties can be specified in terms of pixels (px), points (pt), or as a percentage. In addition the auto keyword can be used, which is the default and allows the browser to figure out the proper height and width.

__Granular Control__

The properties `border`, `padding`, and `margin` can have individual areas controlled just by adding `-left`, `-right`, `-top`, or `-bottom` to them.

For example, you may create an element that only has a margin top on it:

```css
some-element-class {
    margin-top: 50px;
}
```

Remember this as this may come in handy later in other activities :)

__Inspecting the Box Model__

Follow along the instructor as he demonstrates how to view the box model of existing html elements in the browser using Google Chrome.

Note:
Shortcut: `F12` or Right Click then "Inspect Element".

## Box Model Overflows

When you use height and width with a container element, such as one of the semantic elements, it is very useful to know about the overflow property. What if you set your height so small that the content does not fit? The overflow property tells you how to handle that.

```html
<html>
    <head>
        <style>
            section {
                width: 250px;
                color: black;
                background-color: lightgrey;
                padding: 25px;
                border: 10px solid blue;
                margin: 25px;
                height: 100px;
            }
        </style>
        </head>
        <body>
            <section>
                <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum.
                </p>
            </section>
        </body>
</html>
```

The `section` element follows the dimensions you just set. However, its content overflows because it's too large to fit. To "fix" this, we can explore the possible values of the `overflow` property:

- visible
- hidden
- scroll
- auto

__Activity 3:__

In your CSS, update the `section` tag's `overflow` property and test each 4 values above.

## Length Units

Now that we know about overflows, its time we really understand the units of measurement we've been using.

### Absolute Units

So far, we've been using absolute units. These units are representation of actual measurement in the physical world. The units `px`, `mm`, `cm`, `in`, `pt` and `pc`.

|Unit|Description|
|-|-|
|cm|centimeters|
|mm|millimeters|
|in|inches (1in = 96px = 2.54cm)|
|px|literal pixels of the screen or  (1px = 1/96th of 1in)|
|pt|points (1pt = 1/72 of 1in)|
|pc|picas (1pc = 12 pt)|

### Relative Units

These units don’t have fixed values but instead are relative to something else.

|Unit|Description|
|-|-|
|%|We'll use this a lot. % relative to its parent|
|em|Relative to the font-size of the element (2em means 2 times the size of the current font)|
|rem|Relative to font-size of the root element|

Here are also units that are rarely used, use this as reference.

|Unit|Description|
|-|-|
|ex|Relative to the x-height of the current font|
|ch|Relative to width of the "0" (zero)|

## Viewport relative Units

We'll discuss this in more detail later when we get to responsive design. For now, think of this as the user's visible area of a web page which varies with the device (smaller on mobiles, larger on the computer screen).

|Unit|Description|
|-|-|
|vw|Relative to 1% of the width of the viewport*|
|vh|Relative to 1% of the height of the viewport*|
|vmin|Relative to 1% of viewport's* smaller dimension|
|vmax|Relative to 1% of viewport's* larger dimension|

This is not only used for layouts, but also for fonts (ie: some designs may require larger font for larger screens).

## The Display Property

With CSS you can take control of how each element is layed out on the page. You can hide elements, you can make block elements inline, and inline elements block. There are two ways to control the visibility of an element. You can completely hide it, as if it is not there and takes up no space on the page, or you can have the leave the space on the page, but it will not have anything in it.

Consider the code below:
```html
<html>
    <head>
        <style>
            h1.gone {
                background-color: #bbbbbb;
                display: none;
            }
        </style>
    </head>
    <body>
        <h1>Hello World One</h1>
        <h1 class="gone">Hello World Two</h1>
        <h1>Hello World Three</h1>
        <h1 class="gone">Hello World Four</h1>
        <h1>Hello World Five</h1>
    </body>
</html>
```

For the purpose of hiding and shoping, display can be any of the following:

|Display|Purpose|
|-|-|
|show|Default visibility|
|none|Removes all trace of the element and its children|
|hidden|Used for when you want to hide an element, but make it take the space up anyway (Test it out on your own)|

There are lots of other possible display values. We'll discuss some of them as well:

### Display for Controlling Flow of Text/Children

|Display|Purpose|
|-|-|
|inline|Displays an element as an inline element (like `<span>`). __Any height and width properties will have no effect.__
|block|	Displays an element as a block element (like `<p>`). It starts on a new line, and takes up the whole width|

Consider the following example:

```html
<span>I'm naturally inline, anything after me will be added "in line"</span> Some text outside the span
<p>I'm naturally displayed as "block". I'll be displayed on a new line, additionally, text outside my own will be on another line as well.</p> This text is outside p
```

We can manually create inline and block elements with css as we discovered in usage of the `display` property:

```html
<div>
    Elements are normally inline
    <img src="https://image.flaticon.com/icons/png/128/1077/1077976.png">
    <img src="https://image.flaticon.com/icons/png/128/1077/1077976.png">
</div>

<div>
    But if we put "block" display on them, they're now as if they're paragraphs
    <img style="display: block" src="https://image.flaticon.com/icons/png/128/1077/1077976.png">
    <img src="https://image.flaticon.com/icons/png/128/1077/1077976.png">
</div>
```

There's also `inline-block` elements:

|Display|Purpose|
|-|-|
|inline-block|Displays an element as an inline-level block container. The element itself is formatted as an inline element, but you can apply height and width values|

For a better visualization, see below:

![](/img/display-property.png)

### Other Display Values

We are also concerned about `flex`, this will take it's own session though after we learned the basics.

You may see all other values in this [link](https://www.w3schools.com/cssref/pr_class_display.asp).

## Floating

The CSS float property allows us to push HTML elements to the left or right, so that other elements will wrap around them. This can be extremely useful for images, but will also be very useful when we begin to work on more complex layouts for our pages. Lets begin with a simple example.

```html
<html>
   <head>
      <style>
      </style>
    </head>
<body>
    <p>the quick brown fox jumped over the lazy dog.  the quick brown fox jumped over the lazy dog.  the quick brown fox jumped over the lazy dog.  <img src="https://mobilelegends.gcube.id/wp-content/uploads/sites/6/2017/12/Mobile-Legends-Items-Magic-3-Calamity-Reaper.png" /> the quick brown fox jumped over the lazy dog. the quick brown fox jumped over the lazy dog. the quick brown fox jumped over the lazy dog.
    </body>
</html>
```

Notice that the logo appears right in the middle of the text in its normal inline flow. Now, add a CSS rule for an img tag that sets the float property to left. Then change the rule to float the image to the right.

__Activity 4:__

Add style so that the `img` will have the rule set: `float: left`. Create another image and this time, apply `float: right`. 

Hint: Review CSS selectors (classes) so that you can have two `img` tags with different css rules.

The float property can also be applied to block elements. This will cause the block elements to behave more like inline elements.

## Positioning

There are several different ways to affect the positioning of html elements either inside or outside of the normal flow of the layout.

|CSS Position|Description|
|-|-|
|static|This is the default positioning value for the css position property. The static value simply tells the browser to position this element in the “normal flow” of the document.|
|fixed|Fixed positioning is measured against the frame of the browser window. Elements with a fixed position value do not move even when the contents of the browser window are scrolled. The navigation bar at the top of a webpage uses the fixed position value so it is always visible. Because fixed elements are outside the flow of the document they can sometimes cause unexpected results that you have to deal with carefully.|
|relative|A relatively positioned element is measured relative to its normal position in the flow. Using a relative position value lets you create elements that overlap each other.|
|absolute|An absolute element is positioned relative to the first parent element that has a position other than static. If no such element is found, the containing block is the html tag for the entire document. Absolutely positioned elements are positioned outside the normal flow of the document.|

If you understood correctly, you should be wary of using both `fixed` and `absolute` as they distrupt or go out of the normal flow of elements in an HTML document.

To better understand positioning, let's explore some examples:

### Fixed Position Elements

Fixed element sample: [click here](/modules/css/long-samples/position-fixed.md)

__Activity 5:__

Notice that in the fixed element example, your header overlaps with the content. Find a way so that the content does not overlap anymore __even if you scroll.__

- Hint 1: Adding position fixed to the `ol` element is wrong.
- Hint 2: Review our topic on box elements
- Hint 3: After adding a solution from box elements, when you scroll, the problem will still exist. Maybe add a background color (white will do) and width may resolve it?

### Relatively Positioned Elements

Let's get some images (at least 3) from the internet and have them stack at each other. You may use the following:

- `https://image.flaticon.com/icons/png/128/70/70367.png`
- `https://image.flaticon.com/icons/png/128/684/684831.png`
- `https://image.flaticon.com/icons/png/128/1077/1077976.png`

Then add them in a markup and put ids `a`, `b`, and `c` on them.

```html
<html>
    <head>
        <style>
            img.card {
                height: 200px;
            }
        </style>
    </head>
    <body>
        <img id="a" class="card" src="https://image.flaticon.com/icons/png/128/70/70367.png" />
        <img id="b" class="card" src="https://image.flaticon.com/icons/png/128/684/684831.png" />
        <img id="c" class="card" src="https://image.flaticon.com/icons/png/128/1077/1077976.png" />
    </body>
</html>
```

Right now, if you run the code:

- The images are inline elements and so do not create a line break.
- The browser lays out inline images top to bottom and left to right.

Let's try adding the css rule:
```css
img#b {
    position: relative;
    top: 100px;
    left: -100px;
}
```

Great, now we have made the second card appear to be on top of the first. Notice that although we have moved the second image, the position of the third image does not change. This is because space is still reserved for the second image in its middle position, we are manually moving it relative to where it would normally be in the flow. So a relative positioning works within the flow of the document. 


__Activity 6:__

On your own, add a rule for the third image to add it to the stack. They should appear as if they are cascading.

Hint: to actually cascade, you might have to use a larger `top` coordinate.