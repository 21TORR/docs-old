#######
Library
#######

Usage
#####

Normally, you just import it in your ``helpers/_mixins.scss``:

.. code-block:: scss

    @forward "~@21torr/atlantis/mixins" as atlantis;

and your remaining application just uses your ``_mixins.scss`` then.


Mixins
######

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

.. code-block:: scss

    @include atlantis.center-children;

Centers all children. Sets ``display: flex`` with the centering settings on the element.



.. _atlantis/mixins/position/center-element:

``.center-element()``
=====================

.. code-block:: scss

    @include atlantis.center-element;

Centers the element in the parent. Sets ``position: absolute`` + transforms on the element.


.. _atlantis/mixins/position/fill-parent:

``.fill-parent()``
==================

.. code-block:: scss

    @include atlantis.fill-parent;

Positions (via ``position: absolute``) the element in the parent, so that it completely covers the parent.


.. _atlantis/mixins/position/flex-equal-columns:

``.flex-equal-columns()``
=========================

.. code-block:: scss

    @include atlantis.flex-equal-columns;

Will set sibling elements to flex-based equal columns.


.. _atlantis/mixins/position/flex-fill-height:

``.flex-fill-height()``
=======================

.. code-block:: scss

    @include atlantis.flex-fill-height;

Sets the element to automatically fill the remaining height. Should be used with ``flex-direction: column`` on the parent.


.. _atlantis/mixins/position/flex-fill-width:

``.flex-fill-width()``
======================

.. code-block:: scss

    @include atlantis.flex-fill-width;

Sets the element to automatically fill the remaining width.


.. _atlantis/mixins/position/flex-fixed-height:

``.flex-fixed-height()``
========================

.. code-block:: scss

    @include atlantis.flex-fixed-height($height);

Sets the element to a fixed flex height. It won't be resized in the flex context. Should be used with ``flex-direction: column`` on the parent.

Takes an optional ``$height`` to manually fixate the size. If you omit it, it will just keeps its inherent size.


.. _atlantis/mixins/position/flex-fixed-width:

``.flex-fixed-width()``
=======================

.. code-block:: scss

    @include atlantis.flex-fixed-width($width);

Sets the element to a fixed flex width. It won't be resized in the flex context.

Takes an optional ``$width`` to manually fixate the size. If you omit it, it will just keeps its inherent size.



Scroll
======

.. _atlantis/mixins/scroll/smooth-scroll:

``.smooth-scroll()``
====================

.. code-block:: scss

    @include atlantis.smooth-scroll;

Lets the element smooth scroll.

.. warning::

    Will also set ``overflow: scroll``, so you will always have scroll bars on desktop.



Size
====

.. _atlantis/mixins/size/aspect-ratio:

``.aspect-ratio()``
===================

.. code-block:: scss

    @include atlantis.aspect-ratio($width, $height);

Applies the aspect-ratio trick (with ``padding-bottom`` and ``height: 0``).

You should use it with just the aspect ratios:

.. code-block:: scss

    video {
        @include atlantis.aspect-ratio(16, 9);
    }



.. _atlantis/mixins/size/square:

``.square()``
=============

.. code-block:: scss

    @include atlantis.square($size);

Sets ``$width`` and ``$height`` to the same ``$size`` value.



SVG
===

.. _atlantis/mixins/svg/color-svg:

``.color-svg()``
================

.. code-block:: scss

    @include atlantis.color-svg($color);

Sets the SVG coloring. It will set the ``fill`` for any child class ``._f`` and the ``stroke`` for any child class ``._s``.


.. _atlantis/mixins/svg/svg-child:

``.svg-child()``
================

.. code-block:: scss

    @include atlantis.svg-child;

Applies ``display: block`` to any ``svg`` child and automatically stretches it to it's parent size.
Normally you want to use that for any svg and set the dimensions on the parent DOM element.



Transition
==========

.. _atlantis/mixins/transition/transition:

``.transition()``
=================

.. code-block:: scss

    @include atlantis.transition($properties, $duration: .15s, $easing: ease-in-out, $will-change: true);

Will automatically set ``will-change`` on the given properties and apply the transitions for all properties.

Normally, you can leave the default value of everything, to have consistent look and feel.

Usage:

.. code-block:: scss

    button {
        @include atlantis.transition(width height, .5s);
    }


Visibility
==========

.. _atlantis/mixins/visibility/hide-text:

``.hide-text()``
================

.. code-block:: scss

    @include atlantis.hide-text($absolute: false);

Will hide the text, so that it's invisible on normal page views, but readable for screen readers.

If, for some reason, the default behavior doesn't work, you can try to move the text by an ``vw`` value, by setting
``$absolute: true``.


.. _atlantis/mixins/visibility/text-overflow-ellipsis:

``.text-overflow-ellipsis()``
=============================

.. code-block:: scss

    @include atlantis.text-overflow-ellipsis;

Prevents wrapping of text by displaying ellipsis instead.


Functions
#########

SVG
===

.. _atlantis/functions/svg/inline-svg:

``.inline-svg()``
=================

.. code-block:: scss

    @include atlantis.inline-svg($svg);

Inlines the SVG on the element. Will return a ``url()`` element so it can be used directly as an image.

Usage:

.. code-block:: scss

    .element {
        background-image: atlantis.inline-svg('<svg...>...</svg>');
    }
