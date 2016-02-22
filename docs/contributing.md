<h1>Contributing</h1>

[TOC]

We encourage contribution to the VW Sandbox.  Below are some possible different ways to contribute.  We are always interested in featuring better demonstration content creating using the VW Sandbox.

# Contribute to Documentation

Please contribute to the documentation.  

The documentation is written in [Markdown Syntax](https://daringfireball.net/projects/markdown/syntax) and generated using [MkDocs](http://www.mkdocs.org/).  It is version controlled in the [SandboxDocs](https://github.com/adlnet/SandboxDocs) GitHub repository.  Commits to the master branch are automatically built and published to the [documentation website](http://sandboxdocs.readthedocs.org/) hosted by [Read the Docs](https://readthedocs.org/).  The following style guide should help ensure a consistent reading experience.

## Building the documentation
 
1. Install [MkDocs](http://www.mkdocs.org/#installation)
1. git clone https://github.com/adlnet/SandboxDocs
1. mkdocs serve

The mkdocs serve command will generate the documentation and host it at [http://localhost:8000](http://localhost:8000) by default.

!!! note:
	It is good practice to build the documentation locally before deploying to prevent build errors.  If a build error does occur on the readthedocs site, check the [Builds](https://readthedocs.org/projects/sandboxdocs/builds/) page from the lower left hand corner link labeled Read the Docs.

## General Style

Use the name "VW Sandbox" when refering to the software.


## Capitalize Headers

Capitalize header titles with five or more letters.

You can use the [http://titlecapitalization.com/](http://titlecapitalization.com/) tool to automatically capitalize your title using the above rules.


## Capitalize System Component Keywords

Capitalize, but don't highlight, keywords for commonly referred to system components like the Engine, Scene, Editor, Editors (e.g., Physics Editor, Heirarchy Editor), or Content Libraries.


## Highlighted Words 

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

The above will produce:
!!! note:
	A clear and concise note.


If you want to add a warning, use:

```
!!! warning:
	Careful not to ...
```

The above will produce:
!!! warning:
	Careful not to ...

## Dashes

The documentation settings also include the [SmartyPants](https://pythonhosted.org/Markdown/extensions/smarty.html) markdown extension.

If you want to make a dash, write it using `--` (two hyphens).  These will be replaced to produce the appropriate HTML Entity (--).

## Embedded comments

If you want o provide a comment in the manual to guide further development of the manual (e.g, add information about XYZ here), then create a markdown comment using:

```
[comment]: <> (add information about XYZ here)
```



# Contribute 3D Models

Contact `sandbox@adlnet.gov` to find the easiest way to share game ready openly licensed 3D models with the community.

# Contribute Simulation Objects

Contact `sandbox@adlnet.gov` to find the easist way to share your well constructed simulation objects with the community.

# Contribute to Core Development

Please send pull requests through [https://github.com/adlnet/Sandbox](https://github.com/adlnet/Sandbox).

Most development takes place on a development branch and is periodically merged with master and released.  Release numbers are based on the type of changes in accordance with [Semantic Versioning 2.0.0](http://semver.org/spec/v2.0.0.html).  Releases should include tagging the master branch with the release number, providing release notes, and updating the ADL hosted instance.

Planning and tracking is done using a [public PivotalTracker](https://www.pivotaltracker.com/n/projects/892864).  If you're interested in possible ideas for development contributions, we keep an icebox of stories in PivotalTracker.

# Contribute Issues

Found a bug or have a feature recommendation?  Please share it through GitHub Issues at [https://github.com/adlnet/Sandbox/issues/](https://github.com/adlnet/Sandbox/issues).