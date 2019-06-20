
## Activity 1-1:

As you might expect, the headings continue to get smaller as you go from 1 to 6. But when you go to level 7 the text gets bigger. This is because the web browser is written so that it just ignores any tags that it does not know about. This is somewhat of a disadvantage as you don’t get any error messages, things just look wrong, and you have to figure out why.

Incorrect heading closing tags are also ignored. The same reason as to using h7.

## Activity 1-2

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