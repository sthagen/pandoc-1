
Pandoc (Python Library)
================================================================================

![Python](https://img.shields.io/pypi/pyversions/pandoc.svg)
[![PyPI version](https://img.shields.io/pypi/v/pandoc.svg)](https://pypi.python.org/pypi/pandoc)
[![Mkdocs](https://img.shields.io/badge/doc-mkdocs-845ed7.svg)](https://boisgera.github.io/pandoc)
[![GitHub discussions](https://img.shields.io/badge/discuss-online-845ef7)](https://github.com/boisgera/pandoc/discussions)
[![Downloads](https://pepy.tech/badge/pandoc)](https://pepy.tech/project/pandoc)
[![GitHub stars](https://img.shields.io/github/stars/boisgera/pandoc?style=flat)](https://github.com/boisgera/pandoc/stargazers)

[![linux](https://github.com/boisgera/pandoc/actions/workflows/linux.yml/badge.svg)](https://github.com/boisgera/pandoc/actions/workflows/linux.yml)
[![macos](https://github.com/boisgera/pandoc/actions/workflows/macos.yml/badge.svg)](https://github.com/boisgera/pandoc/actions/workflows/macos.yml)
[![windows](https://github.com/boisgera/pandoc/actions/workflows/windows.yml/badge.svg)](https://github.com/boisgera/pandoc/actions/workflows/windows.yml)


🚀 Getting started
--------------------------------------------------------------------------------

Install [Pandoc] first, for example with [conda]:

    $ conda install -c conda-forge pandoc

Then, install the Pandoc Python Library with pip:

    $ pip install --upgrade pandoc


🌌 Overview 
--------------------------------------------------------------------------------

[Pandoc] is the awesome open-source command-line tool that converts documents 
from one format to another. The project was initiated by [John MacFarlane]; 
under the hood, it's a [Haskell] library.

The Pandoc Python Library brings [Pandoc]'s document model to Python:

    $ echo "Hello world!" | python -m pandoc read 
    Pandoc(Meta({}), [Para([Str('Hello'), Space(), Str('world!')])])

It can be used to analyze, create and transform documents, in Python:

    >>> import pandoc
    >>> text = "Hello world!"
    >>> doc = pandoc.read(text)
    >>> doc
    Pandoc(Meta({}), [Para([Str('Hello'), Space(), Str('world!')])])

    >>> paragraph = doc[1][0]
    >>> paragraph
    Para([Str('Hello'), Space(), Str('world!')])
    >>> from pandoc.types import Str
    >>> paragraph[0][2] = Str('Python!')
    >>> text = pandoc.write(doc)
    >>> print(text)
    Hello Python!

For more information, refer to the  [📖 documentation][doc].

[Pandoc]: https://pandoc.org/
[John MacFarlane]: https://johnmacfarlane.net/
[pandoc-install]: https://pandoc.org/installing.html
[conda]: https://docs.conda.io
[Haskell]: https://www.haskell.org/
[Python]: https://www.python.org/
[TPD]: https://hackage.haskell.org/package/pandoc-types-1.20/docs/Text-Pandoc-Definition.html
[doc]: https://boisgera.github.io/pandoc
