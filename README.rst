======================
cookiecutter-pylibrary
======================

Cookiecutter_ template for a Python python library. 

*Notes*:

* This is largely designed to address this `blog post about packaging python 
  libraries <http://blog.ionelmc.ro/2014/05/25/python-packaging/>`_.
  
  * ... and it will save you from `packaging pitfalls 
    <http://blog.ionelmc.ro/2014/06/25/python-packaging-pitfalls/>`_.
* There's a bare library using this template (if you're curious about the final
  result): https://github.com/ionelmc/python-nameless.
* There's also a *minimal* version of this, see [1]_

Features
--------

This is an "all inclusive" sort of template.

* BSD 2-clause license.
* Tox_ and Pytest_ for testing Python 2.6, 2.7, 3.3, PyPy etc. [1]_
* Support for creating a tests matrix out of dependencies and python versions. [1]_
* Travis-CI_ and AppVeyor_ for continuous testing.
* Coveralls_ for coverage tracking (using Tox_).
* Documentation with Sphinx_, ready for ReadTheDocs_.
* Configurations for:

  * `isort <https://pypi.python.org/pypi/isort>`_
  * `bumpversion <https://pypi.python.org/pypi/bumpversion>`_

* Support for C extensions (including coverage measurement for the C code).
* Packaging and code quality checks. This template comes with a tox environment (``check``) that will:

  * Check if your ``README.rst`` is valid.
  * Check if the ``MANIFEST.in`` has any issues.
  * Run ``flake8`` (a combo of PEP8, pyflakes and McCabe checks)

Requirements
------------

Projects using this template have these minimal dependencies:

* Cookiecutter_ - just for creating the project
* Tox_ - for running the tests
* Setuptools_ - for building the package, wheels etc. Now-days Setuptools is widely available, it shouldn't pose a
  problem :)

To get quickly started on a new system, just `install setuptools
<https://pypi.python.org/pypi/setuptools#installation-instructions>`_ and then `install pip
<https://pip.pypa.io/en/latest/installing.html>`_. That's the bare minimum to required install Tox_ and Cookiecutter_. To install
them, just run this in your shell or command prompt::

  pip install tox cookiecutter

Usage
-----

This template is more involved than the regular `cookiecutter-pypackage
<https://github.com/audreyr/cookiecutter-pypackage>`_.

First generate your project::

  cookiecutter gh:CacconeLabYale/cookiecutter-pylibrary

You will be asked for these fields:

.. list-table::
    :stub-columns: 1

    * - project_name
      - Verbose project name, used in headings (docs, readme, etc).
    * - repo_name
      - Repository name on github.
    * - package_name
      - Python package name (whatever you would import).
    * - distribution_name
      - PyPI distribution name (what you would ``pip install``).

The testing (``tox.ini`` and ``.travis.yml``) configuration is generated from templates. For your convenience there's an
initial bootstrap ``tox.ini``, to get the initial generation going just run::

  tox

You can later regenerate ``tox.ini`` and ``.travis.yml`` by running::

  tox -e configure

After this you can create the initial repository (make sure you `create <https://github.com/new>`_ an *empty* Github
project)::

  git init .
  git add .
  git commit -m "Initial skel."
  git remote add origin git@github.com:ionelmc/python-nameless.git
  git push -u origin master

Then:

* `Enable the repository in your Travis CI account <https://travis-ci.org/profile>`_.
* `Enable the repository in your Coveralls account <https://coveralls.io/repos/new>`_.
* `Add the repo to your ReadTheDocs account <https://readthedocs.org/dashboard/import/>`_ + turn on the ReadTheDocs
  service hook. Don't forget to enable virtualenv and specify ``docs/requirements.txt`` as the requirements file in
  `Advanced Settings`.

Developing the project
``````````````````````

To run all the tests, just run::

  tox

To see all the tox environments::

  tox --listenvs

To only build the docs::

  tox -e docs

To build and verify that the built package is proper and other code QA checks::

  tox -e check

Releasing the project
``````````````````````

Before releasing your package on PyPI you should have all the tox environments passing.

To make a release of the project on PyPI, the most simple usage is::

  python setup.py release
 
(``release`` is aliased to ``register clean sdist bdist_wheel upload``, see ``setup.cfg``).

If you care about security you can do secure uploads to PyPI using `twine <https://pypi.python.org/pypi/twine>`_.

Questions & answers
-------------------

There's no Makefile?

  Sorry, no ``Makefile`` yet. The Tox_ environments stand for whatever you'd have in a ``Makefile``.

Not Exactly What You Want?
--------------------------

No way, this is the best. :stuck_out_tongue_winking_eye:

.. [1]

  In case you don't fancy having a test matrix generator script there's a `simpler variant of this template
  <https://github.com/ionelmc/cookiecutter-pylibrary-minimal>`_ that:

  * Doesn't have a generator script (no ``bootstrap.py``).
  * Doesn't use Pytest_. Just bare ``unittest``.

If you have criticism or suggestions please open up an Issue or Pull Request.

.. _Travis-CI: http://travis-ci.org/
.. _Tox: http://testrun.org/tox/
.. _Sphinx: http://sphinx-doc.org/
.. _Coveralls: https://coveralls.io/
.. _ReadTheDocs: https://readthedocs.org/
.. _Setuptools: https://pypi.python.org/pypi/setuptools
.. _Pytest: http://pytest.org/
.. _AppVeyor: http://www.appveyor.com/
.. _Cookiecutter: https://github.com/audreyr/cookiecutter
