<h1>Contributing</h1>

[TOC]

We encourage contribution to the VW Sandbox.  Below are some possible different ways to contribute.  We are always interested in featuring better demonstration content creating using the VW Sandbox.

# Contribute to Documentation

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