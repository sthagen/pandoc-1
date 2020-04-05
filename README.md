
Pandoc (Python Library)
================================================================================

<!--
[![PyPi](https://img.shields.io/pypi/v/pandoc.svg)](https://pypi.python.org/pypi/pandoc)
![Python](https://img.shields.io/pypi/pyversions/pandoc.svg)
![Status](https://img.shields.io/pypi/status/pandoc.svg)
-->
[![Travis CI Build Status](https://travis-ci.org/boisgera/pandoc.svg?branch=master)](https://travis-ci.org/boisgera/pandoc)
[![AppVeyor Build status](https://ci.appveyor.com/api/projects/status/usube01hmjcl1m0t?svg=true)](https://ci.appveyor.com/project/boisgera/pandoc)

*This README is about the 2.x branch of the library (alpha stage!). 
Install the latest version with:*

    $ pip install --upgrade git+https://github.com/boisgera/pandoc.git

This project provides a Pythonic data model for [Pandoc] documents :

    $ echo "Markdown text" | python -m pandoc read 
    Pandoc(Meta(map()), [Para([Str('Markdown'), Space(), Str('text')])])

A Pythonic Version of Pandoc
--------------------------------------------------------------------------------

[Pandoc] is the "document swiss army knife" made by [John MacFarlane].
It brings:

  - a command-line tool,

  - a [Haskell] library, 

  - a document (meta-)model.

The command line tool is what you need to convert documents from one format 
to another, for example Markdown to HTML or Markdown to PDF.
But to analyze, create or transform documents, 
you may find this Python library useful.

[Pandoc]: http://pandoc.org/
[John MacFarlane]: http://johnmacfarlane.net/
[Haskell]: https://www.haskell.org/
[Python]: https://www.python.org/

The basic process is the following:

 1. First, create a document; for example, read a Markdown text

        >>> import pandoc
        >>> markdown = "Hello"
        >>> doc = pandoc.read(markdown)
        >>> doc
        Pandoc(Meta(map()), [Para([Str(u'Hello!')])])

 2. Then, analyze and/or transform the document as you like

        >>> from pandoc.types import *
        >>> para = doc[1][0]
        >>> para
        Para([Str(u'Hello')])
        >>> contents = para[0]
        >>> contents
        [Str(u'Hello')]
        >>> contents.extend([Space(), Str("World!")])
        >>> doc
        Pandoc(Meta(map()), [Para([Str(u'Hello'), Space(), Str('World')])])

 3. Finally, output the new document as Markdown

        >>> pandoc.write(doc)
        u'Hello World\n'

    and optionally, generate its HTML version

        >>> pandoc.write(doc, file="doc.html")
        u'<p>Hello World</p>\n'


