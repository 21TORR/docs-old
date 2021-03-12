#############
Feature Flags
#############

**Feature Flags** is a symfony bundle that integrates feature flags into your application.

Installation
############

.. code-block:: bash

    composer require 21torr/feature-flags


Defining Feature Flags
######################

In the root of your project, create a ``.features.yaml`` file and define your feature flags there:

.. code-block:: yaml

    feature: true
    some-other: false
    login: on
    something: off

You can use ``true``, ``false``, ``on`` and ``off`` as possible values.


Usage
#####

PHP / Symfony
=============

Fetch the ``FeatureFlags`` service:

.. code-block:: php

    <?php

    public function myAction (FeatureFlags $flags) : Response
    {
        if (!$flags->hasFeature("login"))
        {
            throw $this->createNotFoundException("Login disabled.");
        }

        return $this->render(...);
    }


Twig
====

In twig, use the ``has_feature()`` twig function:

.. code-block:: twig

    {%- if has_feature("login") -%}
        <a href="{{ path("login") }}">Login</a>
    {%- endif -%}

