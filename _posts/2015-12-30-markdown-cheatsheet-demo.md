---
layout: post
title: "Markdown Cheatsheet Demo"
comments: true
description: "Markdown Cheatsheet Demo..."
keywords: "markdown, typography components, dummy content"
---

## Typography Elements in One

Let's start with a informative paragraph. **This text is bolded.** But not this one! _How about italic text?_ Cool right? Ok, let's **_combine_** them together. Yeah, that's right! I have code to highlight, so `ThisIsMyCode()`. What a nice! Good people will hyperlink away, so [here we go](#) or [http://www.example.com](http://www.example.com).

<div class="divider"></div>

## Headings H1 to H6

# H1 Heading

## H2 Heading

### H3 Heading

#### H4 Heading

##### H5 Heading

###### H6 Heading

<div class="divider"></div>

## Footnote

Let's say you have text that you want to refer with a footnote, you can do that too! This is an example for the footnote number one [[^1]]. You can even add more footnotes, with link! [[^2]]

<div class="divider"></div>

## Blockquote

> Start by doing what's necessary; then do what's possible; and suddenly you are doing the impossible. --Francis of Assisi

**NOTE:** This theme does NOT support nested blockquotes.

<div class="divider"></div>

## List Items

1. First order list item
2. Second item

* Unordered list can use asterisks
- Or minuses
+ Or pluses

<div class="divider"></div>

## Code Blocks

```javascript
var modularpattern = (function() {
    // your module code goes here
    var sum = 0 ;

    return {
        add:function() {
            sum = sum + 1;
            return sum;
        },
        reset:function() {
            return sum = 0;    
        }  
    }   
}());
alert(modularpattern.add());    // alerts: 1
alert(modularpattern.add());    // alerts: 2
alert(modularpattern.reset());  // alerts: 0
```

```python
s = "Python syntax highlighting"
print s
```

```
No language indicated, so no syntax highlighting.
But let's throw in a <b>tag</b>.
```
$$ E = mc^2 $$
$ a^2+b^2=c^2 $
<div class="divider"></div>

## Hidden Block

<details>
  <summary markdown="span">Click me</summary>
	
  <p>the answer is <code>42</code></p>

**abc**

$ E=mc^2 $
  
  ```python
  print("Hello world")
  ```

</details>

<div class="divider"></div>

## Table

### Table 1: With Alignment

| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
| zebra stripes | are neat      |    $1 |

### Table 2: With Typography Elements

Markdown | Less | Pretty
--- | --- | ---
*Still* | `renders` | **nicely**
1 | 2 | 3

<div class="divider"></div>

## Horizontal Line

The HTML `<hr>` element is for creating a "thematic break" between paragraph-level elements. In markdown, you can create a `<hr>` with any of the following:

* `___`: three consecutive underscores
* `---`: three consecutive dashes
* `***`: three consecutive asterisks

renders to:

___

---

***

<div class="divider"></div>

## Media

### Video Embedded Iframe

<div class="video-container"><iframe src="https://player.bilibili.com/player.html?isOutside=true&bvid=BV1x5411o7Kn&cid=505002580&as_wide=1&high_quality=1&danmaku=0"
			 allowfullscreen="allowfullscreen" scrolling="no" frameborder="0" sandbox="allow-top-navigation allow-same-origin allow-forms allow-scripts"></iframe></div>

### Image

![Minion](https://avatars.githubusercontent.com/u/151628144?s=400&u=be73ac31f53e7f813c725a129026b17ed7074543&v=4)

---
Footnote:

[^1]: 1: Footnote number one yeah baby!

[^2]: 2: A footnote you can link to - [click here!](#)
