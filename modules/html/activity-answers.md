# HTML Basics Activity Answers

If you haven't tried to answer them yet, please go back to the lesson by clicking [here](/modules/html/index.md).

## Activity 1:

As you might expect, the headings continue to get smaller as you go from 1 to 6. But when you go to level 7 the text gets bigger. This is because the web browser is written so that it just ignores any tags that it does not know about. This is somewhat of a disadvantage as you don’t get any error messages, things just look wrong, and you have to figure out why.

Incorrect heading closing tags are also ignored. The same reason as to using h7.

## Activity 2

__Sample answer for nesting paragraphs:__
```html
<p>
    Test paragraph
    <p> with another paragraph inside</p>
</p>
```

Notice that paragraphs ignore nesting. This is actually correct as in normal documents, there's no such thing as a paragraph inside a paragraph. So as a recommended practice, DO NOT nest paragraphs in the first place

__Sample answer for heading inside paragraphs:__
```html
<p>
    <h1>Test h1</h1>
    Test paragraph
</p>
```

Same thing happens in headings inside paragraphs so dont bother nesting them as well. And if you're stubborn and still do, this will actually create a bug in your markup where css styles __does not apply to paragraphs that have headings inside them!__ (Follow along the instructor as he demonstrate this). So again DO NOT put heading tags in paragraphs.

## Activity 3

Texts are not the only "children" an element can have. You can usually put other elements inside elements (except of course in our samples in Activity 2). Putting `<a>` tags as "parent" of these elements makes the whole element a link.

__Sample answers__

```html

<a href="https://ervinne13.github.io">
<p>I'm a paragraph but also a link</p>
</a>

<a href="https://ervinne13.github.io">
<h1>And I'm a heading</h1>
</a>

<a href="https://ervinne13.github.io">
<img src="https://cdn3.iconfinder.com/data/icons/media-player-music-video-minimalist-outline-1/48/Video_player_love_favorite-512.png" alt="even images can be links">
</a>

```

You are also not limited on the number of children an element can have. 

```html
<a href="https://ervinne13.github.io">
<h1>I'm a heading</h1>
<p>I'm a paragraph</p>
</a>
```

## Activity 4

All the tags you are tasked to do have different effect on text:

__Bold Text__

```html
<b>This text is bold</b>
```

__Strong Text__

```html
<strong>Joseph Joestar</strong>
```

Note that both Bold and Strong may look the same. They are semantically different though. Semantics may not express anything different in the users eyes, but it will on the developers'. Activity 5 answers will discuss this more in detail.

__Italic Text__
```html
<i>this text is italicized</i>
```

__Emphasized Text__
```html
<em>this text is emphasized</em>
```

Difference between italicized and emphasized is pretty much the same as bold and strong, it's all semantics.

__Coded Text__
```html
<code>this is some code</code>
```

The `<code>` tag is a phrase tag. It defines a piece of computer code.

__Subscripts__
```html
log(n)<sub>10</sub>
```

__Superscripts__
```html
2x<sup>2</sup>
```

## Activity 5

The `<b>` tag is for "offset text conventionally styled in bold". If you read deeper into the details you'll see it adds, "without conveying any extra emphasis or importance".

`<strong> `is different. It "represents a span of text with strong importance." There is semantic meaning of importance here. In fact, a `<strong>` tag within another `<strong> `tag has even more importance. There is nested importance. The html5 spec is enlightening on this.

Sample answers:

```html
<b>Test <b>Test2</b></b>

<strong>Test <strong>Test2</strong></strong>
```

Note again that these are semantics. This might not mean much to a beginner, but when you have to manage a codebase that has hundreds of files with hundreds (some times even thousands) lines of code, semantics will really help in readability.

You may read more about semantic HTML [here](http://seekbrevity.com/semantic-markup-important-web-design/). Bottom line is, semantics convey meaning but not appearance. As a beginner, you may (to a degree) neglect this a bit until such time that you are now comfortable in making your markup work. As you become more experienced though, please learn about semantic HTML as well.

## Activity 6

Your answer should be something like:
```html
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
```

## Want to go back to the lesson?

You may do so by clicking [here](/modules/html/index.md).