###
CSS
###

These are guidelines on how to write (hopefully) modern and compatible CSS.

Atomic CSS Design
#################

All docs about the general structure are in its own article, under :doc:`./structure`.


Nesting
#######

You should not nest deeper than 4 levels in your SCSS code.

While your top level class name must be descriptive and unique, in your nested names you can shorten the
main name so that the meaning is still understandable.

Normally, you can achieve this by reusing a suffix of the parent class name:


.. code-block:: scss

    .contacts-list {

        .list-entry {
            .entry-title {
                // if it's important that it's nested
            }
        }

        .entry-title {
            // otherwise keep it here
        }
    }

Additionally, while you should wrap your component in a single global class, the nesting *inside* your
component should be as flat as possible.


Class Names
###########

You should always avoid styling HTML elements and instead use class names.

There are some exceptions, mainly in very simple cases or where the HTML tag is never used standalone.
Some exceptions include:

*   ``svg`` (always styled in the context of another component)
*   ``li`` (always styled in the context of a list)
*   all table subelements
*   ``.content a``


Headlines
=========

The convention of not styling HTML elements directly applies especially to headlines. It is crucial to **separate logical headline level of the visual headline level**, as they serve different purposes. The logical headline level is important for SEO and the general structure of your document, while the visual headline level is important for styling.

So define your logical headline level by using semantic elements:

.. code-block:: html

    <h1>...</h1>
    <!-- ... -->
    <h6>...</h6>

and define your visual headline level by classes:

.. code-block:: scss

    .h1 { /* ... */ }
    // ...
    .h6 { /* ... */ }

It makes perfect sense to mix different levels of visual and logical levels:

.. code-block:: html

    <h1 class="h1">...</h1>
    <h1 class="h2">...</h1>
    <h2 class="h1">...</h2>
    <h3 class="h1">...</h3>
    <div class="h2">...</div>


Modifier Classes
################

If your component can change its state (like "opened", "active", "disabled") you can use modifier classes.
These classes normally start with either ``is-`` or ``has-``.

.. code-block:: html

    <button class="button is-active"></button>

These classes are always tied to their component, so they are safe to reuse in the app:

.. code-block:: scss

    .button {
        // tie them to `.button`
        &.is-active {
        }
    }


Interaction States
##################

Always style all interaction states, that includes

*   ``:hover``
*   ``:focus``
*   ``:active``
*   sometimes you need a manual "is active" class, so in this case you should style ``.is-active`` as well.

You can use atlantis for that:

.. code-block:: scss

    .button {
        color: black;

        @include atlantis.on-interaction("is-active") {
            color: fuchsia;
        }
    }


Styling SVGs
############

When styling SVGs, you normally only need to change the ``fill`` and the ``stroke`` of some elements.
To ease the integration and make the code as minimal as possible, we only mark the elements with the class names which properties they need to change:

.. code-block:: xml

    <svg>
        <!-- change fill of the circle -->
        <circle class="_f" cx="50" cy="50" r="40"/>

        <!-- change stroke of the path -->
        <path class="_s" d="..."/>
    </svg>

And in your scss you can then use it like this:

.. code-block:: scss

    .my-element {
        &.is-active {
            @include atlantis.color-svg($highlight);
        }
    }

This will apply the given color to the correct properties of your elements.



File Structure
==============

Every ``atom``, ``molecule`` and ``organism`` file should only contain exactly one component, so normally a single
selector (with possibly some nested selectors).

Examples
--------

.. code-block:: scss

    // please don't do that
    .my-component {
        // ...
    }

    .some-other-thing {
        // ...
    }

This should be avoided. Split it into two separate files.

One exception from this rule is if the selectors are *logically* grouped to a single component and are just all top level
to avoid nesting (this should be reflected in the selector names):

.. code-block:: scss

    // this is okay, even if you should prefer having a single top level selector
    .accordion {
        // ...
    }

    .accordion-title {
        // ...
    }

.. tip::

    Having a single top level selector is in most cases a great idea.
    You should avoid over-optimizing for very short selectors. This one additional top level is great, rather focus on
    keeping the nesting to a minimum *inside* this top level selector.

The name should of the file should exactly match the top level selector.

Only example: for ``template`` s it is preferred, to have the project class name as prefix.

    *   ``template/__default.scss`` -> class name: ``.21torr``
    *   ``template/_blog.scss`` -> class name: ``.21torr-blog``
    *   ``template/_shop.scss`` -> class name: ``.21torr-shop``



Media Queries
#############

In most cases it is useful to build your SCSS mobile first, as normally you only add things to your styles, when going
from narrower to wider screens. It can make sense to have a single media query for special settings for only the phone version.

It is **heavily** recommended to add named media queries in your project:

.. code-block:: scss
    :caption: helper/_mixins.scss

    $tablet-width: 90rem;
    $desktop-width: 120rem;

    @mixin on-phone-only {
        @include atlantis.on-max-width($tablet-width - .1rem) {
            @content;
        }
    }

    @mixin on-tablet {
        @include atlantis.on-min-width($tablet-width) {
            @content;
        }
    }

    @mixin on-desktop {
        @include atlantis.on-min-width($desktop-width) {
            @content;
        }
    }

And then only use these named mixins in your app.

To motivate a clear structure and avoid surprising overrides, you should only have a single media query per size at the
end of your main component selector. It is also recommended to order the media queries by ascending screen width, starting
with the "phone only" version:


.. code-block:: scss
    :caption: molecule/_my-component.scss

    .my-component {
        // ...

        @include on-phone-only {
            // ...
        }

        @include on-tablet {
            // ...
        }

        @include on-desktop {
            // ...
        }
    }
