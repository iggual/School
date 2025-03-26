# 🎨 CSS Cheatsheet

Welcome to the **CSS Cheatsheet** of the **Institute for Unconventional Genius (IUG)**! This guide will help you master the art of CSS with a touch of humor. Whether you're a newbie or a seasoned pro, you'll find something to chuckle about here. Let's dive in!

## 1. Basic Syntax

Every CSS rule consists of a selector and a declaration block. Think of it as a fashion rulebook for your web page – without it, your page would be wearing socks with sandals.

```css
selector {
    property: value;
}
```

Example:
```css
h1 {
    color: blue;
}
```

## 2. Selectors

### Type Selector

Selects all elements of a given type. It's like saying "Hey, all paragraphs, wear blue!"

```css
p {
    color: blue;
}
```

### Class Selector

Selects all elements with a given class. Use a period (.) followed by the class name. It's like a VIP pass for styling.

```css
.intro {
    font-size: 20px;
}
```

### ID Selector

Selects a single element with a given ID. Use a hash (#) followed by the ID name. It's like giving a specific element a unique fashion statement.

```css
#main {
    background-color: yellow;
}
```

### Attribute Selector

Selects elements with a specific attribute. Because some elements need special treatment.

```css
a[target="_blank"] {
    color: red;
}
```

### Pseudo-class Selector

Selects elements in a specific state, such as `:hover`, `:focus`, or `:nth-child`. Perfect for those moments when you want an element to feel special.

```css
a:hover {
    color: green;
}
```

## 3. Colors

### Named Colors

Use predefined color names. Because sometimes, you just want to call a spade a spade.

```css
body {
    background-color: lightblue;
}
```

### Hexadecimal Colors

Use hex codes to specify colors. It's like a secret code for colors.

```css
h1 {
    color: #ff6347;
}
```

### RGB Colors

Use the `rgb()` function to specify colors. Perfect for when you want to sound like a tech wizard.

```css
p {
    color: rgb(255, 99, 71);
}
```

### RGBA Colors

Use the `rgba()` function to specify colors with transparency. Because sometimes, you need a little transparency in your life.

```css
div {
    background-color: rgba(255, 99, 71, 0.5);
}
```

## 4. Font Styling

### Font Family

Specify the font family. Because fonts are like outfits for your text.

```css
body {
    font-family: Arial, sans-serif;
}
```

### Font Size

Specify the font size. Bigger is sometimes better.

```css
h1 {
    font-size: 2em;
}
```

### Font Weight

Specify the font weight. Make your text as bold as your personality.

```css
p {
    font-weight: bold;
}
```

### Text Alignment

Specify the text alignment. Because sometimes, you just need to center your life... and your text.

```css
div {
    text-align: center;
}
```

## 5. Box Model

### Margins

Specify the space outside an element. It's like personal space for your elements.

```css
div {
    margin: 10px;
}
```

### Padding

Specify the space inside an element. Give your content a little breathing room.

```css
div {
    padding: 10px;
}
```

### Borders

Specify the border of an element. Because every element deserves a stylish frame.

```css
div {
    border: 1px solid black;
}
```

### Width and Height

Specify the width and height of an element. Because size matters, at least in CSS.

```css
div {
    width: 100px;
    height: 100px;
}
```

## 6. Backgrounds

### Background Color

Specify the background color. Give your page a splash of color.

```css
body {
    background-color: lightgray;
}
```

### Background Image

Specify the background image. Because a picture is worth a thousand properties.

```css
body {
    background-image: url('image.jpg');
}
```

### Background Position

Specify the position of the background image. Center it like it's the star of the show.

```css
body {
    background-position: center;
}
```

### Background Repeat

Specify whether the background image should repeat. Because sometimes, less is more.

```css
body {
    background-repeat: no-repeat;
}
```

## 7. Display and Visibility

### Display

Specify how an element is displayed. Hide and seek for web elements.

```css
div {
    display: none;
}
```

### Visibility

Specify whether an element is visible. Because sometimes, you need to make things disappear.

```css
div {
    visibility: hidden;
}
```

## 8. Positioning

### Static Positioning

The default positioning for elements. Like staying in your comfort zone.

```css
div {
    position: static;
}
```

### Relative Positioning

Position an element relative to its normal position. A little nudge here and there.

```css
div {
    position: relative;
    top: 10px;
    left: 10px;
}
```

### Absolute Positioning

Position an element relative to its nearest positioned ancestor. It's like following the leader.

```css
div {
    position: absolute;
    top: 10px;
    right: 10px;
}
```

### Fixed Positioning

Position an element relative to the browser window. Because some elements just need to stay put.

```css
div {
    position: fixed;
    bottom: 0;
    right: 0;
}
```

## 9. Flexbox

### Container

Use `display: flex` to create a flex container. Flex your layout muscles.

```css
.container {
    display: flex;
}
```

### Direction

Specify the direction of the flex items. Because sometimes, you need to row, row, row your layout.

```css
.container {
    flex-direction: row;
}
```

### Justify Content

Align flex items along the main axis. Center stage for your content.

```css
.container {
    justify-content: center;
}
```

### Align Items

Align flex items along the cross axis. Keep things in line.

```css
.container {
    align-items: center;
}
```

## 10. Grid

### Container

Use `display: grid` to create a grid container. Layout perfection.

```css
.container {
    display: grid;
}
```

### Columns and Rows

Specify the number of columns and rows in the grid. Organize your chaos.

```css
.container {
    grid-template-columns: repeat(3, 1fr);
    grid-template-rows: repeat(2, 100px);
}
```

### Gap

Specify the gap between grid items. Because spacing is everything.

```css
.container {
    gap: 10px;
}
```

### Item Positioning

Specify the position of grid items. Because every item deserves its place.

```css
.item {
    grid-column: 1 / 3;
    grid-row: 1 / 2;
}
```

That’s it! This CSS Cheatsheet should cover everything you need to style your web pages effectively and with a sense of humor. Happy styling! 😄
