# Designing the Components

This section will be part of your practical activities. Here, we will be designing each of the components individually without the layout. We will only really "stitch" once everything is done.

First off, we'll have to learn some more techniques like adding fonts and separating css.

## Adding Fonts

In our mocks, you can see that the font we've used is "segoe ui". You may add fonts on your design by using the `@font-face` in CSS like so:

```css
@font-face {
    font-family: "Segoe UI";
    font-weight: 400;
    src: local("Segoe UI");
}
```

We may also add some more using the same fonts but different font weights so that we'll have the same fonts as in the mocks:

```css
@font-face {
    font-family: "Segoe UI";
    font-weight: 400;
    src: local("Segoe UI");
}
@font-face {
    font-family: "Segoe UI";
    font-weight: 600;
    src: local("Segoe UI Semibold");
}
@font-face {
    font-family: "Segoe UI";
    font-weight: 700;
    src: local("Segoe UI Bold");
}
```

To make use of these fonts, add the ruleset `font-family: "Segoe UI"` to your target element.

```css
body {
    font-family: "Segoe UI";
}
```

Adding it to the body of your markup will make this font the "default".