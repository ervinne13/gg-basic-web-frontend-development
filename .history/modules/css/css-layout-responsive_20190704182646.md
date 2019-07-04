# Responsive CSS Layouts

We'll create a quite generic solution for this - a grid system. Essentially: imagine you have an element with an unknown number of children. Each of those children is some percentage of the width of parent such that they make equal rows, like 25% wide each for four columns, 33.33% wide each for three columns, etc. The goal is to fill the space of this "grid" evenly. There are an unknown number of children, so let's say you were going with 25% and there were 7 children, that would be 4 in the first row and 3 in the second.

## A Basic Grid system

We'll pretty much immitating what a framework like bootstrap can already do. We'll learn how to implement our own grid system from scratch. A grid system would typically look something like:

![](https://a8q8p3f5.stackpathcdn.com/wp-content/uploads/2015/07/Bootstrap-grid.png)

We will make use of our knowledge in flexboxes to create a generic grid system. Consider (and write up) the following html code:

```html
<html>
    <head>
        <style>
            .box {
                background-color: grey;
                width: 100%;
                min-height: 100px;;
            }
        </style>
    </head>
    <body>
        <div class="grid-container">
            <div class="row">
                <div class="col">
                    <div class="box">I'm box 1</div>
                </div>
                <div class="col">
                    <div class="box">I'm box 2</div>
                </div>
                <div class="col">
                    <div class="box">I'm box 3</div>
                </div>
            </div>
        </div>
    </body>
</html>
```

All columns (specified by a `col` class) are wrapped in a row and one container. Then add the following styles:

```css
.grid-container {
    max-width: 1440px;
    margin: 0 auto;
}

.grid-container .row {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
}
```

You could create different behaviors per row with different `justify-content` values for the `.row` container. Try the following out:

- flex-start (default)
- flex-end
- center
- space-between
- space-around

For our purposes, let's use `space-between` for our row. Note that the property `flex-flow` is just a shortcut for `flex-direction` + `flex-wrap`. You may review flex direction on our lesson on basic css layout. As for flex-wrap, we'll be needin this later on when we apply dynamically changing `flex-basis` so just keep this in mind and we'll go back to this later on.

Now, let's create the actual columns, add the following to your styles:

```css
.grid-container .row .col {
    flex-basis: 33.33%;
    width: 259px;
    padding: 10px;
    box-sizing: border-box;
}
```

__`flex-basis: 33.33%;`__

This will enable us to display the the columns by 3 every row.

__`width: 259px;`__

Width is just there for some browsers that require a width to be defined. It's not actually used though as the actual width is determined by `flex-basis`.

__`box-sizing: border-box;`__

Padding is self explanatory but what about border sizing. Try removing this line. You should notice that "Box 2" is pushed to the right and "Box 3" now on the next line. This is because flex-basis is using the width of the element in the computation. Remember your box model? The width is the actual space consumed by your content outside the padding.

__The ruleset `box-sizing: border-box;` makes it so that the width of the element will include the padding. This way, we can put padding to our content while not interfering with the flexbox flex-basis.__

## Making the Grid Responsive

If you try reducing the size of your webpage, the columns stay on the same row. What we can do is make use of what we've learned earlier and combine them. Create media queries and adjust the `flex-basis` accordingly. Add the following code to your style:

```css
@media(max-width: 1440px) {
    .grid-container .row .col{
        flex-basis: 33.33%;
    }
}

@media(max-width: 600px) {
    .grid-container .row .col{
        flex-basis: 100%;
    }
}
```

This will make it so that if the screen is `601px` wide or more (until `1440px`), the columns will stay on the same row, but if the screen is now only `600px` wide or less, set `flex-basis` to 100% to let the columns consume all the space. Effectively making it responsive.

Note that a limit of `1440px` is set there so that it would just generate space on each side instead of stretch when the screen is too wide.

As you've guessed, this will be used later on for our recommendations screen.

## Responsive Screen for Non Uniform Width Elements

Our screen 1 is probably the trickiest to do, but it's not so hard to do with flexbox. The left panel should fill the remaining space left by the image to the right.

For example:

```html
<html>
    <head>
        <style>
            body {
                font-family: "Segoe UI", Arial, sans-serif;
            }

            .main-screen {
                width: 100%;
                height: 100vh;
                display: flex;
                flex-direction: row;
            }

            .hero-title {
                font-family: "Segoe UI Semibold";
                font-size: 65px;
            }

            .main-screen .-content {
                padding: 120px 75px;
            }

            .main-screen .-content, 
            .main-screen .-right-image-container img {
                height: 100%;
            }

        </style>
    </head>
    <body>
        <section class="main-screen">
            <div class="-content">
                <span class="hero-title">
                    Hi!
                    <div>I'm Ervinne</div>
                </span>
                <h1></h1>
            </div>
            <div class="-right-image-container">
                <img src="https://github.com/ervinne13/gg-php-w-laravel-workshop/blob/master/img/Sodusta,%20Ervinne.jpg?raw=true">
            </div>
        </section>
    </body>
</html>
```

The image is left at the center of the page because the `-content` part of the page only consumes so much. To make it span the rest of the page just add a `flex: 1` ruleset (shortcut for `flex-grow: 1`) to it so that it will consume all the space left by the image:

```css
.main-screen .-content {
    flex: 1;
    padding: 120px 75px;
}
```

### Removing the Image for Small Screens

In our mocks, we don't display the image for phones. To hide it when the screen is small, we're going to add a media query to hide it when the screen reaches a certain width limit. Let's set it to the same limit as our grid, `600px`:

```css

```