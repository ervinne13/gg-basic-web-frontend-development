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

__Closing Elements / Open & Close Elements__

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

__Images__

Images are another common element of a document or a web page. To include an image in a document you must use an `img` tag. Image tags are an example of an inline element because they just flow in with the surrounding text. They do not force a new block to be created in the rendering of the html. A basic image element can be written as:

```html
<img src="https://cdn.shopify.com/s/files/1/0093/8606/6016/products/sticker-grumpy-octocat_1279x.jpeg?v=1556305667">
```

__Tag Attributes:__

The image tag has a new component to it called an attribute. In general tags can have many attributes in the case of an image we can inlude it by using a `src` attribute that contains the URL to the image we want to embed. We can embed any image on the internet in our own document by referring to it by its URL in the src attribute.

We can also specify another attribute of an `img` tag called `alt`. The value of `alt` is a string of text that describes the image. This can be used for webpage readers (to be honest, I don't know what it's actually called but it's a feature in browsers where parts of the page are read out loud by your computer).

There are many other attributes that an `img` element can have. You may read about them [here](https://www.w3schools.com/tags/tag_img.asp).

As an activity, follow along the instructor and try out different images in your scratch markup.

__Links__

A link is an element that redirects the user to a specified URL.
A link can be created with:

```html
<a href="https://ervinne13.github.io">Click to view my profile</a>
```

Activity 1-3:

What happens if you put different types of elements aside from text inside the `<a>` tags?

Try it out with:
 - `p`
 - `h1`
 - `img`

__Element Children & Parent Children Relationship__

If you did activity 1-3, you will notice that asid from strings of text, you can actually also specify other elements inside elements like in the case of links. An HTML document is actuall a "tree" of elements. Each element can have one or more "children" "nodes" (or leafs, but its more commonly refered to as nodes).

Plain text, as in what we see inside `p` tags are also nodes, they are called "text nodes" everything inside an HTML document is a "tree" of "nodes":

![](https://blog.scrapinghub.com/hs-fs/hubfs/tree-7.png?width=564&name=tree-7.png)

We will learn more of this later when we construct a complete HTML document. We'll use this image again as reference later on.

__Simple Text Formatting__

You may also do simple formatting with html tags. The instructor would like to leave this up to you as an activity though.

Activity 1-4

What happens to text nodes if they are inside the following "Closing Elements / Open & Close Elements"?

- `<b>`
- `<strong>`
- `<i>`
- `<em>`
- `<code>`
- `<sub>`
- `<sup>`

Activity 1-5

What happense if you nest `<b>` tags together? What about `<strong>`?

__Lists__

An HTML list can be ordered or unordered. The difference is that an unordered list is bulleted while an ordered list uses numbers to represent list items. Example:

Unordered List:

```html
<ul>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ul>
```

Ordered List:

```html
<ol>
  <li>Coffee</li>
  <li>Tea</li>
  <li>Milk</li>
</ol>
```

An ordered list has a `type` attribute. This can be set to:

- 1 = numeric list (1, 2, 3 ...)
- A = uppercase letters (A, B, C ...)
- a = lowercase letters (a, b, c ...)
- I = uppercase roman numerals (I, II, III, IV, ...)
- i = lowercase roman numerals (i, ii, iii, iv, ...)

__Others__

Line Breaks

You may create line breaks through the use of `<br>` tags. You might also notice other developers do this `<br />` instead. This is fine, but usually unecessary. The extra `/` is there for XHTML, a stricter kind of HTML that we wont cover where ALL TAGS MUST BE CLOSED, as a result, developers must write `<br></br>` or as a shortcut, `<br />`.

Comments

The following code is a "comment", it can contain anything and the browser will just ignore its contents. Comments are used to describe something in your markup:

```html
<!-- I'm a comment, HTML won't display me -->
```

Divs

A `<div>` element does not do anything in itself but group a set of child elements.
They can be useful though, when we now try to add styling to them. For example:

```html
<div style="background-color:black; color: white">
    <h3>This is a heading</h3>
    <p>This is a paragraph.</p>
</div>
```

## HTML Documents

An html document is a file that contains HTML code. It is usually structured like:

```html
<!DOCTYPE html>
<html>
    <head>
        <title>Title of the document</title>
    </head>
    <body>
        The content of the document......
    </body>
</html>
```

Children of the `<head>` element is not visible in the page of the browser. Its children is usually composed of dependencies, meta data, page title, etc.

The `<body>` element should contain the elements that we just learned so far.

Note that the <!DOCTYPE> declaration is not an HTML tag; it is an instruction to the web browser about what version of HTML the page is written in.

For example, to declare our webpage as:

HTML5:
```html
<!DOCTYPE html>
```

HTML 4.01 Strict
```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
```

In general, you should set this to HTML5. This is so that even if HTML6 is released, the browser will still interpret your markup as HTML5 and will not apply HTML6 features yet as that may break your webpage.

## Answers to all activities

Congratulations! You now know how to code in HTML, that makes you a web developer!
As your reference, [click here](to view answers to all the activities we did).

## What to do next? (Outside this workshop)

First, you may read up about all the other HTML tags [here](https://www.w3schools.com/tags/tag_comment.asp) (navigate in the left bar for each tags and their definitions).

## Next Topic: Basic Styling

Click [here](/modules/html/basic-styling.md) to go to the next topic.