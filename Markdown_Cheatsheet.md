# Markdown Cheatsheet

This **cheatsheet** covers the most commonly used **Markdown** syntax for *formatting text*, [creating links](http://epic.free.nf), embedding images, and more. Perfect for beginners and pros alike!

## 1. Headings

Use # to create headings. The number of # symbols determines the heading level (H1 to H6).

# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6

## 2. Text Formatting

Bold
Wrap text with double asterisks (**) or double underscores (__).

**Bold text**
__Bold text__
Italics
Wrap text with single asterisks (*) or single underscores (_).

*Italic text*
_Italic text_
Bold + Italics
Combine bold and italics by using triple asterisks (***) or underscores (___).

***Bold and italic***
___Bold and italic___
Strikethrough
Use double tildes (~~) to strike through text.

~~Strikethrough text~~

## 3. Lists
Unordered Lists
Use -, *, or + for bullet points.

- Item 1
- Item 2
  - Sub-item 2.1
  - Sub-item 2.2
Ordered Lists
Use numbers followed by a period (.).

1. First item
2. Second item
   1. Sub-item 2.1
   2. Sub-item 2.2


## 4. Links
Inline Links
Wrap the link text in square brackets ([]) and the URL in parentheses (()).

[Ætheria Calendar](http://epic.free.nf)
Reference Links
Define a reference ID and use it later in the document.

[Ætheria Calendar](http://epic.free.nf)


## 5. Images
Inline Images
Use an exclamation mark (!), followed by alt text in square brackets ([]) and the image URL in parentheses (()).

![Alt text](https://example.com/image.jpg)
Reference Images
Define a reference ID and use it later in the document.

![Alt text][logo]

[logo]: https://example.com/image.jpg


## 6. Code

Inline Code
Wrap code snippets in backticks (`).

Use `let x = 10;` to declare a variable.

Code Blocks
Use triple backticks (```) or indent lines with four spaces.

```javascript
function greet() {
    console.log("Hello, World!");
}
```

Specify the language after the opening triple backticks for syntax highlighting:

```python
def greet():
    print("Hello, World!")
```

## **7. Blockquotes**

Use a greater-than symbol (`>`) to create blockquotes.

> This is a blockquote.
>
> > Nested blockquote.

## 8. Horizontal Rules
Create horizontal rules with three or more hyphens (---), asterisks (***), or underscores (___).

---
***
___

## 9. Tables

Create tables using pipes (|) and hyphens (-). Align columns with colons (:).

| Header 1 | Header 2 | Header 3 |
|----------|:--------:|---------:|
| Left     | Center   | Right    |
| Data 1   | Data 2   | Data 3   |

## 10. Escaping Characters

Use a backslash (\) to escape special characters like *, _, `, etc.

\*This is not italic\*

## 11. Task Lists

Create task lists with checkboxes using [ ] for unchecked and [x] for checked items.

- [x] Task 1 (completed)
- [ ] Task 2 (not completed)
- [x] Task 3 (completed)

## 12. Footnotes

Add footnotes with [^label] and define them at the bottom of the document.

Here's a footnote reference.[^1]

[^1]: This is the footnote content.

## 13. Special Features

HTML in Markdown
You can embed raw HTML in Markdown for advanced styling.

<div style="color: red;">This text is red.</div>

Emoji Support
Use emoji shortcuts or Unicode to include emojis.

:smile: :thumbsup: ❤️

## 14. Advanced Tips

Anchors for Headings
Add custom IDs to headings for direct linking.

## My Section {#custom-id}
Link to it like this:

[Jump to My Section](#custom-id)

Line Breaks
End a line with two spaces to force a line break.

This is the first line.  
This is the second line.

That’s it! This Markdown Cheatsheet should cover everything you need to format your documents effectively. 😊
