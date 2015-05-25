---
layout: post
title:  "Relative, Absolute and Fixed Positioning in CSS"
date:   2014-11-30 15:30:00
categories: technical
tags: css positioning
---
We had fun this week at DBC diving into HTML and CSS.  To anyone who is not familiar with these acronymns, you actually are, you just don't know it yet. If you have ever looked at a website, you were looking at something created by HTML and CSS.

HTML stands for HyperText Markup Language. It's simply a way to organize, structure and describe the function of elements on a web page, like <q>Hey, that's a paragraph of text</q> or <q>that's an important heading</q>. Who is it talking to? It conveys this information to your web browser so the web browser can display or <q>render</q> it.

Okay, but how does it know HOW to render it? How does it know to make that text Verdana and make the paragraph take up half the page? That's where CSS comes in.

CSS stands for Cascading Style Sheets. Cascading Style Sheets are basically a set of instructions on how things should be displayed on a web page. These instructions can address colors, fonts, images, and the size and arrangement of elements on a page.

The cascading part simply means: prepare to spend a lot of time with Google Chrome Developer Tools.  No, seriously it means that elements can inherit styling instructions from multiple sources.

Remember the part about how HTML structures pages by function? The elements on a webpage are organized in the form of a tree-like hierarchy called the DOM (the Document Object Model).  Elements - like a paragraph, a list of items or a section of content - each have a single <q>parent</q> branch and can have multiple <q>children</q> branches in the hierarchy. For example, if a list of links is contained in the site navigation section, the list is a child node of the navigation section. The individual links in the list are children of the list node.

Just as you inherited your great looks from your parents, a child node will inherit the styling of CSS applied to its parent node. Any CSS applied directly to that child node will in turn pass that styling down to its child nodes.

### The Box Model ###

Despite what you might think, the box model is NOT an attractive person who does ads for The Packaging Store. The box model describes how all elements on a web page basically occupy a certain amount of real estate on the page in the shape of a box or rectangle. Each box has padding, a border and a margin.

Going with the real estate metaphor: the html element would be your house. The CSS border would be your property line. The CSS padding would be the distance from your house to your property line. The CSS margin would be the distance from your property line to your neighbor's property line. You use CSS to control the size of the html element, the padding, the border and the margin for each box on your page.

### CSS Positioning ###

How do all these boxes fit together? How do you position each box on the page?

In an html document, there is a <q>natural flow</q> of the elements on the page. Each element cozies up to the next element with the size and spacing based on the CSS box model. This is the default behavior of elements and it's called `static` positioning. Every element occurs where it would naturally fall on the page.

You often need an element to occur out of it's natural position for design purposes. Luckily, an element does not have to occur in it's default position. The box can be offset by specifying an alternate CSS `position` property and identifying an offset amount. The possible alternate CSS position values are relative, absolute and fixed.

When you set the position property to `relative`, you start from the position where the element would normally fall (with the default static setting) and offset it by some value or values that you specify. For example, you could say `left: 35px` and it would shift the box 35 pixels to the right.

When you set the position property to `absolute`, you can also offset the position of the element but the offset is relative to a different thing. An element with an absolute position will look up the HTML DOM and find the next element up the tree that is set to either relative, absolute or fixed position. It will then set itself relative to that object. You have essentially removed the element from the natural order of the page so other page elements will ignore it.

Fixed position objects are set to an exact location on the screen. This position does not change if you scroll down the page or position any other elements around it. If you set the element to fixed position with top: 20px and left: 20px the element will always be exactly 20px from the top and 20px from the left side.

Below are some great resources on CSS positioning. These articles helped me and I recommed them if you are interesed.

* [W3School CSS Positioning](http://www.w3schools.com/css/css_positioning.asp "W3School CSS Positioning")
* [Absolute, Relative, Fixed Positioning: How Do They Differ?](http://css-tricks.com/absolute-relative-fixed-positioining-how-do-they-differ/ "Absolute, Relative, Fixed Positioning: How Do They Differ?")
