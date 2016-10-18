Features
========

.. warning::

   Be carefull your ``develop`` branch is up-to-date before starting or finishing a feature! Even if you can quite easily fix that ;)

This possibility will be used to implement new features in the project. Features are designed to be created from the ``develop`` branch, and reintegrated in the ``develop`` branch as well.

.. note::

   You can have as many features as you want on a project; you'll see at usage than working with too many features can be a kind of nightmare; as well as long running ones ;)

Creation
--------

The name of the feature is up to you, choose something simple and short, describing what you are doing. To start a feature named `my-great-feature` you'll use:

.. code-block:: bash

   $ git flow feature start my-great-feature

This will automatically do the following:

1. create a new branch named ``feature/my-great-feature`` from the ``develop`` branch,
2. checkout the ``feature/my-great-feature`` branch.

So, yes, you're ready to go! Just hack, commit, push, ... You're on a branch, you can do what you want (well... almost!).

As stated in :ref:`working_with_github`, you will use your fork to push new branches. You'll achieve that running:

.. code-block:: bash

   (feature/my-great-feature) $ git push -u {github_username} feature/my-great-feature

Lifetime
--------

Sometimes, nothing happened on the ``develop`` branch until you finish your feature, and you'll have nothing to take care of.

But sometimes, some other features have been added, or some bugs have been fixed... You'll have to keep you feature branch up-to-date. Considering your ``develop`` branch has been updated (you always keep your ``develop`` updated, don't you? :p):

.. code-block:: bash

   (feature/my-great-feature) $ git flow feature rebase

This will rebase you feature branch on top of the develop; it sounds just like you've just created your feature right now and it applies your commit one by one on the top. Explaining rebasing is out of the scope of the current documentation, but you'll find many resources on it.

Pull Request
------------

Your feature has been finished, it must now be reviewed before being merged. Push last changes to your fork, go to your github fork page, select your branch and clik "New pull request" button.

You can provide aditionnal details if any, submit, and wait for another developer to review your changes! Once accepted, go back to your local copy, and see the paragraph below.

Finishing
---------

Once you're done, and your PR has been accepted, you can clean up a bit your branch history, squashing your commits to prevent keeping commit messages like "oops, I did it again!". Assuming your working copy is on the feature branch, you'll then run:

.. code-block:: bash

   (feature/my-great-feature) $ git flow feature finish

This will do the following:

1. merge branch ``feature/my-great-feature`` into ``develop``,
2. ask you for a commit message (default will be "Merge branch 'feature/my-great-feature' into develop")
3. delete branch ``feature/my-great-feature``

For the the second step, you can just save the message as it; if you've squashed your commits, you can remove the merge commit simply using:

.. code-block:: bash

   (develop) $ git rebase -i

Or not, it's up to you :)

You're done, the `my-great-feature` has reached ``develop`` and will be part of the next release!
