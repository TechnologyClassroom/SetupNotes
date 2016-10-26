# sphinx-doc
sphinx-doc is a way to write ebooks, documentation, or websites once and export to your desired output.  Exported formats include epub, html, pdf, etc.

# Markup Syntax
http://www.sphinx-doc.org/en/stable/rest.html

http://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html

https://pythonhosted.org/an_example_pypi_project/sphinx.html

# Templates

Themes are located in the /usr/share/sphinx/themes/ folder.

The default theme can be found in the /usr/share/sphinx/themes/basic folder.

http://www.sphinx-doc.org/en/1.4.8/templating.html

Adding creative commons
TP from https://groups.google.com/forum/#!topic/sphinx-users/f3Yl45l1KYg suggests overwriting the footer with a template:

CC BY 3.0 US
```
    {%- block footer %}
      <div class="footer">
       <span class="creativecommons">
        <a href="http://creativecommons.org/licenses/by/3.0/us/" >
          <img src="{{ pathto("_static/creativecommons-88x31.png", 1) }}"
               border="0" alt="Creative Commons License"/>
         </a>
        Whatever is licensed under a
        <a href="http://creativecommons.org/licenses/by/3.0/us/">
         Creative Commons Attribution 3.0 United States License.
        </a>
       </span>
      </div>
    {%- endblock %}
```

CC BY-SA 4.0 INTL
```
    {%- block footer %}
      <div class="footer">
       <span class="creativecommons">
        <a href="https://creativecommons.org/licenses/by-sa/4.0/" >
          <img src="{{ pathto(".static/ccby-sa4.0intl88x31.png", 1) }}"
               border="0" alt="Creative Commons License"/>
         </a>
        This work is licensed under a 
        <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">
         Creative Commons Attribution-ShareAlike 4.0 International License
        </a>
       </span>
      </div>
    {%- endblock %}
```



# Examples
http://www.sphinx-doc.org/en/stable/tutorial.html

https://github.com/sphinx-doc/sphinx/blob/master/EXAMPLES

Front: https://docs.chef.io/index.html Back: https://github.com/chef/chef-web-docs/tree/master/chef_master/source

https://github.com/yoloseem/awesome-sphinxdoc


# Code Snippets

<h2>Picture</h2>

.. image:: ../../images/Picture1.svg
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

