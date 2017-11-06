# sphinx-doc
sphinx-doc is a way to write ebooks, documentation, or websites once and export to your desired output.  Exported formats include epub, html, pdf, etc.

# Creating a new sphinx-doc project

Install sphinx-doc according to their documentation.  Open a terminal.  Navigate to a new directory for your project.  Run the sphinx-quickstart program.

```sphinx-quickstart```

I used these answers:

```
> Root path for the documentation [.]: .
> Separate source and build directories (y/n) [n]: y
> Name prefix for templates and static dir [_]: _
> Project name: InsertProjectName
> Author name(s): InsertAuthorOrAuthorsHere
> Project version []: 1.0
> Project release [1.0]: 1.0
> Project language [en]: en
> Source file suffix [.rst]: .rst
> Name of your master document (without suffix) [index]: index
> Do you want to use the epub builder (y/n) [n]: y
> autodoc: automatically insert docstrings from modules (y/n) [n]: y
> doctest: automatically test code snippets in doctest blocks (y/n) [n]: n
> intersphinx: link between Sphinx documentation of different projects (y/n) [n]: n
> todo: write "todo" entries that can be shown or hidden on build (y/n) [n]: n
> coverage: checks for documentation coverage (y/n) [n]: n
> imgmath: include math, rendered as PNG or SVG images (y/n) [n]: n
> mathjax: include math, rendered in the browser by MathJax (y/n) [n]: n
> ifconfig: conditional inclusion of content based on config values (y/n) [n]: n
> viewcode: include links to the source code of documented Python objects (y/n) [n]: n
> githubpages: create .nojekyll file to publish the document on GitHub pages (y/n) [n]: n
> Create Makefile? (y/n) [y]: y
> Create Windows command file? (y/n) [y]: y
```

After this the directory trees are created.  Edit ./source/index.rst to modify the document.

Build a new epub into the build directory with this command:

```sphinx-build -b epub source build```

# conf.py

[config.py epub options](http://www.sphinx-doc.org/en/stable/config.html#options-for-epub-output)

An example conf.py file I have used can be found [here](https://github.com/GhostCityGames/Midnight-Riders/blob/master/source/conf.py).

```
# epub cover image
epub_cover = ('_static/mr-cover.png', '')

# epub index
epub_use_index = False

# If true, "Created using Sphinx" is shown in the HTML footer. Default is True.
#
html_show_sphinx = False
```

# Templates

Themes are located in the /usr/share/sphinx/themes/ folder.

The default theme can be found in the /usr/share/sphinx/themes/basic folder.

[Templating](http://www.sphinx-doc.org/en/stable/templating.html)

[Theming at tinkerer.me](http://tinkerer.me/doc/theming.html)

Adding creative commons
TP from https://groups.google.com/forum/#!topic/sphinx-users/f3Yl45l1KYg suggests overwriting the footer with a template:

Template modifiers can be placed in the file ./source/_templates/layout.html

CC BY-SA 4.0 INTL
```
{% extends "!layout.html" %}
{%- block footer %}
{{ super() }}
  <div class="footer">
    <span class="creativecommons">
      <a href="https://creativecommons.org/licenses/by-sa/4.0/" >
        <img src="{{ pathto("_static/ccby-sa4.0intl88x31.png", 1) }}"
          alt="Creative Commons License"/></a>
      This work is licensed under a
      <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
        Creative Commons Attribution-ShareAlike 4.0 International License
      </a>
    </span>
  </div>
{%- endblock %}
```

Removing the navigation links at the top of each page

```
{% block relbar1 %}{% endblock %}
```

# Examples
https://github.com/GhostCityGames/Midnight-Riders

http://www.sphinx-doc.org/en/stable/tutorial.html

https://github.com/sphinx-doc/sphinx/blob/master/EXAMPLES

Front: https://docs.chef.io/index.html Back: https://github.com/chef/chef-web-docs/tree/master/chef_master/source

https://github.com/yoloseem/awesome-sphinxdoc


# Code Snippets

```
Adding a picture

.. image:: /_static/picture.png
   :width: 700px
   :align: center

.. end_tag

<h2>3 column time table</h2>

+-----------+------------+----------+
|      Time | Activity   | Notes    |
+===========+============+==========+
|  5-10 min | ...        | ...      |
+-----------+------------+----------+
| 10-15 min | ...        | ...      |
+-----------+------------+----------+
|    15 min | ...        | ...      |
+-----------+------------+----------+
|    40 min | ...        | ...      |
+-----------+------------+----------+
|    10 min | ...        | ...      |
+-----------+------------+----------+
```

# Helpful links for Sphinx and ReStructuredText

http://www.sphinx-doc.org/en/stable/rest.html

http://openalea.gforge.inria.fr/doc/openalea/doc/_build/html/source/sphinx/rest_syntax.html

http://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html

https://pythonhosted.org/an_example_pypi_project/sphinx.html

[epub FAQ](http://sphinx.readthedocs.io/en/latest/faq.html#epub-info)

[config.py epub options](http://www.sphinx-doc.org/en/stable/config.html#options-for-epub-output)

[Theming](http://www.sphinx-doc.org/en/stable/theming.html)

[Theming at tinkerer.me](http://tinkerer.me/doc/theming.html)

[Templating](http://www.sphinx-doc.org/en/stable/templating.html)

[ReStructured Text](http://docutils.sourceforge.net/rst.html)

[ReStructured Text Quick Reference](http://docutils.sourceforge.net/docs/user/rst/quickref.html)

[ReStructured Text Primer](http://docutils.sourceforge.net/docs/user/rst/quickstart.html)

# Check links

Make sure all of your links work with this command:

```make linkcheck```

# Troubleshooting

Problem: ```make latexpdf``` returns errors about python2.7 and normalize with Debian.

Solution: While making pdfs is experimental, I was able to remove this error by forcing python 3.

Remove all copies of sphinx with python 2.

```
sudo apt purge python-sphinx
sudo apt purge sphinx-doc
sudo pip uninstall sphinx
```

Install sphinx with python 3.

```sudo apt install python3-sphinx```

Change this line in ```Makefile```:

```SPHINXBUILD   = python3 -msphinx```

to this:

```SPHINXBUILD   = python3 -msphinx```
