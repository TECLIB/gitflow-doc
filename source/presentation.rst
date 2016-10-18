Presentation
============

`git-flow <http://nvie.com/posts/a-successful-git-branching-model/>`_ is a branching model, which come along with some documentation, and a git plugin to add command line facilities.

.. image:: _static/images/gitflow.png
   :scale: 25%

Keep in mind that it is just designed to get something standardized; all the background use standard git commands, you can achieve "manually" everything git-flow propose. It is just simplier to use, and it prevents to use the incorect branch, or to forget about merging somewhere.

It is not the goal of the present documentation to list pros and cons of this model, we'll note that it is not designed to get long running support branches, it has been once something that would have been implemented; but it has not been done.

According to the semantic `versionning rules <http://semver.org>`_:

* you'll add ``features`` only for *major* or *minor* versions,
* you'll ``release`` *major* or *minor* versions,
* you'll ``hotfix`` *patch* versions.

Conventions
-----------

The present documentation assumes that:

* a ``$`` sign will precede each command line instructions,
* any term beetween ``()`` before the ``$`` sign is the name of the current branch,
* all is driven from the command line (I do not use any git GUI anyways).

Pre-requisites
--------------

In order the get the commands available; you'll have to install the `git-flow git plugin <https://github.com/nvie/gitflow>`_.

Most of Linux distributions have it in their repositories (so ``yum install git-flow`` or ``apt-get install git-flow`` would do the trick) or you can follow the `installation instructions <https://github.com/nvie/gitflow/wiki/Installation>`_ provided on the project wiki.

Many GIT software are aware of gitflow, or can be if you install a simple plugin; check their respective documentation.

If you use command line, there are numerous ways to get usefull informations displayed in your prompt. While this is not a pre-requisite, it can help you save time!

.. figure:: _static/images/zsh-git-prompt.png
   :scale: 70%
   :align: center

   As an example, the ZSH git prompt I use

.. _working_with_github:

Working with Github
-------------------

Each project will have a main repository hosted on Github. Even if you are part of the core developers, you will use the main repository only to push changes on the ``develop`` and ``master`` branches. All other branches will be created on a fork (use the eponym button at the top of the project - see below) you will create on your account.

.. figure:: /_static/images/fork_button.png
   :scale: 50%
   :align: center

   The fork button

.. figure:: /_static/images/forked.png
   :scale: 50%
   :align: center

   The forked repo on my personnal account

From the main repository you've cloned the project to, add a new remote, let's say naming as your github username (name does not matter, just remember what you choose, and stay consistent accross projects). Replacing ``{github_username}`` with your own username, run the following:

.. code-block:: bash

   $ git remote add {github_username} git@github.com:{github_username}/mreporting.git

All branchs you will create that must be reviewed will be pushed to your fork.

Initialization
--------------

Initializing git-flow is quite simple, just clone the repository, go to the ``master`` branch and run:

.. note::

   When you clone a git repository, the default branch will be checkout. In most cases, it will be ``master``, but double check.

.. code-block:: bash

   (master) $ git flow init

You can assume the default answer is correct for all questions. If the ``develop`` branch already exists, it will be used, the process will create it otherwise.
