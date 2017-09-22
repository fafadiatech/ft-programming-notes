# Notes on Shphinx {Documentation Generator}

## Notes from [walkthrough](https://www.youtube.com/watch?v=LQ6pFgQXQ0Q)
1. `.rst` is formatting structure for documentation itself
1. `make html` will generate output in `_build/html`
1. To add new page update `toctree` section within `index.rst` , make sure respective `.rst` file exists
1. Put `=` below main title of you documentation. This is what is used for heading
1. Add a section below `-` section heading
1. [automodule](http://www.sphinx-doc.org/en/stable/ext/autodoc.html) help auto generate documentation for you. This also picks up any document string that you're written

## References

1. [All in one Official Reference](https://pythonhosted.org/an_example_pypi_project/sphinx.html)
1. [rST Cheatsheet](http://github.com/ralsina/rst-cheatsheet/raw/master/rst-cheatsheet.pdf)
1. [Python Docstring conventions](https://www.python.org/dev/peps/pep-0257/)