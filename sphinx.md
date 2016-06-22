```
pip install sphinx
pip install sphinx_rtd_theme
```
## Getting Started

Create docs folder:

```bash

   $ mkdir docs
   $ cd docs
```

Create the sphinx skeleton:

```
$ sphinx-quickstart

> Root path for the documentation [.]:
> Separate source and build directories (y/n) [n]: y
> Name prefix for templates and static dir [_]:
> Project name: Giza
> Author name(s): Mac Pingu
> Project version: 0.1
> Project release [0.1]:
> Project language [en]:
> Source file suffix [.rst]:
> Name of your master document (without suffix) [index]:
> Do you want to use the epub builder (y/n) [n]:
> autodoc: automatically insert docstrings from modules (y/n) [n]:
> doctest: automatically test code snippets in doctest blocks (y/n) [n]:
> intersphinx: link between Sphinx documentation of different projects (y/n) [n]: y
> todo: write "todo" entries that can be shown or hidden on build (y/n) [n]: y
> coverage: checks for documentation coverage (y/n) [n]:
> imgmath: include math, rendered as PNG or SVG images (y/n) [n]:
> mathjax: include math, rendered in the browser by MathJax (y/n) [n]:
> ifconfig: conditional inclusion of content based on config values (y/n) [n]:
> viewcode: include links to the source code of documented Python objects (y/n) [n]: y
> githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]:
> Create Makefile? (y/n) [y]:
> Create Windows command file? (y/n) [y]:
```
Your file system should now look similar to this:

```
mypackage
├── src
└── docs
    ├── Makefile
    ├── make.bat
    ├── build
    └── sources
         ├── conf.py
         └── index.rst
```
Let's build our docs into HTML to see how it works. Simply run:

# Inside top-level docs/ directory.

$ make html

hange the Look

You can change the look of the generated documents by setting the html_theme setting in your conf.py. Go ahead and set it like this:

html_theme = 'sphinxdoc'

If you rebuild your documentation, you will see the new theme:

$ make html

Editar `html_theme = 'sphinx_rtd_theme'` en `conf.py`

Check the Links

Sphinx can check if the links in your document are valid: make linkcheck

cd .. git init git add . git commit -m 'make html' git push -u origin master

Agregar Disqus

```
echo "sphinxcontrib-disqus" > requirements.txt
```

Luego `git push` a readthedocs.

Agregar Disqus a `Index.rst`

```
.. disqus::
    :disqus_identifier: index
```

Make html

```
    cd docs/_build/html
    python -m SimpleHTTPServer 8080
    firefox http://localhost:8080/
```
