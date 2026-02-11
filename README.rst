oslo-pkg-resources
==================

Standalone redistribution of ``pkg_resources``, which was removed from
``setuptools`` in v82.0.0.

This package provides the ``pkg_resources`` module exactly as it existed
in ``setuptools`` v81.0.0, allowing projects that depend on it to
continue functioning.

Installation
------------

.. code-block:: bash

    pip install oslo-pkg-resources

Usage
-----

.. code-block:: python

    import pkg_resources

    # Use pkg_resources as before
    dist = pkg_resources.get_distribution("my-package")
    print(dist.version)

Deprecation Notice
------------------

``pkg_resources`` is deprecated. Consider migrating to:

- `importlib.resources <https://docs.python.org/3/library/importlib.resources.html>`_ for resource access
- `importlib.metadata <https://docs.python.org/3/library/importlib.metadata.html>`_ for distribution metadata
- `packaging <https://pypi.org/project/packaging/>`_ for version and requirement parsing

This package exists as a bridge to allow projects time to migrate away
from ``pkg_resources``.

License
-------

MIT License. See ``LICENSE`` for details.

This package is derived from `setuptools <https://github.com/pypa/setuptools>`_
by the Python Packaging Authority.
