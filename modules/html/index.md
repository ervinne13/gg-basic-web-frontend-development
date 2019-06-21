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

Activity 1:

Create an html file (whatever you name it, just add .html) and try to write 7 heading elements h1 to h7. What happens on h7 tags? What happense if you close an h2 tag with an h1 or h3?
(Answers at the end)

__Paragraps__

```html
<p>A basic paragraph<p>
<p>Multiple paragraph elements automatically add vertical spaces  between each other. Effectively imitating a paragraph in a letter.</p>
```

Activity 2:

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

Activity 3:

What happens if you put different types of elements aside from text inside the `<a>` tags?

Try it out with:
 - `p`
 - `h1`
 - `img`

__Element Children & Parent Children Relationship__

If you did activity 3, you will notice that asid from strings of text, you can actually also specify other elements inside elements like in the case of links. An HTML document is actuall a "tree" of elements. Each element can have one or more "children" "nodes" (or leafs, but its more commonly refered to as nodes).

Plain text, as in what we see inside `p` tags are also nodes, they are called "text nodes" everything inside an HTML document is a "tree" of "nodes":

![](https://blog.scrapinghub.com/hs-fs/hubfs/tree-7.png?width=564&name=tree-7.png)

We will learn more of this later when we construct a complete HTML document. We'll use this image again as reference later on.

__Simple Text Formatting__

You may also do simple formatting with html tags. The instructor would like to leave this up to you as an activity though.

Activity 4

What happens to text nodes if they are inside the following "Closing Elements / Open & Close Elements"?

- `<b>`
- `<strong>`
- `<i>`
- `<em>`
- `<code>`
- `<sub>`
- `<sup>`

Activity 5

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

__Tables__

A table is like a spreadsheet. It is composed of rows and header. An example would look something like:

```html
<table>
    <tr>
        <td>1</td>
        <td>Russell</td>
        <td>Jackson</td>
        <td>94</td>
    </tr>
     <tr>
        <td>2</td>
        <td>John</td>
        <td>Deere</td>
        <td>80</td>
    </tr>
</table>
```

You may also write a header row by changing the column tags from `td` to `th`.

```html
<table>
     <tr>
        <th>Number</th>
        <th>First Name</th>
        <th>Last Name</th>
        <th>Points</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Russell</td>
        <td>Jackson</td>
        <td>94</td>
    </tr>
     <tr>
        <td>2</td>
        <td>John</td>
        <td>Deere</td>
        <td>80</td>
    </tr>
</table>
```

There are many attributes you can use with the various table tags.

- `table` * `width` - you can specify a width as a percentage or as a number of pixels. This attribute is useful for right now, but its use is not encouraged, as you are better off to use CSS to control the look of your table. We say that this attribute is deprecated * border - you can add borders to your tables as in the example above, but this tag is deprecated as well. * The spacing between the cells of the table. Also deprecated.
- `td` * `colspan` – if you have a particular table where you need an extra wide column in some rows you can make a cell of your table span more than one column using the colspan attribute. Its value is the number of columns.
- `td` * `rowspan` – If you have a particular table where you need an column to span multiple rows you can make a cell of your table span more than one row using the rowspan attribute. Its value is the number of rows.

Warning! Do not use tables to layout your page. We'll be discussing some best practices on how to achieve this when we get to do CSS Layouts.

Activity 6:

Create a table that looks like this:

<table>
     <tr>
        <th>Contact</th>
        <th colspan="2">Phone Numbers</th>
    </tr>
    <tr>
        <td rowspan="2">Doris</td>
        <td>Mobile</td>
        <td>09123456789</td>
    </tr>
    <tr>
        <td>Home</td>
        <td>779 12 34</td>
    </tr>
    <tr>
        <td rowspan="2">Ervinne</td>
        <td>Mobile</td>
        <td>09987654321</td>
    </tr>
    <tr>
        <td>Home</td>
        <td>997 43 21</td>
    </tr>
</table>

Hint: This is going to require both `rowspan` and `colspan` attributes. This is difficult to do at once so try to make 1 column or row work first, then the rest.

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

## Basic Semantic HTML

Some tags in HTML are designed for you to use in creating a logical structure for your page. As you have probably noticed many sites have a navigation bar in the header, and have some information about the page in a footer. Many web pages have sidebars, and of course blogs and many news sites are divided into articles. Scholarly web sites are divided into parts and sections.

Example:

![](https://www.w3schools.com/html/img_sem_elements.gif)

```html
<html>
    <body>
        <header>
            <p>This is text in the header</p>
        </header>
        <aside>
            <p>This is a side comment</p>
        </aside>
        <article>
            <p>This is some text for an article</p>
        </article>
        <p>Notice that there is nothing special about the location of any of this text.  Without CSS the semantic tags simply divide the document logically</p>
    </body>
</html>
```

Again, semantic tags are are working like `div` elements without styling. But it would now be easier for us to apply CSS later on and understand the parts of the page better with semantic tags.

In fact, if you try to run the code above, it would just look like this (without the lines):

---

<html>
    <body>
        <header>
            <p>This is text in the header</p>
        </header>
        <aside>
            <p>This is a side comment</p>
        </aside>
        <article>
            <p>This is some text for an article</p>
        </article>
        <p>Notice that there is nothing special about the location of any of this text.  Without CSS the semantic tags simply divide the document logically</p>
    </body>
</html>

---

Some info, before HTML5, we only really have `div` and `span` as invisible strucutral tags.

## Applying Basic Styling

You normally shouldn't put styles directly in HTML, but before CSS existed, this is how it was done.

To "style" an element, you can do something like:

```html
<p style="font-weight: bold">This text should be bold even if it's defined in a paragraph tag</p>
```

(Try it out on your own)

### Parts of a Style

The style is defined using the `style` attribute which can be added to almost any kind of tag in HTML.

The code `font-weight: bold` is what we call a "rule set". Each rule set can be separated by a semicolon (;). For example, we can set two (or more) rulesets in a style attribute of an element like so:

```html
<p style="font-weight: bold; font-size: 30px;">This text should be bold even if it's defined in a paragraph tag</p>
```

(Try it out on your own)

A rule set is a "key-value" pair divided by a colon (:) where the left hand side defines what property to set, and on the right, the value of that property. 

For example, we can search google about __"what are the possible font-weight property values"__? (Go ahead and google it out)

As of 2019, it should show a table of possible values listing "normal", "bold", "bolder", "lighter", and so on. See full reference [here](https://htmldog.com/references/css/properties/font-weight/)

It looks ugly though, so bear with me until we do lessons on CSS.

### Don't be ashamed to Google

It's impossible to memorize or know about each and every tag, element, attribute, style/css property, etc. so Google is your friend. Don't be ashamed to search for answers in Google whenever you don't know something.

The important thing is that you understand and at least know about the terminologies so you can pin point your search results.

## Styles are Cascading

Styles in HTML or CSS are naturally cascading. This means that styles of the parent element are "cascades" or applies to all of its children elements.

Consider the code below:

```html
<p style="color: green"> An algebraic expression: 2x<sup>2</sup> </p>
```

(Try it out yourself)

You may stop the cascading effect by specifying a style to the child elements as well. For example:

```html
<p style="color: green"> An algebraic expression: 2x<sup style="color: blue">2</sup> </p>
```

## Answers to all activities

Congratulations! You now know how to code in HTML, that makes you a web developer!
As your reference, [click here](to view answers to all the activities we did).

## What to do next? (Outside this workshop)

First, you may read up about all the other HTML tags [here](https://www.w3schools.com/tags/tag_comment.asp) (navigate in the left bar for each tags and their definitions).

## Next Topic: Source Control Management

Let's take a break on development first and learn about source control management. This topic is a must master (not just must know) if you're serious about being a web developer in the future.

We'll be learning this first before moving on so that all of our practice code can be saved in GIT.

Click [here](/modules/git.md) to go to the next topic.