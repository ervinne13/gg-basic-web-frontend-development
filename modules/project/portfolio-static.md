# Building Your Portfolio Using Plain CSS & HTML

You now have enough knowledge to put to use to develop a static page for your portfolio. Let's start with the first screen.

## Common Styling

We can start by creating the common styling that we've identified earlier. The font, box shadows, and a circular image. Create a new folder `assets/css` and inside it, create the file `style.css` which will then contain:

```css
body {
    font-family: "Segoe UI", Arial, sans-serif;
    color: #414141;
}

img.-circle-sm {
    width: 64px;
    height: 64px;
    border-radius: 32px;
}

img.-circle {
    width: 128px;
    height: 128px;
    border-radius: 64px;
}

.shadowed {
    box-shadow: 0px 0px 14px -8px #414141;
}

section {
    margin-bottom: 20px;
}
```

Note that we've added an extra `color: #414141;` ruleset as well so that the text are not too black. We've also drastically reduced the box shadow so that it would look more like our mocks instead of literally getting the value from XD. The margin bottom for sections is pretty self explanatory

Commit and push your changes to git.

## Main Screen

We'll need your portrait image for this page, so copy your image to a new folder `assets/img` in your project so we may reference it in our markup later.

Copy your CV or resume as well in a new folder called `assets/others`.

Next, we can now copy and paste our previously created components. Let's start with the markup:

```html
<html>
    <head>
        <meta content="width=device-width, initial-scale=1" name="viewport" />
        <link rel="stylesheet" href="assets/css/style.css">
    </head>
    <body>
        <section class="main-screen">
            <div class="-content">
                <span class="hero-title">
                    Hi!
                    <div>I'm Ervinne</div>
                </span>
                <div>
                    <a href="https://www.facebook.com/ervinne.sodusta" target="_blank">
                        <img src="assets/img/facebook.svg">
                    </a>
                    <a href="https://www.linkedin.com/in/ervinne-sodusta-a8910977/" target="_blank">
                        <img src="assets/img/linkedin.svg">
                    </a>
                    <a href="https://github.com/ervinne13/" target="_blank">
                        <img src="assets/img/github.svg">
                    </a>
                </div>
                <p>An aspiring frontend web developer from the Philippines</p>

                <div class="call-to-action-container">
                    <a class="call-to-action" href="assets/others/sample-cv.docx">
                        Download My CV
                    </a>
                </div>
            </div>
            <div class="-right-image-container">
                <img src="assets/img/portrait.jpg">
            </div>
        </section>
    </body>
</html>
```

This is pretty much just "stitching" together the elements that we were able to create early on in this workshop. The only thing new here is the `.call-to-action-container` which will be used to create a vertical gap (margin).

For the styling, we want to put our styles in the `styles.css` file instead. Since we can't separate by file (would create inefficient http requests) let's just add in some comments to separate each part of our styling:

```css
/* Main Screen Styling */
.main-screen {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: row;
}

.hero-title {
    font-weight: 500;
    font-size: 65px;
}

.main-screen .-content {
    flex: 1;
    padding: 120px 75px;
}

.main-screen .-content, 
.main-screen .-right-image-container img {
    height: 100%;
}

.call-to-action-container {
    margin-top: 28px;
}

.call-to-action {
    padding: 12px 18px;
    text-decoration: none;
    color: white;
    font-size: 24px;
    background-color: #121212;
}

@media(max-width: 600px) {
    .main-screen .-right-image-container {
        display: none;
    }

    .hero-title {
        font-weight: 400;
        font-size: 45px;
    }

    .-content {
        text-align: center;
    }
}
/* End if Main Screen Styling */
```

This would be the accumulation of what we did earlier. The only thing new here is the style for `.call-to-action-container`, which is used to add a vertical spacing between the button/link and the contents on top of it.

## Recommendations Screen

Write up the same markup for the 3 column responsive layout we did earlier. Inside each column, the recommendations:

```html
<html>
    <head>
        <meta content="width=device-width, initial-scale=1" name="viewport" />
        <link rel="stylesheet" href="assets/css/style.css">
    </head>
    <body>
        <section class="main-screen">
            <!-- ... -->
        </section>
        <section class="recommendations-screen">
            <h1>Awesome People Who Recommends Me</h1>
            <div class="grid-container">
                <div class="row">
                    <div class="col">
                        <article class="recommendation">
                            <img class="-circle" src="https://randomuser.me/api/portraits/women/60.jpg" alt="Profile Image">
                            <div class="-body shadowed">
                                <span class="-name">Doris Tumulak</span>
                                <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Necessitatibus animi nemo atque commodi explicabo! Doloribus nobis magnam est nesciunt illum inventore adipisci enim autem minus fugiat eos, corrupti, quia rem.</p>
                            </div>
                        </article>
                    </div>
                    <div class="col">
                        <article class="recommendation">
                            <img class="-circle" src="https://randomuser.me/api/portraits/women/64.jpg" alt="Profile Image">
                            <div class="-body shadowed">
                                <span class="-name">Vanessa Getubig</span>
                                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis, maxime ipsum quibusdam consequatur ipsam quas aliquid praesentium iusto nostrum dignissimos voluptatibus vitae id porro tempora sint labore perferendis quaerat veniam?</p>
                            </div>
                        </article>
                    </div>
                    <div class="col">
                        <article class="recommendation">
                            <img class="-circle" src="https://randomuser.me/api/portraits/men/61.jpg" alt="Profile Image">
                            <div class="-body shadowed">
                                <span class="-name">Mike Yap</span>
                                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet odio, aperiam culpa, illo illum dolores aspernatur debitis aut reiciendis suscipit natus exercitationem doloribus unde quia soluta recusandae, ab neque. Itaque?</p>
                            </div>
                        </article>
                    </div>
                </div>
            </div>
        </section>
    </body>
</html>
```

We also added a simple `h1` heading as a simple screen separator and then used different images. After copy pasting, it's also good to generate different lorem ipsum variants so that the height of the recommendations varies.

In your `style.css`, add the following styles:

```css
/* Generic 3 columned grid styling */
.grid-container {
    max-width: 1440px;
    margin: 0 auto;
}

.grid-container .row {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
}

.grid-container .row .col {
    flex-basis: 33.33%;
    width: 259px;
    padding: 10px;
    box-sizing: border-box;
}

.box {
    background-color: grey;
    width: 100%;
    min-height: 100px;;
}

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
/* End of generic 3 columned grid styling */
```

... for the grid. Refresh your page and your content should now be responsive. Of course, also add in the styling for the recommendations:

```css
/* Recommendation screen styling */
.recommendation {
    display: flex;
    flex-direction: column;
}

.recommendation > * {
    margin: auto;
}

.recommendation img.-circle {
    z-index: 100;
}

.recommendation .-body {
    padding: 24px;
    padding-top: 88px;
    margin-top: -64px;
}

.recommendation .-name {
    font-weight: bold;
    color: #B8B8B8;
}
/* End of recommendation screen styling */
```

## Work History Screen

Lastly, we can now copy paste our code to the work history screen. Write up the markup like:

```html
<html>
    <head>
        <meta content="width=device-width, initial-scale=1" name="viewport" />
        <link rel="stylesheet" href="assets/css/style.css">
    </head>
    <body>
        <section class="main-screen">
            <!-- ... -->
        </section>
        <section class="recommendations-screen">
            <!-- ... -->
        </section>
        <section class="employement-history">
            <h1>My Employment History</h1>

            <article class="employement-history-entry">
                <img class="-circle-sm" src="https://helium.nuworks.ph/img/nuworks-logo-colored.png">
                <div class="-body shadowed white-box">
                    <h4>NuWorks Interactive Labs Inc.</h4>
                    <span class="sub-h4">August 2016 to Present</span>
                    <strong>Role: Fullstack Developer</strong>
                    <p>Provided high quality PHP (Laravel) and JavaScript (MERN) based applications depending on client needs.</p>
                </div>
            </article>
            <article class="employement-history-entry">
                <img class="-circle-sm" src="https://helium.nuworks.ph/img/nuworks-logo-colored.png">
                <div class="-body shadowed white-box">
                    <h4>Global Strategic Solutions & Service</h4>
                    <span class="sub-h4">Feb 2012 to Aug 2016</span>
                    <strong>Role: Development Team Lead</strong>
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus, dolorum totam, qui consequatur quia veniam quas cupiditate, amet debitis sit eveniet officiis tenetur. Aliquam reprehenderit voluptas illo cumque modi. Rem!</p>
                </div>
            </article>
        </section>
    </body>
</html>
```

And finally, the same styling as we did earlier:

```css
/* Work history screen */
.experience-screen {
    margin-top: 30px;
}

.employement-history-entry > * {
    display: inline-block;
}

.employement-history-entry {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

.employement-history-entry > .-body {
    margin-left: 20px;
    padding: 0px 15px;
    max-width: 500px;
}

span.sub-h4 {
    font-weight: bold;
    color: #9e9e9e;
    display: block;
}

@media all and (max-width: 600px) {
    .employement-history-entry img {
        display: none;
    }

    .recommendation-place-holder {
        min-width: 70%;
    }
}
/* End of work history screen */
```

## Aesthetic Adjustments

We can create some contrast between our shadowed boxes and the background by creating a different background than white. Update the style of your `body` tag to:

```css
body {
    font-family: "Segoe UI", Arial, sans-serif;
    color: #414141;
    background-color: #f2f3f7;
}
```

Then add the style:

```css
.white-box {
    background-color: white;
}
```

... and add the `white-box` class to each of the elements that needs to have white background.

Note that we could've just added `background-color: white` ruleset to the `-shadowed` but looking at the code sematically, it won't make sense anymore. `-shadowed`'s purpose is to add shadow to a box, it's not concerned with the background color.

## Subtle Animations

Animations can be achieved through the use of `@keyframes` in CSS3. Consider the following style:

```css
.fade-in-right {
    animation-name: fadeInRight;
    animation-duration: 1s;
}

@keyframes fadeInRight {
    0% {
        opacity: 0;
        transform: translateX(40px);
    }

    100% {
        opacity: 1;
        transform: translateX(0);
    }
}
```

Animations can be defined by creating keyframes. Keyframes define what happens to the element at a specified point in time through percent of how long the `animation-duration` is set. In this case, at the start of the animation, we move the element to the right first by `40px`, we also hide it initially. Then when the animation finishes, it should be fully visible and is translated back to where it is originally placed.

Add this class to the `body` of your markup and it should fade in from the right.

## Review

Your markup should look like below at the end of this session:

```html
<html>
    <head>
        <meta content="width=device-width, initial-scale=1" name="viewport" />
        <link rel="stylesheet" href="assets/css/style.css">
    </head>
    <body class="fade-in-right">
        <section class="main-screen">
            <div class="-content">
                <span class="hero-title">
                    Hi!
                    <div>I'm Ervinne</div>
                </span>
                <div>
                    <a href="https://www.facebook.com/ervinne.sodusta" target="_blank">
                        <img src="assets/img/facebook.svg">
                    </a>
                    <a href="https://www.linkedin.com/in/ervinne-sodusta-a8910977/" target="_blank">
                        <img src="assets/img/linkedin.svg">
                    </a>
                    <a href="https://github.com/ervinne13/" target="_blank">
                        <img src="assets/img/github.svg">
                    </a>
                </div>
                <p>An aspiring frontend web developer from the Philippines</p>

                <div class="call-to-action-container">
                    <a class="call-to-action" href="assets/others/sample-cv.docx">
                        Download My CV
                    </a>
                </div>
            </div>
            <div class="-right-image-container">
                <img src="assets/img/portrait.jpg">
            </div>
        </section>
        <section class="recommendations-screen">
            <h1>Awesome People Who Recommends Me</h1>
            <div class="grid-container">
                <div class="row">
                    <div class="col">
                        <article class="recommendation">
                            <img class="-circle" src="https://randomuser.me/api/portraits/women/60.jpg" alt="Profile Image">
                            <div class="-body shadowed white-box">
                                <span class="-name">Doris Tumulak</span>
                                <p>Lorem ipsum dolor, sit amet consectetur adipisicing elit. Necessitatibus animi nemo atque commodi explicabo! Doloribus nobis magnam est nesciunt illum inventore adipisci enim autem minus fugiat eos, corrupti, quia rem.</p>
                            </div>
                        </article>
                    </div>
                    <div class="col">
                        <article class="recommendation">
                            <img class="-circle" src="https://randomuser.me/api/portraits/women/64.jpg" alt="Profile Image">
                            <div class="-body shadowed white-box">
                                <span class="-name">Vanessa Getubig</span>
                                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Blanditiis, maxime ipsum quibusdam consequatur ipsam quas aliquid praesentium iusto nostrum dignissimos voluptatibus vitae id porro tempora sint labore perferendis quaerat veniam?</p>
                            </div>
                        </article>
                    </div>
                    <div class="col">
                        <article class="recommendation">
                            <img class="-circle" src="https://randomuser.me/api/portraits/men/61.jpg" alt="Profile Image">
                            <div class="-body shadowed white-box">
                                <span class="-name">Mike Yap</span>
                                <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Amet odio, aperiam culpa, illo illum dolores aspernatur debitis aut reiciendis suscipit natus exercitationem doloribus unde quia soluta recusandae, ab neque. Itaque?</p>
                            </div>
                        </article>
                    </div>
                </div>
            </div>
        </section>
        <section class="employement-history">
            <h1>My Employment History</h1>

            <article class="employement-history-entry">
                <img class="-circle-sm" src="https://helium.nuworks.ph/img/nuworks-logo-colored.png">
                <div class="-body shadowed white-box">
                    <h4>NuWorks Interactive Labs Inc.</h4>
                    <span class="sub-h4">August 2016 to Present</span>
                    <strong>Role: Fullstack Developer</strong>
                    <p>Provided high quality PHP (Laravel) and JavaScript (MERN) based applications depending on client needs.</p>
                </div>
            </article>
            <article class="employement-history-entry">
                <img class="-circle-sm" src="https://helium.nuworks.ph/img/nuworks-logo-colored.png">
                <div class="-body shadowed white-box">
                    <h4>Global Strategic Solutions & Service</h4>
                    <span class="sub-h4">Feb 2012 to Aug 2016</span>
                    <strong>Role: Development Team Lead</strong>
                    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Delectus, dolorum totam, qui consequatur quia veniam quas cupiditate, amet debitis sit eveniet officiis tenetur. Aliquam reprehenderit voluptas illo cumque modi. Rem!</p>
                </div>
            </article>
        </section>
    </body>
</html>
```

And your css, `style.css`:

```css
body {
    font-family: "Segoe UI", Arial, sans-serif;
    color: #414141;
    background-color: #f2f3f7;
}

img.-circle-sm {
    width: 64px;
    height: 64px;
    border-radius: 32px;
}

img.-circle {
    width: 128px;
    height: 128px;
    border-radius: 64px;
}

.white-box {
    background-color: white;
}

.shadowed {
    box-shadow: 0px 0px 14px -8px #414141;
}

section {
    margin-bottom: 20px;
}

/* Generic 3 columned grid styling */
.grid-container {
    max-width: 1440px;
    margin: 0 auto;
}

.grid-container .row {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-between;
}

.grid-container .row .col {
    flex-basis: 33.33%;
    width: 259px;
    padding: 10px;
    box-sizing: border-box;
}

.box {
    background-color: grey;
    width: 100%;
    min-height: 100px;;
}

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
/* End of generic 3 columned grid styling */

/* Main Screen Styling */
.main-screen {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: row;
}

.hero-title {
    font-weight: 500;
    font-size: 65px;
}

.main-screen .-content {
    flex: 1;
    padding: 120px 75px;
}

.main-screen .-content, 
.main-screen .-right-image-container img {
    height: 100%;
}

.call-to-action-container {
    margin-top: 28px;
}

.call-to-action {
    padding: 12px 18px;
    text-decoration: none;
    color: white;
    font-size: 24px;
    background-color: #121212;
}

@media(max-width: 600px) {
    .main-screen .-right-image-container {
        display: none;
    }

    .hero-title {
        font-weight: 400;
        font-size: 45px;
    }

    .-content {
        text-align: center;
    }
}
/* End if Main Screen Styling */

/* Recommendation screen styling */
.recommendation {
    display: flex;
    flex-direction: column;
}

.recommendation > * {
    margin: auto;
}

.recommendation img.-circle {
    z-index: 100;
}

.recommendation .-body {
    padding: 24px;
    padding-top: 88px;
    margin-top: -64px;
}

.recommendation .-name {
    font-weight: bold;
    color: #B8B8B8;
}
/* End of recommendation screen styling */

/* Work history screen */
.experience-screen {
    margin-top: 30px;
}

.employement-history-entry > * {
    display: inline-block;
}

.employement-history-entry {
    display: flex;
    justify-content: center;
    margin-bottom: 20px;
}

.employement-history-entry > .-body {
    margin-left: 20px;
    padding: 0px 15px;
    max-width: 500px;
}

span.sub-h4 {
    font-weight: bold;
    color: #9e9e9e;
    display: block;
}

@media all and (max-width: 600px) {
    .employement-history-entry img {
        display: none;
    }

    .recommendation-place-holder {
        min-width: 70%;
    }
}
/* End of work history screen */

/* Animations */

.fade-in-right {
    animation-name: fadeInRight;
    animation-duration: 1s;
}

@keyframes fadeInRight {
    0% {
        opacity: 0;
        transform: translateX(40px);
    }

    100% {
        opacity: 1;
        transform: translateX(0);
    }
}

/* End of animations */
```

## End

Congratulations! You now know at least the basics of web development. You may change your portfolio however you like using the knowledge that you've gained here. You may also research some advanced techniques and apply it.