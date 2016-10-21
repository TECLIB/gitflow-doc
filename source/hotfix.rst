Hotfix
======

.. warning::

   Be carefull your ``master`` branch is up-to-date before starting a hotfix, and both your ``master`` and ``develop`` branches are up-to-date before finishing it!

You will use `hotfix` to fix bugs against the latest stable release of the project, no matter it was a *major, a *minor* or another *patch*.

.. note::

   You can have **only one** hotfix at the same time!

Creation
--------

The name of the hotfix must be the release it will become. If the latest release was `1.3.2`; you'll want to create a `1.3.3` hotfix using:

.. code-block:: bash

   $ git flow hotfix start 1.3.3

This will automatically do the following:

1. create a new branch named ``hotfix/1.3.3`` from the ``master`` branch,
2. checkout the ``hotfix/1.3.3`` branch.

Lifetime
--------

Just like :doc:`features`, you will have nothing to do if there were no changes on the master branch since you've created your `hotfix`.

If something has changed in the master, that means another `hotfix` has already been done, which also means that the version you are using is probably incorrect now. In that case, you will have to:

* rename your `hotfix` branch,
* update the code

Assuming the `1.3.3` version has been released from another `hotfix`, you will work on the `1.3.4` version:

.. code-block:: bash

   (hotfix/1.3.3) $ git branch -m hotfix/1.3.4
   (hotfix/1.3.4) $ git rebase -i master

Pull Request
------------

Your `hotfix` has been finished, it must now be reviewed before being merged. Push last changes to your fork, go to your github fork page, select your branch and clik "New pull request" button.

You can provide aditionnal details if any, submit, and wait for another developer to review your changes! Once accepted, go back to your local copy, and see the paragraph below.

Finishing
---------

.. warning::

   Before running the commands to end your `hotfix`, make sure that:

   * your ``master`` branch is up-to-date
   * no other `hotfix` using the same version number has been merged (use ``git tag | sort -V``)

.. warning::

   You **have to use Git command line, and not Github facilities** to finish the hotfix!

Finishing a `hotfix` is as simple as:

.. code-block:: bash

   $ git flow hotfix finish 1.3.4

This will:

* Merge changes into the ``master`` branch,
* Create a ``1.3.4`` tag,
* Merge changes into the ``develop`` branch,
* Remove your local ``hotfix\1.3.4`` branch.

Once your `hotfix` has been finished; you'll have to push ``master``, ``develop`` and ``tags`` and also remove remote ``hotfix/1.3.4`` branch:

.. code-block:: bash

   (master)  $ git push
   (master)  $ git push --tags
   (master)  $ git checkout develop
   (develop) $ git push
             $ git push {github_username} :hotfix/1.3.4
