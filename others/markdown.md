# Markdown Basic Syntax

## Topics

- [Headings](#headings)
- [Emphasis](#emphasis)
- [UnOrdered Lists](#unordered-lists)
- [Ordered Lists](#ordered-lists)
- [Links](#links)
- [Images](#images)
- [Code Blocks](#code-blocks)
- [Inline HTML](#inline-html)
- [Tables](#tables)
- [Footnotes](#footnotes)
- [Definition Lists](#definition-lists)
- [Task Lists](#task-lists)
- [Emoji](#emoji)
- [HTML Blocks](#html-blocks)
- [Math and LaTeX](#math-and-latex)

### Headings

Use `#` for headings. The number of `#` symbols corresponds to the heading level.

```markdown
# Heading 1

## Heading 2

### Heading 3

#### Heading 4

##### Heading 5

###### Heading 6
```

### Emphasis

Bold: **text** or **text**
Italic: _text_ or _text_
Strikethrough: ~~text~~

```markdown
**Bold Text**
_Italic Text_
~~Strikethrough Text~~
```

### Unordered Lists

Use -, \*, or + for unordered lists.

```markdown
- Item 1
- Item 2
  - Subitem 2.1
  - Subitem 2.2

* Item 3
* Item 4
```

### Ordered Lists

Use numbers followed by a period for ordered lists.

```markdown
1. First item
2. Second item
3. Third item
   1. Subitem 3.1
   2. Subitem 3.2
```

### Links

```markdown
[Link Text](https://www.example.com)
```

### Images

```markdown
![Alt Text](https://www.example.com/image.jpg)
```

### Tables

```markdown
| Header 1 | Header 2 |
| -------- | -------- |
| Cell 1   | Cell 2   |
| Cell 3   | Cell 4   |
```

Code Blocks
Use triple backticks ``` for code blocks.

```python
def hello_world():
    print("Hello, World!")
```

### Inline HTML

You can also use inline HTML for more advanced formatting.

```markdown
<p>This is a paragraph in HTML.</p>
```

## Footnotes

Here is a footnote reference[^1].

```markdown
[^1]: This is the footnote.
```

## Definition Lists

```markdown
Term 1
: Definition 1

Term 2
: Definition 2
```

## Task Lists

```markdown
- [x] Completed task
- [ ] Incomplete task
```

## Emoji

```markdown
:smile: :heart: :+1:
```

## Math and LaTeX

```markdown
Inline math: $E = mc^2$

Block math:

$$
E = mc^2
$$
```
