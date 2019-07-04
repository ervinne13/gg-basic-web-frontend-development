# Designing the Components

This section will be part of your practical activities. Here, we will be designing each of the components individually without the layout. We will only really "stitch" once everything is done.

First off, we'll have to learn some more techniques like adding fonts and separating css.

## Adding Fonts

In our mocks, you can see that the font we've used is "segoe ui". To make use of these fonts, add the ruleset `font-family: "Segoe UI"` to your target element.

```css
body {
    font-family: "Segoe UI";
}
```

Adding it to the body of your markup will make this font the "default".

## Fallback Fonts

Fonts may or may not be available on your users devices. So in what situation would a browser not have the font you're asking for? That's pretty common. There are only a handful of fonts that are considered "web safe"—meaning that it's likely most computers visiting your site have that font installed and so the browser can use it. Think: Arial, Times New Roman, Courier, Georgia, Verdana, and a handful of others.

To enable a "fallback" font, just specify multiple fontts in your `font-family` property:

```css
body {
    font-family: "Segoe UI", Arial, sans-serif;
}
```

Note that "Segoe UI" is wrapeed in double quotes because it has spaces in it.

## External CSS Files

Now before we move on to working on our components, let's first learn how to load external css files.

In your project, create a folder called `assets/css` and inside it, a file called `style.css`. Paste the following code inside it:

```css
body {
    font-family: "Segoe UI", Arial, sans-serif;
}
```

Then create a markup at the root of your project called `index.html` (or call it whatever you like, as long as it's extension is .html) and put the following contents:

```html
<html>
    <head>
        <link rel="stylesheet" type="text/css" href="assets/css/style.css">
    </head>
    <body>
        <p>I'm a paragraph with Segoe UI font.</p>
    </body>
</html>
```

Notice that the `style` tag is replaced with a `link` tag that points to the css file we just created earlier.

Note that this is unrealiable! This is pointing to a file relatively from where it's currently located. Ideally we'll put the actual url of the file here or at least put `/` IF we are sure about how this file will be uploaded. We can resolve this later on with webpack after we learn JavaScript.

## Designing Components: Icon Box Links

After importing the actual boxes from your mocks, add them to your projects directory in a folder called `assets/svg`.

Then create the following markup:

```html
<a href="https://www.facebook.com/ervinne.sodusta">
    <img src="assets/svg/facebook.svg">
</a>
```

(On your own, do the same for linkdin and github).

## Designing Components: Testimonial

Write up our initial markup in a new file called `recommendation.html` with the following content:

```html
<html>
    <head>
        <link rel="stylesheet" type="text/css" href="assets/css/style.css">
        <link rel="stylesheet" type="text/css" href="assets/css/recommendation.css">
        <style>
            body {
                width: 300px
            }
        </style>
    </head>
    <body>
        <article class="recommendation">
                <img class="-circle" src="https://randomuser.me/api/portraits/women/60.jpg" alt="Profile Image">
                <div class="-body">
                    <span class="-name">Doris Tumulak</span>
                    <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Necessitatibus animi nemo atque commodi explicabo! Doloribus nobis magnam est nesciunt illum inventore adipisci enim autem minus fugiat eos, corrupti, quia rem.</p>
                </div>
        </article>
    </body>
</html>
```

Note that the body width is there to immitate a small container since we are rendering only the recommendation component. Also notice the new file it's referencing: `recommendation.css`, create that file.

Now first thing is to make the image circular, based on our mocks, we should set the dimensions to `128px` evenly and its border radius to `64px` so let's do that. Open `assets/css/style.css` and add:

```css
img.-circle {
    width: 128px;
    height: 128px;
    border-radius: 64px;
}
```

Next is to update the name to its appropriate style from the markup, it should be bold and greyish. This time, open `assets/css/recommendation.css` file and add:

```css
.recommendation .-name {
    font-weight: bold;
    color: #B8B8B8;
}
```

Note that anything that seems generic (a circular image) should be written on our generic `style.css` file, that's why we separated the other markup earlier.

We'll also need to add appropriate paddings in the body:

```css
.recommendation .-body {
    padding: 24px;
    padding-top: 88px;
}
```

Why `padding-top: 88px;`? This is because we will be placing the image at the top of this box later on, half of it (`64px`) will consume the box, and the other `24px` is what we want the space of the text and the image to be, hence 64 + 24 = `88px`.

Next is to make it so that the body of the recommendation looks like a box with shadow. We can do that by following the mocks with (add this in the `style.css` instead):

```css
.shadowed {
    box-shadow: 0px 0px 50px #414141;
}
```

The output is weird though. We followed the markup but the shadow seems to be too large. We can control this by adding another value between the size and the color in `box-shadow`. This value is called `spread` which determines how much the shadow is spread, let's make it negative so it's much much more subtle:

```css
.shadowed {
    box-shadow: 0px 0px 50px -8px #414141;
}
```

Finally, to align the image and "attach" it to the box, we'll first center it. Like usual, we'll put flex on the parent and set the margin to auto to center:

```css
 .recommendation {
    display: flex;
    flex-direction: column;
}

.recommendation > * {
    margin: auto;
}
```

Now to "attach" the image, we can just move the box up and set it's margin to negative of whatever the half of the size of the image:

```css
.recommendation .-body {
    padding: 24px;
    padding-top: 88px;
    margin-top: -64px;
}
```

The image seems transparent though, this is because both components have the same `z-index`. Remember your dimensions `x` and `y`? There's also a `z` dimention that dictates which components are brought to the front or to the back. Let's add a relatively larger `z-index` to the image:

```css
.recommendation img.-circle {
    z-index: 100;
}
```

Nicely done! Your recommendation component should now be complete

## Designing Components: Employment History Item

This time, we will revise our employment history item so that the styles are better reusable.

Create a new markup `employment-history.html` with the following contents:

```html
<html>
    <head>
        <link rel="stylesheet" type="text/css" href="assets/css/style.css">
        <link rel="stylesheet" type="text/css" href="assets/css/employment-history.css">
        <style>
            body {
                width: 300px;
            }
        </style>
    </head>
    <body>
        <article class="employement-history-entry">
            <img class="-circle-sm" src="https://helium.nuworks.ph/img/nuworks-logo-colored.png">
            <div class="-body shadowed">
                <h4>NuWorks Interactive Labs Inc.</h4>
                <strong>Role: Fullstack Developer</strong>
                <p>Provided high quality PHP (Laravel) and JavaScript (MERN) based applications depending on client needs.</p>
            </div>
        </article> 
    </body>
</html>
```

One change you may have noticed from the previous iteration is that the `-body` element now also has a `shadowed` class. This is so that the shadow property is reused and uniform across elements. The previous company logo's class was also changed to `-circle-sm`. Create this class in `style.css`:

```css
img.-circle-sm {
    width: 64px;
    height: 64px;
    border-radius: 32px;
}
```

This is to create a more consistent class the `-circle` class, only smaller.

You should also notice that we are linking a new css called `assets/css/employment-history.css`. Create that file now with the following contents:

```css
.recommendations-screen {
    padding: 0 50px;
}

.recommendations-screen > .-container {
    width: 100%;
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin: auto;
}

.recommendation-place-holder {
    width: 25%;
    min-width: 200px;
    height: 400px;
    background-color: grey;
}

.experience-screen {
    margin-top: 30px;
}

.employement-history-entry > * {
    display: inline-block;
}

.employement-history-entry {
    display: flex;
    justify-content: center;
}

.employement-history-entry > .-body {
    margin-left: 20px;
    padding: 0px 15px;
    max-width: 500px;
}
```

Check and you'll see that we've removed the classes we either removed or replaced in the markup.

## A Preview on Responsive Design

We will learn responsive design in more detail later on but let's do a little spoiler and try to do something neat before we end this session. Let's try to hide a certain part of the view if the page is too small.

Edit the `employment-history.css` file and let's practice on something called a media query:

```css
@media all and (max-width: 479px) {
    .employement-history-entry img {
        display: none;
    }
}
```

Then add the following code inside the `head` tag of your webpage:

```html
<meta content="width=device-width, initial-scale=1" name="viewport" />
```

Check your webpage and change the size of the browser, then refresh. You should see that your image will show/hide depending on the screen size now.

## Next Lesson

Now that we know about design and a bit about media queries. Let's revisit css layouts, this time though, while considering responsiveness.

Our next lesson would be Responsive CSS Layouts, [click here](/modules/css/css-layout-responsive.md) to go to the next lesson.