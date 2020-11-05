######
Mixins
######

Mixins

Usage
#####

Normally, you just import it in your ``helpers/_mixins.scss``:

.. code-block:: scss

    @forward "~@21torr/atlantis/mixins" as atlantis;


Library
#######

Container
=========

.. _atlantis/mixins/container/centered-container:

``.centered-container()``
=========================

.. code-block:: scss

    @include atlantis.centered-container($max-width, $min-margin);

Renders a centered container. The container will always have a horizontal margin of ``$min-margin`` to the browser edge, but will at most be ``$max-width`` wide. It will be horizontally centered.



Font
====

.. _atlantis/mixins/font/emoji-fonts:

``.emoji-fonts()``
==================

.. code-block:: scss

    @include atlantis.emoji-fonts('Some Font', Georgia);

Renders a ``font-family`` declaration and automatically appends all required fonts to support emojis.


.. _atlantis/mixins/font/system-fonts:

``.system-fonts()``
===================

.. code-block:: scss

    @include atlantis.system-fonts('Some Font', Georgia);

Renders a ``font-family`` declaration and automatically appends all fallback fonts (including to support emojis).



Interaction
===========

.. _atlantis/mixins/interaction/on-interaction:

``.on-interaction()``
=====================

.. code-block:: scss

    @include atlantis.on-interaction($active-class: null) { @content }

Applies the ``@content`` if the user interacts with the element (``active``, ``hover``, ``focus``).
You can pass an additional ``$active-class``, if you manually want to generate an "active" class as well.

Usage:

.. code-block:: scss

    a {
        color: red;

        @include atlantis.on-interaction("is-active") {
            color: blue;
        }
    }



Media Query
===========

Ideally, you should always wrap these mixins into your own, custom and named mixins like

*   ``on-phone-only()`` (for width <= phone)
*   ``on-tablet()`` (for width >= tablet)
*   ``on-desktop()`` (for width >= desktop)


.. _atlantis/mixins/media-query/on-max-height:

``.on-max-height()``
====================

.. code-block:: scss

    @include atlantis.on-max-height($height) { @content }

Media query for content that should apply if the browser height ``<= $height``.

Supports ``rem`` and ``px`` values.


.. _atlantis/mixins/media-query/on-max-width:

``.on-max-width()``
===================

.. code-block:: scss

    @include atlantis.on-max-width($width) { @content }

Media query for content that should apply if the browser width ``<= $width``.

Supports ``rem`` and ``px`` values.


.. _atlantis/mixins/media-query/on-min-height:

``.on-min-height()``
====================

.. code-block:: scss

    @include atlantis.on-min-height($height) { @content }

Media query for content that should apply if the browser height ``>= $height``.

Supports ``rem`` and ``px`` values.


.. _atlantis/mixins/media-query/on-min-width:

``.on-min-width()``
===================

.. code-block:: scss

    @include atlantis.on-min-width($width) { @content }

Media query for content that should apply if the browser width ``>= $width``.

Supports ``rem`` and ``px`` values.



Position
========

.. _atlantis/mixins/position/center-children:

``.center-children()``
======================


.. _atlantis/mixins/position/center-element:

``.center-element()``
=====================


.. _atlantis/mixins/position/fill-parent:

``.fill-parent()``
==================


.. _atlantis/mixins/position/flex-equal-columns:

``.flex-equal-columns()``
=========================


.. _atlantis/mixins/position/flex-fill-height:

``.flex-fill-height()``
=======================


.. _atlantis/mixins/position/flex-fill-width:

``.flex-fill-width()``
======================


.. _atlantis/mixins/position/flex-fixed-height:

``.flex-fixed-height()``
========================


.. _atlantis/mixins/position/flex-fixed-width:

``.flex-fixed-width()``
=======================



Scroll
======

.. _atlantis/mixins/scroll/smooth-scroll:

``.smooth-scroll()``
====================



Size
====

.. _atlantis/mixins/size/aspect-ratio:

``.aspect-ratio()``
===================


.. _atlantis/mixins/size/square:

``.square()``
=============



SVG
===

.. _atlantis/mixins/svg/color-svg:

``.color-svg()``
================


.. _atlantis/mixins/svg/svg-child:

``.svg-child()``
================


.. _atlantis/mixins/svg/inline-svg:

``.inline-svg()``
=================



Transition
==========

.. _atlantis/mixins/transition/transition:

``.transition()``
=================



Visibility
==========

.. _atlantis/mixins/visibility/hide-text:

``.hide-text()``
================


.. _atlantis/mixins/visibility/text-overflow-ellipsis:

``.text-overflow-ellipsis()``
=============================


