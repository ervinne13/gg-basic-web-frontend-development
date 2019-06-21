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

Activity 3: 

In your CSS, update the `section` tag's `overflow` property and test each 4 values above.