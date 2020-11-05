########
Atlantis
########

**Atlantis** is a library, that combines a lot of commonly used patterns in SCSS.


Reset
#####

Atlantis bundles a reset, that resets the browser default styles

*   Removes all padding and margin
*   Applies ``box-sizing: border-box`` to everything.
*   Resets all list styling (it should be reapplied in your ``.content``)
*   Unifies SVG styling across the app.
*   Unifies form element styling
*   Improves global text styling


Usage:

.. code-block:: scss

    @use "~@21torr/atlantis/reset";

This import belongs in your SCSS entry file.


Mixins
######

All available mixins:

*   :ref:`aspect-ratio() <atlantis/mixins/size/aspect-ratio>`
*   :ref:`center-children() <atlantis/mixins/position/center-children>`
*   :ref:`center-element() <atlantis/mixins/position/center-element>`
*   :ref:`centered-container() <atlantis/mixins/container/centered-container>`
*   :ref:`color-svg() <atlantis/mixins/svg/color-svg>`
*   :ref:`emoji-fonts() <atlantis/mixins/font/emoji-fonts>`
*   :ref:`fill-parent() <atlantis/mixins/position/fill-parent>`
*   :ref:`flex-equal-columns() <atlantis/mixins/position/flex-equal-columns>`
*   :ref:`flex-fill-height() <atlantis/mixins/position/flex-fill-height>`
*   :ref:`flex-fill-width() <atlantis/mixins/position/flex-fill-width>`
*   :ref:`flex-fixed-height() <atlantis/mixins/position/flex-fixed-height>`
*   :ref:`flex-fixed-width() <atlantis/mixins/position/flex-fixed-width>`
*   :ref:`hide-text() <atlantis/mixins/visibility/hide-text>`
*   :ref:`on-interaction() <atlantis/mixins/interaction/on-interaction>`
*   :ref:`on-interaction() <atlantis/mixins/interaction/on-interaction>`
*   :ref:`on-max-height() <atlantis/mixins/media-query/on-max-height>`
*   :ref:`on-max-width() <atlantis/mixins/media-query/on-max-width>`
*   :ref:`on-min-height() <atlantis/mixins/media-query/on-min-height>`
*   :ref:`on-min-width() <atlantis/mixins/media-query/on-min-width>`
*   :ref:`smooth-scroll() <atlantis/mixins/scroll/smooth-scroll>`
*   :ref:`square() <atlantis/mixins/size/square>`
*   :ref:`svg-child() <atlantis/mixins/svg/svg-child>`
*   :ref:`system-fonts() <atlantis/mixins/font/system-fonts>`
*   :ref:`text-overflow-ellipsis() <atlantis/mixins/visibility/text-overflow-ellipsis>`
*   :ref:`transition() <atlantis/mixins/transition/transition>`


Functions
#########

All available functions:

*   :ref:`inline-svg() <atlantis/functions/svg/inline-svg>`
