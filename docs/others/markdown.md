# Markdown Guide

<!-- for joplin users -->
<!-- ${toc} -->

> Markdown is a text-to-HTML conversion tool for web writers. Markdown allows you to write using an easy-to-read, easy-to-write plain text format, then convert it to structurally valid XHTML (or HTML). [source](https://daringfireball.net/projects/markdown/)

## Usefull links

- [Common Mark standard](https://commonmark.org/)
- [Common Mark official specs](https://spec.commonmark.org/)

## Tips & Tricks

### Create an anchor 

[source](https://discourse.joplinapp.org/t/anchors/2928/4)

```md
<!--link-->
Take me to [pookie](##pookie)
<!--anchor-->
## pookie
```

[Link](#test-anchor)

Notes:
- the link must be lower case
- replace space in title with `-`

## Cheat Sheet

This is a quick summary of the Markdown syntax.

|     | Markdown | Rendered Output
| --- | --- | ---
| **Heading 1** | <pre># Heading 1</pre> | <h1>Heading 1</h1>
| **Heading 2** | <pre>## Heading 2</pre> | <h2>Heading 2</h2>
| **Heading 3** | <pre>### Heading 3</pre> | <h3>Heading 3</h3>
| **Bold** | <pre>This is some `**bold text**`</pre> | This is some <strong>bold text</strong>
| **Italic** | <pre>This is some `*italic text*`</pre> | This is some <i>italic text</i>
| **Blockquotes** | <pre>> Kent.<br>> Where's the king?<br><br>> Gent.<br>> Contending with the<br>> fretful elements</pre> | <blockquote>Kent.<br>Where's the king?<br><br>Gent.<br>Contending with<br>the fretful elements</blockquote>
| **List** | <pre>* Milk<br>* Eggs<br>* Beers<br>    * Desperados<br>    * Heineken<br>* Ham</pre> | <ul><li>Milk</li><li>Eggs</li><li>Beers<ul><li>Desperados</li><li>Heineken</li></ul></li><li>Ham</li></ul>
| **Ordered list** | <pre>1. Introduction<br>2. Main topic<br>    1. First sub-topic<br>    2. Second sub-topic<br>3. Conclusion</pre> | <ol><li>Introduction</li><li>Main topic<ol><li>First sub-topic</li><li>Second sub-topic</li></ol></li><li>Conclusion</li></ol>
| **Inline code** | <pre>This is \`someJavaScript()\`</pre> | This is `someJavaScript()`
| **Code block** | <pre>Here's some JavaScript code:<br><br>\`\`\`<br>function hello() {<br>    alert('hello');<br>}<br>\`\`\`<br><br>Language is normally auto-detected,<br>but it can also be specified:<br><br>\`\`\`sql<br>SELECT * FROM users;<br>DELETE FROM sessions;<br>\`\`\`</pre> | Here's some JavaScript code:<br><br><pre>function hello() {<br>&nbsp;&nbsp;&nbsp;&nbsp;alert('hello');<br>}</pre><br>Language is normally auto-detected, but it can also be specified:<br><br><pre>SELECT * FROM users;<br>DELETE FROM sessions;</pre>
| **Unformatted text** | <pre>Indent with a tab or 4 spaces<br>for unformatted text.<br><br>    This text will not be formatted:<br><br>    Robert'); DROP TABLE students;--</pre> | Indent with a tab or 4 spaces for unformatted text.<br><br><pre>This text will not be formatted:<br><br>Robert'); DROP TABLE students;--</pre>
| **Link** | <pre>This is detected as a link:<br><br>`https://hello-there.org`<br><br>And this is a link anchoring text content:<br><br>`[Hello-There](https://hello-there.org)`<br><br>And this is a link, with a title,<br>anchoring text content:<br><br>`[Hello-There](https://hello-there.org "Z01P24 Hello-There promotion")`</pre> | This is detected as a link:<br><br>https://hello-there.org<br><br>And this is a link anchoring text content:<br><br>[Hello-There](https://hello-there.org)<br><br>And this is a link, with a title,<br>anchoring text content:<br><br>[Hello-There](https://hello-there.org "Z01P24 Hello-There promotion") (_hint: hover over the link_)
| **Images** | <pre>`![Joplin icon](https://git.io/JenGk)`</pre> | ![Here's Joplin icon](https://git.io/JenGk)
| **Horizontal Rule** | <pre>One rule:<br>\*\*\*<br>Another rule:<br>\-\-\-</pre> | One rule:<hr><br>Another rule:<br><hr>
| **Tables** | [See below](#tables) | 

### Tables

Tables are created using pipes `|` and and hyphens `-`. This is a Markdown table:

#### Basic tables

First Header | Second Header
-|-
Content Cell | Content Cell
Content Cell | Content Cell

```markdown
First Header | Second Header
-|-
Content Cell | Content Cell
Content Cell | Content Cell
```

~~Note that there must be at least 3 dashes separating each header cell.~~

#### align tables

Colons can be used to align columns:

Tables | Are | Cool
-|:-:|-:
col 3 is | right-aligned | $1600
col 2 is | centered | $12

```markdown
| Tables        | Are           | Cool  |
| ------------- |:-------------:| -----:|
| col 3 is      | right-aligned | $1600 |
| col 2 is      | centered      |   $12 |
```

## Test Anchor

[top](#markdown-guide)
