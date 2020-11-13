#############
CSS Structure
#############

We use **Atomic (CSS) Design** for structuring our SCSS.

*   Every file that is *not* supposed to be compiled as an entry, should start with a ``_`` prefix.
*   By convention, all entry files should be in the root of the main ``scss`` directory.
*   Normally, every project has exactly one entry file for frontend styling and optionally exactly one for backend styles.



Atomic CSS Design
#################

We use a more technical form of atomic design, that has clearer and stricter rules for how to structure your SCSS.

.. important::

    It's perfectly fine to mix two forms of "Atomic Design". You can have your (technical) atoms / molecules / organisms
    defined be the rules here, that then build your (logical) atoms / molecules / organisms.

    While it's great if both definitions perfectly overlap – they don't have to. But you must not adapt rules outside
    of these definitions here for structuring your SCSS, as it otherwise will lose its whole purpose.


*   Every component you build is by default an **atom**.
*   If your component uses other components (as nested selectors) it will always be the highest level of the nested
    components + 1. So for example:

    *   if your component uses no other (defined) component: it will be an atom
    *   if your component uses another atom, it will be a molecule
    *   if your component uses another molecule (and maybe some atoms), it will be an organism
    *   if your component uses another organism: you should restructure your code.

*   Using something from the ``base`` directory does not include the level.


Every component can be as large as it makes sense for you. You should avoid having an atom with several hundred lines of SCSS code and dozens of nested elements, but you also should not have every single class as a single atom. So try to find a good balance.

To come back to the "important" section above: most of the time it makes sense to structure the atoms the same way as your (conceptual / logical) atoms. The molecules are derived from the logic defined above (in contrast to the logical grouping), so it might divert here.



Never position yourself
#######################

To help with integrating different components, no element should position itself.

So don't use these on your top level element:

*   ``position: absolute/fixed``
*   ``position: relative`` + ``top/left/bottom/right``
*   ``transform`` (with positioning)
*   ``margin`` (see exceptions)

You may position nested elements:

.. code-block:: scss

    .list {
        // this is NOT ok (top level):
        margin-left: 3rem;

        .list-item {
            // this is ok (nested):
            margin-left: 3rem;
        }
    }


The only exception to this rule is if this element always needs to be centered. Then you can use ``margin: auto``, but
only on the sides that you actually need:

.. code-block:: scss

    .element {
        @include atlantis.center-horizontal;

        // or the long form:
        margin-left: auto;
        margin-right: auto;
    }

Positioning your top level elements should be done either by

*   elements of a higher order that is using them can position them (as then they are nested)
*   position them by composition (so another CSS class is responsible for positioning and not your main class)
*   the template scss file (most of the time the ``template/__default`` template).



Content
#######

CSS layout components separate into two main categories:

*   structure components
*   rich text / running text components

These two categories are styled completely differently, for example: a link in a running text will look completely
different from a link in the main navigation.

That's why it makes sense to separate the styling of the two. The main layout (+ its reset) will reset all styling
to look neutral, so that it is the easiest, to style structure components, as these will make up most of your application.

For content, we just use a global ``.content`` marker class. This class styles the content according to the "running
text styling" rules. It should mainly style its direct children + some more special cases.

Avoid styling too freely, so that complex things like tables don't break.

To avoid side effects, the ``content`` class should always be applied as deep (in the DOM tree) as possible. That's
why it's really important that it's a *marker class*.

.. hint::

    It needs to be a **marker** class, that means that it only styles the content and is never styled itself.
    This is really important, so that the class can be applied freely throughout the application.

The main styling is covered by just using the atlantis mixin:

.. code-block:: scss
    :caption: ``base/_content.scss``:

    @use "../helper/mixins";

    .content {
        @include atlantis.content(2rem);
    }



Template
########

Templates handle the global positioning of elements. Normally, these are mainly all fixed elements (modals, overlays,
the main page container).
Also all global ``z-index`` handling is done here, to unify it and avoid z-fighting issues.

In nearly all projects you will only need the ``template/__default.scss`` template. Every template should be triggered by a
``body`` class. The default template can just use the project name as class name, so for example:

.. code-block:: scss
    :caption: ``template/__default.scss``:

    .21torr {
        .modal {
            position: fixed;
            // ...
        }

        // ...
    }

.. tip::

    It's important to only apply these global positioning definitions if the body class is set, so that layout preview
    systems don't break when trying to preview an e.g. fixed positioned element.


Entry Files
###########

Most of your code is structure by the `Atomic CSS Design` rules above, but here is the main file:

.. code-block:: scss

    // Vendor
    @use "~@21torr/atlantis/reset";

    // Base
    @use "base/content";
    @use "base/fonts";
    @use "base/global";
    @use "base/icon";
    @use "base/placeholder";

    // Atoms
    @use "atom/...";
    // ...

    // Molecules
    @use "molecule/...";
    // ...

    // Organisms
    @use "molecule/...";
    // ...

    // Templates
    @use "template/_default";
    // ...


.. tip::

    You should sort all individual imports alphabetically. These are by definition independent of each other (otherwise
    they would not be in the same section) and sorting them keeps everything tidy and easy to work with.


Directory Layout
################

See the article for :ref:`code style / directory layouts <scss-directory-layout>`.
