##########
Code Style
##########


Directory Layout
################

Assets
======

.. code-block::

    .
    ├── assets/
    │  ├── js
    │  └── scss
    ├── build/
    │  ├── css
    │  ├── font
    │  ├── icon
    │  ├── img
    │  ├── js
    │  └── vendor
    └── ...

*   Put all your assets that are only required for the (firefly) build in ``assets``.
*   Put all ready-to-use assets in ``build``, that includes
    *   Build output for firefly (``build/css`` and ``build/js``)
    *   minified images / icons
    *   font files


Symfony Projects
================

.. code-block::

    .
    ├── assets/
    ├── bin/
    ├── build/
    ├── config/
    ├── node_modules/
    ├── public/
    ├── src/
    ├── templates/
    ├── tests/
    ├── var/
    │  ├── cache/
    │  ├── logs/
    │  ├── sessions/
    │  └── storage/
    ├── vendor/
    └── ...

*   ``assets`` / ``build`` same as in `Assets`
*   Keep using the default symfony directories
*   Put all publicly available files in ``public``
*   Put all non-publicly available files in ``var/storage``



.. _scss-directory-layout:

SCSS
####

.. code-block::

    scss/
    ├── atom/
    ├── base/
    │  ├── _content.scss
    │  ├── _fonts.scss
    │  ├── _global.scss
    │  ├── _icon.scss
    │  └── _placeholder.scss
    ├── helper/
    │  ├── _mixins.scss
    │  └── _variables.scss
    ├── molecule/
    ├── organism/
    ├── template/
    │  ├── __default.scss
    │  └── ...


*   Most of the time you don't need more than the ``template/__default`` template.



Project Directory Layout
########################

Put all your assets in ``assets/`` and all
