python-env-bootstrap
====================

A zero-dependency script skeleton for bootstrapping a developer's environment for onboarding to an existing Python project.

Designed to work with Python 3.8 or later, it handles the bootstrapping of the tooling and modules environment for developing
in a project without any dependencies except for Python's built-in libraries and network access.

.. note:: It **DOES NOT** setup a new project

  It is NOT for creating a new Python project - it is for onboarding a developer
  to an existing project.

It performs the setup of the *environment* for development of an existing project 
by first checking whether a developer's existing environment is already setup
with all the tools and PyPI modules needed to develop in the project.

If the environment is already setup appropriately, it does not change anything and just exits,
letting the developer know they are good to go.

If their environment *does not* meet the requirements for project development it
creates a virtual environment and performs the bootstrap installation of all required
tooling from PyPI.

It performs this installation to a virtual environment so as to prevent messing up the
developer's own local environment.


You use it by copying the `bootstrap.py <bootstrap.py>`_ standalone script
into your own project's repository and updating the `POST_INSTALL_MESSAGE` string,
the `TOOL_USAGE_INSTRUCTIONS` string, and the `BOOTSTRAP_MODULES` list
of `InstallSpec` instances to match your project's PyPI modules environment requirements.

It has no external dependencies except that it requires at least Python 3.8.


To setup an environment you just run

.. code-block:: shell

  python3 bootstrap.py


with the appropriate path to the script.


That's it. That's everything.

The copy of the script here is setup to install `tox <https://tox.wiki/en/latest/>`_ and `uv <https://docs.astral.sh/uv/>`_.

But you can literally use it to setup anything installable via pip. If you use it to install 'uv', it will bootstrap `uv` first and use to to install everything
else (highly recommended).


Why not just use pip -r requirements.txt?
-----------------------------------------

1. That may not work at all depending on a user's already existing environment. Depending on their system, the version of Python installed, 
   the version of pip on their system, pre-existing and possibly conflicting module requirements, it can easily fail. It is simple, but not very robust
   in the face of the diversity of systems that developers use. It can easily become a case of 'well, it works on *my* system...'
2. If it **DOES** work, it may mess up their existing local user or even system environment so that things other than your project now have problems.
3. It is simply cleaner to not 'dirty up' a developer's environment with every package from every project they've worked on ever used.
