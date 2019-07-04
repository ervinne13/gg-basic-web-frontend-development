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
                    <div class="box">asdf</div>
                </div>
                <div class="col">
                    <div class="box">adsf</div>
                </div>
            </div>
        </div>
    </body>
</html>
```

All columns (specified by a `col` class) are wrapped in a row and one container. Then add the following styles:

```css
.grid-container {
    max-width: 1280px;
    margin: 0 auto;
}

.container .row {
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

For our purposes, let's use `space-between`