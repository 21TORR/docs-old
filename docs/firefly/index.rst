
#######
Firefly
#######

.. image:: https://images.unsplash.com/photo-1584852498908-85e3e7bb303a?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=crop&w=2250&q=80
    :alt: An image of a spaceship


**Firefly** is the (frontend) build system for assets. It has support for

*   building TypeScript / JavaScript
*   building SCSS
*   building JSX (in Preact)
*   linting via Stylelint and ESLint

and unifies the workflow and linting rules across all our projects.

Installation
############

Install Firefly locally in your project:

.. code-block:: bash

    pnpm i -D @21torr/firefly

You can now either call it directly via

.. code-block:: bash

    pnpx firefly
    ./node_modules/.bin/firefly

or use it in scripts in your ``package.json``.


CLI
###

Firefly is a CLI tool.
All builds will include sourcemaps.

.. code-block:: bash

    pnpx firefly [command]

You can add the option ``--verbose`` option to any command, to show verbose
errors from the builder itself (build errors will always be verbose).

Here is an overview of all supported commands:


``build``
=========

.. code-block:: bash

    pnpx firefly

Builds a debug build, including source maps and automatically fixing code style issues.

.. tip::

    This is the default command, so you can omit the ``build`` from the call:

    .. code-block:: bash

        pnpx firefly


``dev``
=======

Builds a debug build and starts watcher that will continuously build debug
builds as soon as a file changed.

.. tip::

    Hit :kbd:`Strg+C` to exit the watcher.


``ci``
======

Builds a debug build (without starting a watcher), but won't run any fixers.
The return code can be used in the CI to fail the build.

Use this in the CI.


``release``
===========

.. code-block:: bash

    pnpx firefly release

Will build a production release. It will include source maps, minify all code, but won't lint or fix the code.

Use this on the production / staging server.

