# HTML Basics

HTML, HyperText Markup Language, gives content structure and meaning by defining that content as, for example, headings, paragraphs, or images. CSS, or Cascading Style Sheets, is a presentation language created to style the appearance of content—using, for example, fonts or colors.

![](https://i.pinimg.com/originals/7c/51/64/7c516430739e108764378d2a461b5c8f.jpg)

In this part of the workshop, we will be making basic webpages with HTML first.

## Tags

HTML is a language that's almost entirely composed of what we call `tags`. A tag is a string of text (name of the tag) with attributes (more on this later) enclosed by < and >.

__And example of a `tag`__

```html
<html>
```

## HTML Elements

An HTML element can either be `closing` or a `singleton` html element.

__Closing Elements__

```html
<p>This is a paragraph</p>
```

__Singletons__

```html
<br>, <img>, <link>, etc...
```

## Basic/Common HTML Tags & Elements

__Headings__

Headings are exactly the "heading" in microsoft word or similar software. It's describes a text that should be larger than usual. Usually used to depict a title in a page.

```html
<h1>Largest of all</h1>
<h2>Still a large text</h2>
<h3>I'm still a heading</h3>

... up to <h6>
```

Activity 1-1:

Create an html file (whatever you name it, just add .html) and try to write 7 heading elements h1 to h7. What happens on h7 tags? What happense if you close an h2 tag with an h1 or h3?
(Answers at the end)

__Paragraps__

```html
<p>A basic paragraph<p>
<p>Multiple paragraph elements automatically add vertical spaces  between each other. Effectively imitating a paragraph in a letter.</p>
```

Activity 1-2:

What happens when you put a paragraph inside another paragraph? What about a header inside a paragraph?

