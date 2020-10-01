#######
Firefly
#######

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

