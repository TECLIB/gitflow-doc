Releases
========

.. warning::

   Be carefull your ``develop`` branch is up-to-date before starting a release, and both your ``master`` and ``develop`` branches are up-to-date before finishing it!

You will use the release feature to publish new *minor* or *major* versions, but not *patches*. It is designed to begin a new fresh release from the ``develop`` branch.

.. note::

   You can have several releases on a project; but honestly, I cannot find a use case where it should really be used. It's up to you ;)

Creation
--------

Just as :doc:`hotfixes <hotfix>`, the banch name must be the version it will become. Let's say we want to release a new *minor* ``1.4.0``:

.. code-block:: bash

   $ git flow release start 1.4.0

This will automatically do the following:

1. create a new branch named ``release/1.4.0`` from the ``develop`` branch,
2. checkout the ``release/1.4.0`` branch.

Lifetime
--------

.. warning::

   Until it's finished, you can still add new :doc:`hotfixes <hotfix>` or :doc:`features <features>` (anyways, if a new feature must reach your release, you've a planning issue ;)).

   But keep in mind **nothing will not reach your release branch until you do something!**.

Most of the time, your release branch should have a quite short lifetime; and changes should be very lite comparing your ``develop``. As an example, on several project I own (or I've owned); the `release` branch was created to update the changelog if any, add the release date, and eventually bump the version.

This kind of branch may be used for testing purposes also.

Sometimes, you can also just create a `release` to finish it immediately without doing any changes... :-)

If a new `hotfix` has been added, than you'll have to get it back to your release branch. To know how to proceed, you'll have to determine if something else has changed; because you probably do not want a feature finished after you decide to release to be backported.

.. note::

   Remember that you should always prefer to merge or cherry pick rather than report changes manually; that would cause conflicts while finishing.

In the simpliest case, nothing else has changed in your ``develop``, just update it and run:

.. code-block:: bash

   (release/1.4.0) $ git merge develop

If there were other changes, it may be a bit more complex. You can either ``cherry-pick`` the fix commit, or use advanced git possibiliies of ``merge`` command (such as merging a specific range of commits, for example); refer to the :ref:`Git documentation <gitdoc>`.

Pul request
-----------

If' you've just created the `release` to bump the version, it is not mandatory to open a pull request. On the other hand, if you've made fixes, you'll have to.

If you're on the second use case, push last changes to your fork, go to your github fork page, select your branch and clik "New pull request" button.

You can provide aditionnal details if any, submit, and wait for another developer to review your changes!

Once accepted, or if you do not need a PR, go back to your local copy, and see the paragraph below.

Finishing
---------

.. warning::

   Before running the commands to end your `release`, make sure that:

   * your ``master`` and ``develop`` branches are up-to-date
   * no other tag using the same version number has been created (use ``git tag | sort -V``)

.. warning::

   You **have to use Git command line, and not Github facilities** to finish the release!

Finishing a `release` is as simple as:

.. code-block:: bash

   $ git flow release finish 1.4.0

This will:

* Merge changes into the ``master`` branch,
* Create a ``1.4.0`` tag,
* Merge changes into the ``develop`` branch,
* Remove your local ``release\1.4.0`` branch.

Once your `release` has been finished; you'll have to push ``master``, ``develop`` and ``tags`` and also remove remote ``release/1.4.0`` branch (if any):

.. code-block:: bash

   (master)  $ git push
   (master)  $ git push --tags
   (master)  $ git checkout develop
   (develop) $ git push
             $ git push {github_username} :release/1.4.0
