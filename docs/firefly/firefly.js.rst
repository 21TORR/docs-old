##########
firefly.js
##########

Firefly is configured by putting a ``firefly.js`` in the root of your project. This file imports the main ``Firefly`` class and must return a (configured) instance of it.

The base file can look like this:

.. code-block:: js

    const {Firefly} = require("@21torr/firefly");

    module.exports = (new Firefly())
        // configuration goes here
        ;

.. tip::

    You can generate the base file by just running

    .. code-block:: bash

        npx firefly init


The configuration of Firefly works by using the fluent methods on the configuration object, like this:

.. code-block:: js

    const {Firefly} = require("@21torr/firefly");

    module.exports = (new Firefly())
        .js({
            // ..
        })
        .scss({
            // ...
        })
        .disableFileNameHashing()
        // ...
        ;


Available configuration options
###############################

.. js:method:: .js(entries)

    Adds JS / TypeScript entries.

    :param entries: The entry files. Key is the name of the entry, value is the relative path to the file.
    :type entries:  Record<string, string>

    Example:

    .. code-block:: js

        .js({
            app: "asset/js/app.ts",
            backend: "asset/js/backend.js",
        })


.. js:method:: .scss(entries)

    Adds SCSS entries.

    :param entries: The entry files. Key is the name of the entry, value is the relative path to the file.
    :type entries:  Record<string, string>


.. js:method:: .outputTo(path)

    Sets the output path, where the compiled files will be stored.
    This is only the base path, the ``js/`` and ``scss/`` subdirectories will be created automatically.

    If you don't configure anything, files will be built to ``build/`` by default

    :param string path: The path where to store the built files.


.. js:method:: .withExternals(externals)

    :param externals: ?.
    :type externals:  Record<string, string>


.. js:method:: .compilePackages(...packages)

    Defines all package names, that should be compiled from ``node_modules``. Will be prefix-matched, so it can be a concrete package name or a organization name.

    :param packages: The names of the packages to compile.
    :type packages: string

    .. tip::

        Packages from the ``@21torr`` organization will be compiled by default.


.. js:method:: .disableFileNameHashing(s)

    Disables the hashing of the entry file names.
