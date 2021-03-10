########
Umbrella
########

**Umbrella** is a template preview library, that eases implementation and testing of templates.

Installation
############

.. code-block:: bash

    composer req 21torr/umbrella


Including Other Components
##########################

You can include other components in your component.

.. code-block:: twig
    :caption: atom/button.html.twig

    <button type="button" class="button {{ type ?? "" }}">{{ label ?? "My Button" }}</button>

and then use it in your other component:

.. code-block:: twig
    :caption: molecule/form.html.twig

    <form class="form">
        {# ... #}

        <div class="form-buttons">
            {{ umbrella("atom", "button", {label: "Submit form") }}
        </div>
    </form>


Variations
##########

Most of the time, you have some variables in your templates to modify the behaviour. You can then add a "variations"
template to have a quick look on all supported variations:

With this base component:

.. code-block:: twig
    :caption: atom/_button.html.twig

    <button type="button" class="button {{ type ?? "" }}">{{ label ?? "My Button" }}</button>

You can then render all your variations like this:

.. code-block:: twig
    :caption: atom/buttons.html.twig

    {{ umbrella_variations("atom", "_button", {
        type: ["", "is-primary", "is-muted"],
        label: [null, "Some special label"],
    }) }}

This will render every combination of every ``type`` combined with every ``label`` in this screen.

.. tip::

    It might be helpful to only have the variations template visible to the user of umbrella and hide the main
    ``button`` template. That's why it is prefixed with an ``_``.
