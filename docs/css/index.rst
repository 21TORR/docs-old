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
        color: $text;

        @include atlantis.on-interaction("is-active") {
            color: $highlight;
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
