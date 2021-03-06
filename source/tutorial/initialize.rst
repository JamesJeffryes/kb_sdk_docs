Initialize the App
====================

The KBase SDK provides a way to quickly bootstrap a new module by generating most of the required components.

The basic options of the command are:

.. code-block:: bash

    $ kb-sdk init [--example] [--verbose] [--language language] [--user username] ModuleName


where ``ModuleName`` must be unique across all SDK modules registered in KBase. For example:


.. code-block:: bash

    $ kb-sdk init --language python --user <your_kbase_user_name> <user_name>ContigFilter


We're using ``<user_name>`` in the module name in this example to make sure that your module has a unique name. However, you would not usually put your own username in the module name, and instead name it something like ``ContigFilter``.

You must always include the ``-u`` option with your username to set yourself as the module owner.

You can set your programming langauge to any of Python, Perl, or Java; for this tutorial, we're using Python.

The ``kb-sdk init`` options are:

.. code::

    -v, --verbose    Show verbose output about which files and directories
                     are being created.
    -u  --user       Set the KBase username of the first module owner
    -e, --example    Populate your repo with an example module in the language
                     set by -l
    -l, --language   Choose a programming language to base your repo on.
                     Currently, we support Perl, Python, and Java. Default is
                     Python


The example we're building will have the same functionality as the app you get when you run ``kbase-init --example ..``. You can reference https://github.com/msneddon/ContigFilter for a working version if you get stuck at any point.

Run the above init script before continuing.

Build the App
---------------------

.. code-block:: bash

    $ cd <user_name>ContigFilter
    $ make


The ``make`` command will run some initial code generation.

Create a Git Repo
---------------------

You will need to publish your code to a public git repository to make it available for building into a custom Docker Image.  Here we'll show a brief example using GitHub.  First, commit your codebase into a local git repository. Then, ``git add`` all files created by kb-sdk and commit. This creates a git repository locally.

.. code:: bash

    $ cd MyModule
    $ git init
    $ git add .
    $ git commit -m 'Initial commit'


Now, create a new GitHub repository on github.com (it can be in your personal GitHub account or in an organization, but it must be public). Make sure your github repository is initially empty (don't add an initial README.md).

* Direct link to create a repo on github https://github.com/new
* Github documentation about creating repos: https://help.github.com/articles/creating-a-new-repository

Sync your local codebase to your repository on github:

.. code:: bash

    $ git remote add origin https://github.com/[GITHUB_USER_OR_ORG_NAME]/[GITHUB_MODULE_NAME].git
    $ git push -u origin master


Remember to continuously push your code changes to your github repo by using ``git push``.
