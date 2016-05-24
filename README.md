# The VW Sandbox Manual

This is the repository for the VW Sandbox Manual.  The manual provides users with information to use the VW Sandbox. 

## Building the documentation
 
1. Install [MkDocs](http://www.mkdocs.org/#installation)
1. git clone https://github.com/adlnet/SandboxDocs
1. mkdocs serve

The mkdocs serve command will generate the documentation and host it at [http://localhost:8000](http://localhost:8000) by default.

NOTE: It is good practice to build the documentation locally before deploying to prevent build errors.  If a build error does occur on the readthedocs site, check the [Builds](https://readthedocs.org/projects/sandboxdocs/builds/) page from the lower left hand corner link labeled Read the Docs.

## General Style

Use the name "VW Sandbox" when refering to the software.

Highlight menu items (e.g., `File` > `Save`), tools (e.g., `Painter`), windows (e.g., `Map Browser`), keyboard buttons (e.g., `ALT`), and single lines of code (e.g., `var = foo;`) using backtick quotes(`).

## Linking

Use relative links between documents rather than absolute links wherever possible to support maximum flexibility in testing and deployment.

When linking to a section in the same document, simply use # and the header name in lower case with "-" (separator) in place of spaces.  So if we are linking to "Header Name" in the same document, we'd use: 
```
[Link to section in the same document](#header-name)
```

If you are linking to a different document or a section in a different document, you must include the document in the link:

```
[Link to section in another document](other-doc.md#header-name)
```

## Titles and Tables of Contents

Use `<h1>` HTML header tags for titles of documents to prevent the titles of documents appearing twice in navigation table of contents.

```
<h1>Title of Document</h1>
```

Use `<h2>` HTML header tags for the title of document table of contents.  Use the word "Contents" in the `<h2>` tags.  Below the `<h2>` tags, add the markdown `[TOC]` extension, which will generate the table of contents. 

```
<h2>Contents</h2>
[TOC]
```

## Notes and Warnings

The documentation settings include the [admonition](https://pythonhosted.org/Markdown/extensions/admonition.html) markdown extension.

If you want to make a note, use:

```
!!! note:
	A clear and concise note.
```


If you want to add a warning, use:

```
!!! warning:
	Careful not to ...
```

## Dashes

The documentation settings also include the [SmartyPants](https://pythonhosted.org/Markdown/extensions/smarty.html) markdown extension.

If you want to make a dash, write it using `--` (two hyphens).  These will be replaced to produce the appropriate HTML Entity.

## Embedded comments

If you want o provide a comment in the manual to guide further development of the manual (e.g, add information about XYZ here), then create a markdown comment using:

```
[comment]: <> (add information about XYZ here)
```

# Contribute to Documentation

Please contribute to the documentation.  

The documentation is written in [Markdown Syntax](https://daringfireball.net/projects/markdown/syntax) and generated using [MkDocs](http://www.mkdocs.org/).  It is version controlled in this GitHub repository.  Commits to the master branch are automatically built and published to the [documentation website](http://sandboxdocs.readthedocs.org/) hosted by [Read the Docs](https://readthedocs.org/).  The following style guide should help ensure a consistent reading experience.

For more information on contributing to the project, view the full  [documentation](https://github.com/adlnet/SandboxDocs/blob/master/docs/contributing.md) for contributing.
