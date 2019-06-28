# CSS Basics Activity Answers

If you haven't tried to answer them yet, please go back to the lesson by clicking [here](/modules/css/index.md).

## Activity 1:

Question 1:
The changed code should be:
```css
p#paragraph2 {
    font-size: 18pt;
    color: red;
}
```

If you said that it will keep the first paragraph’s color blue but change the second to red, your are correct. Why does the second rule over-rule the first? __Because the second rule is more specific.__ You might have thought it was because of the order of the rules, but in fact you can change the order of the two rules and try it and you will see that you still get the same result.

Learn more in [specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)

Question 2: Just matching the id is enough. We don't even need to specify what the tag is. Using tags as selector is still good if we are using classes instead.

__Activity 2__

There are two answers for this. One would be what you've learned so far, adding the tag to the selector:

```css
tr.odd {
    background-color: grey;
    color: white;
}
```

The other answer is to match only tables and the classes inside them. This is discussed in the Selector: Matching Children lesson.

Ex.

```css
table .odd {
    background-color: grey;
    color: white;
}
```

__Activity 3__

After you set the `overflow` property, you can guess how each of these values now behave:

- visible = Is the default
- hidden = Hides anything that overflows from the box model
- scroll = Creates a scrollbar 
- auto = Let's the page choose for the best possible value (scroll in this case)

```html
<html>
    <head>
        <style>
            section {
                overflow: auto;
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

__Activity 4__

The output should be something like:

```html
<html>
   <head>
      <style>
      </style>
    </head>
<body>
    <p>the quick brown fox jumped over the lazy dog.  the quick brown fox jumped over the lazy dog.  the quick brown fox jumped over the lazy dog.  <img style="float: left" src="https://mobilelegends.gcube.id/wp-content/uploads/sites/6/2017/12/Mobile-Legends-Items-Magic-3-Calamity-Reaper.png" /> the quick brown fox jumped over the lazy dog. the quick brown fox jumped over the lazy dog. the quick brown fox jumped over the lazy dog.
    </body>
</html>
```

__Activity 5__

We can "prevent" overlapping by adding a margin to the content that's not a header.

Then, to resolve the scrolling issue, we can add a background color white and have the whole header span 100% through the page so that it can hide the content behind it.

See the whole solution [here](/modules/css/long-samples/position-fixed-non-overlapping.md)

__Activity 6__

Remember that position relative can be understood as relative to its original position, that's why we double the coordinates from image b.

Be careful though, try to make your page narrower. This will put the images in an awkward position because their new "original" positions can be in a new line. Thus behaving a lot differently.

```html
<html>
    <head>
        <style>
            img.card {
                height: 200px;
            }
            img#b {
                position: relative;
                top: 100px;
                left: -100px;
            }
            img#c {
                position: relative;
                top: 200px;
                left: -200px;
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

__Activity 7__

Since position absolute is based on the parent, the children of #image-container will also adjust when their parent adjusts positions:

```html
<html>
    <head>
        <style>
            div#image-container {
                position: relative;
                top: 100px;
            }
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