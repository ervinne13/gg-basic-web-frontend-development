# Responsive CSS Layouts

We'll create a quite generic solution for this - a grid system. Essentially: imagine you have an element with an unknown number of children. Each of those children is some percentage of the width of parent such that they make equal rows, like 25% wide each for four columns, 33.33% wide each for three columns, etc. The goal is to fill the space of this "grid" evenly. There are an unknown number of children, so let's say you were going with 25% and there were 7 children, that would be 4 in the first row and 3 in the second.

## Grid system

We'll pretty much immitating what a framework like bootstrap can already do. We'll learn how to implement our own grid system from scratch. A grid system would typically look something like:

![](https://a8q8p3f5.stackpathcdn.com/wp-content/uploads/2015/07/Bootstrap-grid.png)

We will make use of our knowledge in flexboxes to create a generic grid system. Consider (and write up) the following html code:

```html
<html>
    <head>
        <style>
        </style>
    </head>
    <body>
        <div class="container">
            <div class="row">
                <div class="col">
                    I'm a content inside a 1/3 size column
                </div>
                <div class="col">
                    I'm a content inside a 1/3 size column
                </div>
                <div class="col">
                    I'm a content inside a 1/3 size column
                </div>
            </div>
        </div>
    </body>
</html>
```

All columns (specified by a `col-x` class) are wrapped in a row and one container. Then add the following styles:

```css
.container {
    max-width: 1335px;
    margin: 0 auto;
}

.container .row {
    display: flex;
}

.container .row .col {
    display: flex;
}
```

You could create different behaviors per row with different `justify-content` values for the `.row` container. Try the following out:

- flex-start (default)
- flex-end
- center
- space-between
- space-around