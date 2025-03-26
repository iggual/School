# 🤓 HTML Cheatsheet

Welcome to the **HTML Cheatsheet** of the **Institute for Unconventional Genius (IUG)**! This guide will help you master the art of HTML with a touch of humor. Whether you're a newbie or a seasoned pro, you'll find something to chuckle about here. Let's dive in!

## 1. Basic Structure

Every HTML document starts with a doctype declaration and includes the basic structure of an HTML document. Think of it as the skeleton of your web page – without it, your page would be a jellyfish.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <!-- Content goes here -->
</body>
</html>
```

## 2. Headings

Headings are like the headlines of your web page. Use `<h1>` to `<h6>` to scream at your audience (or just whisper, if you prefer).

```html
<h1>THIS IS A LOUD HEADING</h1>
<h2>Still pretty loud</h2>
<h3>Moderate volume</h3>
<h4>Getting quieter...</h4>
<h5>Almost a whisper</h5>
<h6>Can you even hear me?</h6>
```

## 3. Paragraphs

Paragraphs are for when you have more to say than can fit in a heading. Use `<p>` to write your novel.

```html
<p>This is a paragraph. It's not as loud as a heading, but it still has a lot to say.</p>
```

## 4. Links

Links are like the teleportation devices of the web. Use `<a>` to transport your users to another dimension (or just another web page).

```html
<a href="http://example.com">Click here to be teleported</a>
```

## 5. Images

Images make your web page prettier. Use `<img>` to show off your cat pics.

```html
<img src="https://example.com/cat.jpg" alt="A cute cat">
```

## 6. Lists

Lists are for when you have more than one thing to say. 

### Unordered Lists

Use `<ul>` for unordered lists when you don't care about the order (like a grocery list).

```html
<ul>
    <li>Bananas</li>
    <li>Milk</li>
    <li>Chocolate</li>
</ul>
```

### Ordered Lists

Use `<ol>` for ordered lists when order matters (like steps to defuse a bomb).

```html
<ol>
    <li>Cut the red wire</li>
    <li>Cut the blue wire</li>
    <li>Run away</li>
</ol>
```

## 7. Tables

Tables are for organizing data, like your top 10 favorite ice cream flavors.

```html
<table>
    <tr>
        <th>Rank</th>
        <th>Flavor</th>
    </tr>
    <tr>
        <td>1</td>
        <td>Chocolate</td>
    </tr>
    <tr>
        <td>2</td>
        <td>Vanilla</td>
    </tr>
</table>
```

## 8. Forms

Forms are for collecting information, like your name, email, and deepest secrets.

```html
<form action="/submit" method="post">
    <label for="name">Name:</label>
    <input type="text" id="name" name="name">
    <button type="submit">Submit</button>
</form>
```

## 9. Blockquotes

Use `<blockquote>` to quote someone wise (or yourself, if you're feeling wise).

```html
<blockquote>
    "This is a blockquote. Very profound."
</blockquote>
```

## 10. Inline Code

Use `<code>` to show off your coding prowess.

```html
<p>Use the <code>let</code> keyword to declare a variable.</p>
```

## 11. Code Blocks

For when you need to show a larger chunk of code. Use `<pre>` and `<code>` to keep it formatted nicely.

```html
<pre><code>
function greet() {
    console.log("Hello, World!");
}
</code></pre>
```

## 12. Comments

Comments are for talking to yourself or leaving notes for future you. Use `<!-- -->` to keep them hidden from users.

```html
<!-- This is a comment. Don't forget to buy milk. -->
```

## 13. Entities

Use HTML entities to display reserved characters without breaking your code.

```html
<p>&lt;div&gt;This is a div&lt;/div&gt;</p>
```

## 14. Special Features

### Embedding Media

Use `<iframe>`, `<video>`, and `<audio>` to embed media and keep your users entertained.

```html
<iframe src="https://example.com" width="600" height="400"></iframe>

<video width="320" height="240" controls>
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video tag.
</video>

<audio controls>
    <source src="audio.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
```

### Semantic Elements

Use semantic elements like `<header>`, `<footer>`, `<section>`, and `<article>` to make your document as organized as your sock drawer (hopefully).

```html
<header>
    <h1>Welcome to My Website</h1>
</header>

<section>
    <h2>About Me</h2>
    <p>This is the about me section. Spoiler: I'm awesome.</p>
</section>

<article>
    <h2>My Article</h2>
    <p>This is an article. It's very interesting, I promise.</p>
</article>

<footer>
    <p>Footer content goes here. Like my contact info or a witty sign-off.</p>
</footer>
```

That’s it! This HTML Cheatsheet should cover everything you need to structure your web pages effectively and with a sense of humor. Happy coding! 😄
