# Markdown <!-- omit in toc -->

This documentation targets any Markdown rendering platform who adhers to the official [CommonMark](https://spec.commonmark.org) specification. It also targets GitHub. [GitHub Flavored Markdown](https://github.github.com/gfm/) is a superset of CommonMark. Parts of this documentation who apply only to GitHub are explicitly titled "... GitHub Flavored".

- [Recommended Tools and Settings](#recommended-tools-and-settings)
- [Headings](#headings)
- [Code](#code)
    - [Code Spans](#code-spans)
    - [Code Blocks](#code-blocks)
        - [Indented Code Blocks](#indented-code-blocks)
        - [Fenced Code Blocks](#fenced-code-blocks)
- [Block Quotes](#block-quotes)
- [Lists](#lists)
    - [Bulleted Lists](#bulleted-lists)
    - [Ordered Lists](#ordered-lists)
- [Tables (GitHub Flavored)](#tables-github-flavored)
- [Table of Contents (GitHub Flavored)](#table-of-contents-github-flavored)
- [Escapes](#escapes)
    - [Escapes in Regular Text](#escapes-in-regular-text)
    - [Escapes in Code Spans](#escapes-in-code-spans)

# Recommended Tools and Settings

For Markdown editing, I recommend using [Visual Studio Code](https://code.visualstudio.com). It has a superb built-in Markdown editor who fully adhers to the official [CommonMark](https://spec.commonmark.org) specification and provides live previewing. On top of that, I recommend installing the [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) extension and applying the following settings. 

| VS Code Setting | Value | Meaning |
| - | - | - |
| "markdown.preview.linkify" | `false` | E.g., don't interpret ASP.NET as a link. |
| "markdown.extension.toc.githubCompatibility" | `true`  | Ensure table of contents is understood by GitHub. |
| "markdown.extension.tableFormatter.normalizeIndentation" | `true`  | When formatting the Markdown code, equalize the widths of table cells by filling in spaces where necessary (if the heading separators are at least triples `---`). |



# Headings

* The following Markdown code:

  ```md
  # Heading Level 1
  ## Heading Level 2
  ### Heading Level 3
  #### Heading Level 4
  ##### Heading Level 5
  ###### Heading Level 6 
  ```

* ... is rendered as follows:

  # Heading Level 1 <!-- omit in toc -->
  ## Heading Level 2 <!-- omit in toc -->
  ### Heading Level 3 <!-- omit in toc -->
  #### Heading Level 4 <!-- omit in toc -->
  ##### Heading Level 5 <!-- omit in toc -->
  ###### Heading Level 6  <!-- omit in toc -->


# Code

## Code Spans

Start and stop a code span with equal numbers of `` ` ``. Any beginning or trailing spaces ar ignored.

```md
This represents `a code span` (inline code).  
This also represents ``a code span`` (inline code).  
This, too, represents ``` a code span ``` (inline code).
```

This represents `a code span` (inline code).  
This also represents ``a code span`` (inline code).  
This, too, represents ``` a code span ``` (inline code).

## Code Blocks

### Indented Code Blocks

Use at least four spaces:

```md
    This is some code
    More code
```

    This is some code
    More code

### Fenced Code Blocks

Use ```` ``` ```` or `~~~` as fence, optionally with a language specifier such as `ts`, `cs`, `js`, `java`, `html`, `sql`, etc.

    ```ts
    export class AppComponent {
        model = new Model();
        // etc.
    }
    ```

```ts
export class AppComponent {
    model = new Model();
    // etc.
}
```



# Block Quotes

```md
> Block quote
>> Nested block quote
>>> Double nested block quote
```

> Block quote
>> Nested block quote
>>> Double nested block quote

# Lists

## Bulleted Lists

 Use `-`, `+`, or `*` as bullet character.

```md
- Item
    - Nested item
        - Double nested item 
- Item
```

- Item
    - Nested item
        - Double nested item
- Item 

## Ordered Lists

Digits plus `.` or `)`.

```md
1. Item
    1. Nested item
    2. Nested item
        1. Double nested item
2. Item
3. Item
```

1. Item
    1. Nested item
    2. Nested item
        1. Double nested item
2. Item
3. Item

# Tables (GitHub Flavored)

```md
|Heading1|Heading2|Heading3|
|-|-|-|
|Cell1|Cell2|Cell3|
```

|Heading1|Heading2|Heading3|
|-|-|-|
|Cell1|Cell2|Cell3|

In order to automatically apply equal widths to the table cells in the the above Markdown code, proceed as follows:
* Ensure that each heading separator is at least a triple: `---`.
* Empty cells will be "optimized" away, such as in `|xxx||yyy|` -> `|xxx|yyy|`, which can mess up the table. To avoid this, ensure that each empty cell contains at least a single space.
* In [VS Code](https://code.visualstudio.com), with the [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) extension installed, ensure that the setting "markdown.extension.tableFormatter.normalizeIndentation" is `true`.
* Apply the *Format Document* command.

This will format the above Markdown code as follows:

```md
| Heading1 | Heading2 | Heading3 |
| -------- | -------- | -------- |
| Cell1    | Cell2    | Cell3    |
```

# Table of Contents (GitHub Flavored)

Prerequisite: Use [VS Code](https://code.visualstudio.com) with the [Markdown All in One](https://marketplace.visualstudio.com/items?itemName=yzhang.markdown-all-in-one) extension and the setting "markdown.extension.toc.githubCompatibility": `true`.

Apply the command *Markdown:Create Table of Contents*, which will create a TOC with links to the headings in the document.

To ignore some of the headings in the TOC, use either of the following methods:

* Use an *HTML heading tag* instead of a *markdown format specifier* to define the heading. E.g.,  

  ```html
  <h1>My Title<h1>
  ```
  instead of  

  ```md
  # My Title
  ```
  
* Append the Markdown heading with an `<!-- omit in toc -->` HTML comment. E.g.,  
  ```md
  # My Title <!-- omit in toc -->
  ```

# Escapes

## Escapes in Regular Text

Any punctuation character can be escaped by a preceding `\`.

## Escapes in Code Spans

Within a code span, the `` ` `` character (or repetitions of it) can be escaped by declaring the code span with multiple `` ` ``s.

E.g., to escape `` ` ``, use ``` `` ```:

```md
``let version = 2015; let s = `An ES${version} template literal`;``
```

... which produces: ``let version = 2015; let s = `An ES${version} template literal`;``

To escape ``` `` ```, use ```` ``` ```` :

```md
```let [<Test>] ``One and one is two in F#``() = 1 + 1 |> should equal 2```
```

... which produces: ```let [<Test>] ``One and one is two in F#``() = 1 + 1 |> should equal 2```

Besides `` ` `` , no other character can be escaped within a code span (each character simply represents itself).

