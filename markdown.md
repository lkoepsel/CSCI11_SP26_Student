# Markdown Reference Sheet

A quick guide to Markdown. In VS Code, use the two columns with a magnifying class in the tab space to view the applied formatting.
![](./static/preview.png)

## Text Formatting

- **Bold**: `**text**` or `__text__`
- *Italic*: `*text*` or `_text_`
- ***Bold italic***: `***text***`
- ~~Strikethrough~~: `~~text~~`
- `Inline code`: `` `code` ``

## Headings


# Heading 1
## Heading 2
### Heading 3
#### Heading 4
##### Heading 5
###### Heading 6


## Lists

### Unordered Lists


- Item 1
- Item 2
  - Nested item 2.1
  - Nested item 2.2
- Item 3


### Ordered Lists


1. First item
2. Second item
   1. Nested item 2.1
   2. Nested item 2.2
3. Third item


## Code Blocks

Inline code with backticks:


Use `variable_name` in your code.


Code blocks with triple backticks and language specification:

```python
# this is a python program
python
def hello():
    print("Hello, World!")
```
```bash
# this is a comment in bash
cd CSCI11_Sp26_Student
pwd
```



## Links and Images

- Link: `[Link text](https://example.com)`
- Image: `![Alt text](image.jpg)`

## Blockquotes


> This is a blockquote.
> It can span multiple lines.
> It will be as long as the line allows.
> Then it will roll over to the next line.

## Horizontal Rule

---

## Tables

In the ----- line, use a ":" on the left for left-justified text, both sides for centered and right-side for right-justified text.

| Header 1 | Header 2 | Header 3 | Header 4 |
| -------- | :------: | :------- | -------: |
| text     | Centered | left | right |
| text     | text     | text     | numbers | 

## Line Breaks

Use two spaces at the end of a line or a blank line between paragraphs.

## Escaping Special Characters

Use backslash to escape markdown characters: `\*`, `\_`, `\[`, etc.