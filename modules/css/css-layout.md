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

Whenever you specify a `fixed`, `absolute`, or `relative` position, you may now set the actual positioning you want through the coordinate properties `top`, `bottom`, `left`, and `right`.

![](/img/html-coordinates.png)

To better understand positioning, let's explore some examples:

### Fixed Position Elements

Fixed element sample: [click here](/modules/css/long-samples/position-fixed.md)

__Activity 5:__

Notice that in the fixed element example, your header overlaps with the content. Find a way so that the content does not overlap anymore __even if you scroll.__

- Hint 1: Adding position fixed to the `ol` element is wrong.
- Hint 2: Review our topic on box elements
- Hint 3: After adding a solution from box elements, when you scroll, the problem will still exist. Maybe add a background color (white will do) and width may resolve it?

### Reviewing the Coordinates

![](/img/html-coordinates.png)

Remember the coordinate system we've put? What happens if you specify bottom 0px instead of top? __You may think that it would stick to the bottom of the page, but no__. Remember that the top left of the page is the coordinate 0,0. So your fixed element is now at the top of the page outside its visible area.

So it's actually difficult to fix things at the bottom of the page because you have to compute for the page size first (which varies a lot from device to device).

### Relatively Positioned Elements

Relatively positioned elements can be moved __relative to its current position__.

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

Alsy try to make the webpage narrower (just change the size of your browser) and see what happens to your markup.

__Takeaway from Activity 6__

One of the key take aways from activity 6 is that relatively positioned elements can be unpredictable in a lot of times because it's still somewhat going with the flow of elements while also doing modifications in its position. __Use this with caution.__

### Absolute Positioned Elements

Absolutely positioned elements are absolute, but relative to their container! The official rule is that absolute items are positioned using the the upper left corner of the first non-static container as the origin. If there is no non-static container, then the html tag will be used and the origin will be the upper left corner of the page.

Let's create another markup based on our sample from relative positioning:

```html
<html>
    <head>
        <style>
            img.card {
                height: 200px;
            }
            img#a {
                position: absolute;
                top: 10px;
                left: 50px;
            }
            img#b {
                position: absolute;
                top: 100px;
                left: 200px;
            }
        </style>
    </head>
    <body>
        <div>
            <div id="image-container">
                <img id="a" class="card" src="https://image.flaticon.com/icons/png/128/70/70367.png" />
                <img id="b" class="card" src="https://image.flaticon.com/icons/png/128/684/684831.png" />
            </div>
        </div>
    </body>
</html>
```

Try playing around the position to see. Remember that absolute positioned elements' position is based on its parent.

__Activity 7:__

Notice the div with id = image-container within another div? What happens if you put position absolute and some coordinates to it as well? Whatever the location/coordinates is up to you, just move it from 0,0.

### Position Summary

- __Fixed__ positioned elements stay fixed regardless of the container.
- __Relatively__ positioned elements can be moved relative to its __own__ current position
- __Absolute__ positioned elements can be moved __relative to its container or closest positioned parent.__

## Creating a Layout

Now that we've learned a lot, let's try creating a layout similiar to what we have in the desktop version of our profile page plan.

The intent here is to make us fail and try lots of workarounds when trying to lay things out before finally giving up and learning about `display: flex`. The practices in the next sections are also useful for experience and if you inherit projects that use them since `display: flex` is pretty new.

This is not yet the actual layout as the image you provide may have different width. We'll just be practicing.

Let's first start with this markup:

```html
<html>
    <head>
        <style>
            
        </style>
    </head>
    <body>
        <section class="main-screen">
            <div class="-content">

            </div>
            <div class="-right-image-container">
                
            </div>
        </section>
    </body>
</html>
```

We have `.main-screen` containing two divs, `.-content` and `-right-image-container`. We want to display `.-content` and `-right-image-container` side by side with consuming 100% height and consuming 60% and 40% of the page respectively.

Since both of them should be displayed full height, let's style their container `.main-screen`:

```css
.main-screen {
    height: 100vh;
}
```

Note that you can't actually use 100% as height as the body does not consume `100%` of the page. It's only consuming what its content consumes. We've learned that the unit `vh` though means the height of the viewport. 1vh = 1% of the visible page.

You may add in a background color to check if it really does consume the whole page, remove it afterwards though.

Next is the left and right parts of the screen, our main content should consume 60% with and 100% height of its parent (thus = 100vh). 

```css
.main-screen .-content {
    width: 60%;
    height: 100%;
    background-color: rgb(122, 122, 122);
}

.main-screen .-right-image-container {
    width: 40%;
    height: 100%;
    background-color: black;
}
```

Test it out, you'll notice that it's not as you expect. They are not aligned since the `.-right-image-container` goes to the next line. If you inspect, you should notice that by default, divs are displayed using `display: block;`. Review our lesson in relation to this and you should now deduce that we can use `display: inline-block`. The rule `display: inline` wont work as well because as mentioned, width and height does not take effect for fully inline elements. Modify your styles to:

```css
.main-screen .-content {
    width: 60%;
    height: 100%;
    display: inline-block;
    background-color: rgb(122, 122, 122);
}

.main-screen .-right-image-container {
    width: 39%;
    height: 100%;
    display: inline-block;
    background-color: black;
}
```

That should should fix it right? Still wrong.
Try setting `.-content`'s width to 59% instead or `.-right-image-container`'s width to 39%, either of the two. You'll now achieve what we want to achieve.

This solution is weird though, what happened to the remaining 1%?

The divs do not display inline with each other at 60% + 40% width because inline elements respect the (literal) whitespace between your divs in the html, as in `</div> <div>` (in this case, a new line instead of just space). That sounds silly, but that is essentially what is going on.

The space between your first `</div>` and second `<div>` create an actual gap that you can see on the page. This gap carries its own static width that must be accounted for when adding up to 100%.

With this in mind, you can essentially achieve the desired result by removing the space between your inline divs in the html.

```html
<section class="main-screen">
    <div class="-content">

    </div><div class="-right-image-container">
        
    </div>
</section>
```

This fix is awkward though, no sane person would let your code behavior be dependent awkward on whitespacing so revert that and let's find a better way. One way to "fix" this, is to add the ruleset `white-space: nowrap;` on the container element so that the white spaces don't manifest between divs.

```css
.main-screen {
    height: 100vh;
    white-space: nowrap;
}
```

The problem with this solution is that it does not remove the white-space between the divs. It just ignores it. 

#### Breaking the Flow

Try adding actual content in your markup, update it to:

```html
<section class="main-screen">
    <div class="-content">
        <h1>Ow Broken</h1>
    </div>
    <div class="-right-image-container">
        
    </div>
</section>
```

Wow, your layout is now broken beyond compare. We can try other workarounds like giving up on displaying it `block-inline` but workarounds are the work of the devil (kidding, but it usually is, it may work now, but will give you more headache later on).

Let's first try the workaround:

```css
.main-screen {
    height: 100vh;
}

.main-screen .-content {
    width: 60%;
    height: 100%;
    float: left;
    background-color: rgb(122, 122, 122);
}

.main-screen .-right-image-container {
    width: 40%;
    height: 100%;
    float: left;
    background-color: black;
}
```

We've removed display: `inline-block` and replaced it with `float: left;`.

Nice! So far it's fixed. But try adding some content after the `-content` and `-right-image-container` div:

```html
<section class="main-screen">
    <div class="-content">
        <h1>Nice, not broken</h1>
    </div>
    <div class="-right-image-container">
        
    </div>
    Some content after
</section>
```

Content does not display because it's behind the two divs. This is because they are "floating" outside the normal flow of elements.

## Finally Using Flex

Frustrating right? You solve one problem and another problem pops out. Slap in more workarounds and the problem "should" be fixed eventually. We don't want workarounds as much as possible though.

So now, the instructor wants you to remove the `float` or `display: inline-block` in the child elements and then just add `display: flex` in the parent element. The end css should look like:

```css
.main-screen {
    height: 100vh;
    display: flex;
}

.main-screen .-content {
    width: 60%;
    height: 100%;
    background-color: rgb(122, 122, 122);
}

.main-screen .-right-image-container {
    width: 40%;
    height: 100%;
    background-color: black;
}
```

That should resolve everything, even the text outside `-content` and `-right-image-container`. Even adding long text in the `.-content` works flawlessly:

```html
<div class="-content">
    <h1>Nice, not broken</h1>
    <p>Lorem ipsum, dolor sit amet consectetur adipisicing elit. Ab, pariatur autem. Hic quibusdam eius sit harum dignissimos aliquam voluptate quo necessitatibus impedit quis quam molestias alias debitis, ut unde quas?</p>
</div>
<div class="-right-image-container">
    
</div>
```

CSS Flexbox is a large topic of its own, see [here, this is the instructor's reference](https://css-tricks.com/snippets/css/a-guide-to-flexbox/). Its relatively new and was introduced just last 2017 so you will encounter code that does not yet use flexbox (thus, those bad mistakes we made earlier) if you inherit old code.

The main idea behind the flex layout is to give the container the ability to alter its items' width/height (and order) to best fill the available space (mostly to accommodate to all kind of display devices and screen sizes). A flex container expands items to fill available free space, or shrinks them to prevent overflow.

### Flexbox Basics

![](https://css-tricks.com/wp-content/uploads/2018/11/00-basic-terminology.svg)

|Terminology|Description|
|-|-|
|main axis|The main axis of a flex container is the primary axis along which flex items are laid out.|
|main-start/main-end| The flex items are placed within the container starting from main-start and going to main-end.|
|main size|A flex item's width or height, whichever is in the main dimension, is the item's main size. The flex item's main size property is either the ‘width’ or ‘height’ property, whichever is in the main dimension.|
|cross axis|The axis perpendicular to the main axis is called the cross axis. Its direction depends on the main axis direction.|
|cross-start|cross-end|Flex lines are filled with items and placed into the container starting on the cross-start side of the flex container and going toward the cross-end side.|
|cross size|The width or height of a flex item, whichever is in the cross dimension, is the item's cross size. The cross size property is whichever of ‘width’ or ‘height’ that is in the cross dimension.|

The main axis, is not necessarily just horizontal. We can actually set the axis by specifying the `flex-direction`:

#### The Flex Direction

Using the property `flex-direction`, you may change how the elements inside a flexbox is displayed.

![](https://css-tricks.com/wp-content/uploads/2018/10/flex-direction.svg)

Possible valuefor `flex-direction`:

|Direction|Description|
|-|-|
|row|(Default) going left to right|
|row-reverse| Right to left|
|column|Going top to bottom|
|column-revers|Bottom to top|

Now try adding `flex-direction` property on your `.main-screen` to see what happens.

#### Using Flex to Display Variable Width Elements

We know that our right panel (`-right-image-container`) will not have a set width of 40% but will depend on the ration of the image we upload. This is where `flexbox` will shine more. We can now remove the width property from both the panels. In fact, we can remove the whole `.main-screen .-right-image-container` as we don't need to style it, instead, we'll put `.main-screen .-right-image-container` like so:

```css
.main-screen {
    height: 100vh;
    display: flex;
    flex-direction: row;
}

.main-screen .-content {
    height: 100%;
}

.main-screen .-right-image-container img {
    height: 100%;
}
```

Flex will automatically try to find the ideal width (since we specified flex direction row) to fill all the space in it. Now, whatever the width of your image is after applying ratio depending on screen height, the `-content` will automatically adjust!

We can further simplify our css by combining the panels:

```css
.main-screen {
    height: 100vh;
    display: flex;
    flex-direction: row;
}

.main-screen .-content, 
.main-screen .-right-image-container img {
    height: 100%;
}
```

For now, we're only really concerned on laying things out by percentage so let's skip other details of flex for now. We'll revisit flex again later when we get to screens that need it.

## Laying Out Evenly

The layout for the first screen is pretty much done, we can now move on to displaying the recommendations. We plan to display 3 recommendations evenly in a horizontal fashion so what we know already works. For example, add the following:

In your styles:
```css
.recommendations-screen {
    width: 100%;
    display: flex;
    flex-direction: row;
}

.recommendation-place-holder {
    width: 25%;
    min-width: 200px;
    height: 400px;
    background-color: grey;
}
```

and in your markup:
```html
<section class="recommendations-screen">
    <div class="recommendation-place-holder"></div>
    <div class="recommendation-place-holder"></div>
    <div class="recommendation-place-holder"></div>
</section>
```

This will display 3 placeholders for recommendation component displayed as vertical rectangles. Notice that it sticks together though. This is because it's displaying content at the start:

![](https://css-tricks.com/wp-content/uploads/2018/10/align-content.svg)

We should display it instead with space between by adding the ruleset: `justify-content: space-between;`

```css
.recommendations-screen {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
```

We can also add some padding at the left and right for aesthetics by adding `padding: 0 50px;`. This is a shorthand method of defining margins so that it will display 0 margin on both top and bottom, then 50px on left and right.

```css
.recommendations-screen {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
```

You'll notice that this does not display as we intend to, the panel overflows to the right of the page. This is because despite having a padding (even a margin), the panel will still take up 100% of the width as we told it to. Flexbox's calculation does not include margin and padding, only the content inside it. The solution to this is to create another panel that has the margin (section), and inside it, another panel (div) inside it that is displayed flex. Do the following updates:

... to your css:

```css
.recommendations-screen {
    padding: 0 50px;
}

.recommendations-screen > .-container {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
}
```

... and to your HTML
```html
<section class="recommendations-screen">
    <div class="-container">
        <div class="recommendation-place-holder"></div>
        <div class="recommendation-place-holder"></div>
        <div class="recommendation-place-holder"></div>
    </div>
</section>
```

### Completing Our Layout

This will be the last area we need to layout for our online profile, our employment history.

We'll have to display the logo of the company at the left and a box containing a header and a text to the right.

We may consider each of these work experiences as articles so let's declare the markup as such:

```html
<article class="employement-history-entry">
    <img class="company-logo" src="https://helium.nuworks.ph/img/nuworks-logo-colored.png" alt="NuWorks Interactive Labs. Inc. Logo">
    <div class="-body">
        <h4>NuWorks Interactive Labs Inc.</h4>
        <strong>Role: Fullstack Developer</strong>
        <p>Provided high quality PHP (Laravel) and JavaScript (MERN) based applications depending on client needs.</p>
    </div>
</article>
```

The markup should be something like above. To be able to test well, just make sure you have a relatively long description of your role

Let's make the image rounded first, we can do that by specifying equal `border-radius` to whatever the `width` and `height` is (must be equal).

```css
.company-logo {
    width: 50px;
    height: 50px;
    border-radius: 50%;
}
```

Next we can lay the elements out. We want them to display inline-block with each other, so let's write css that will put `inline-block` to all of `.employement-history-entry`'s children:

```css
.employement-history-entry > * {
    display: inline-block;
}
```

The problem though, is that if the screen size is narrow (try resizing your webpage). We've dealt with this problem before. The solution is (again), make the parent element `display: flex`:

```css
.employement-history-entry {
    display: flex;
}
```

We're pretty much done, but before we close this, let's style the content a bit so that it can display as a box with appropriate inner spaces (padding):

```css
.employement-history-entry > .-body {
    margin-left: 20px;
    padding: 0px 15px;
    width: 500px;
}
```

The property `margin-left` is there to provide a space bet. the image while `padding` is used to enable inner spaces. We've also added a with so that it's consistent with all our other experiences. We can also add in a background image to immitate a box:

```css
.employement-history-entry > .-body {
    margin-left: 20px;
    padding: 0px 15px;
    max-width: 500px;
    background-color: #ececec;
}
```

Let's also add a subtle box shadow:

```css
.employement-history-entry > .-body {
    margin-left: 20px;
    padding: 0px 15px;
    max-width: 500px;
    background-color: #ececec;
    box-shadow: 0px 0px 56px -8px #aaaaaa;
}
```

#### Box Shadow

The possible property values of a box shadow is as follows:

```css
box-shadow: none|h-offset v-offset blur spread color |inset|initial|inherit;
```

What we just did is to provide 0 offset (adding offset will imitate a one sided shadow, try it out) so that shadow is pread around evenly like a border, then add a large blur of `56px`. The value spread = -8px is there to imitate a somewhat rounded blur. Try experimenting values of your own.

## Centering Contents

With flexbox, centering contents is also very easy. Just justify content to center and you're good to go:

```css
.employement-history-entry {
    display: flex;
    justify-content: center;
}
```

For aesthetics, also add some margin at the top of the panel:

```css
.experience-screen {
    margin-top: 30px;
}

```

And we're pretty much done. You may add in more of your experiences if you want.

## Next Lessons

We now know quite a lot about HTML and CSS already so we may proceed on actually creating our components now. In fact, we already did one: work history.

Our next lesson should be designing these components individually. Ideally, we'll use something like storybook for this but since we're pressed in time, let's settle on the good old fashion way.

[Click here to view the next lesson](/module/css/desigining-components.md)