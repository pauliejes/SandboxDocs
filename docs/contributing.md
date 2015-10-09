<h1>Contributing</h1>

Contributions of code, issues, questions, and discussion are encouraged.

<h2>Contents</h2>
[TOC]

# Documentation

Please contribute to the documentation.  The following style guide should help ensure a consistent reading experience.

Use the name "VW Sandbox" when refering to the software.

Highlight menu items (e.g., `File` > `Save`), tools (e.g., `Painter`), windows (e.g., `Map Browser`), keyboard buttons (e.g., `ALT`), and single lines of code (e.g., `var = foo;`) using backtick quotes(`).

## Linking

Use relative links between documents rather than absolute links wherever possible to support maximum flexibility in testing and deployment.

When linking to a section in the same document, simply use # and the header name in lower case with "-" (separator) in place of spaces.  So if we are linking to "Header Name" in the same document, we'd use: 
```
[Link to section in the same document](#header-name)
```

## Titles and Tables of Contents

Use `<h1>` HTML header tags for titles of documents to prevent the titles of documents appearing twice in navigation table of contents.

```
<h1>Title of Document</h1>
```

Use `<h2>` HTML header tags for the title of document table of contents.  Use the word "Contents" proceeded by the markdown `[TOC]` extension.  

```
<h2>Contents</h2>
[TOC]
```

