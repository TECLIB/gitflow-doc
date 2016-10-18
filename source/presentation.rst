Presentation
============

`git-flow <http://nvie.com/posts/a-successful-git-branching-model/>`_ is a branching model, which come along with some documentation, and a git plugin to add command line facilities.

.. image:: _static/images/gitflow.png
   :scale: 25%

Keep in mind that it is just designed to get something standardized; all the background use standard git commands, you can achieve "manually" everything git-flow propose. It is just simplier to use, and it prevents to use the incorerect branch, or to forget about merging somewhere.

It is not the goal of the present documentation to list pros and cons of this model, we'll note that it is not designed to get long running support branches, it has been once something that would have been implmented; but it has not been done.

According to the semantic `versionning rules <http://semver.org>`_:

* you'll add features only for *major* or *minor* versions,
* you'll release *major* or *minor* versions,
* you'll hotfix *patch* versions.

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
