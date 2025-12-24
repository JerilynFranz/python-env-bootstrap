python-env-bootstrap
====================

A zero-dependency script skeleton for bootstrapping a developer's environment for onboarding to an existing Python project.

Designed to work with Python 3.8 or later, it handles the bootstrapping of the tooling and modules environment for developing
in a project without any dependences except for Python's native libraries and network access.

.. note:: It **DOES NOT** setup a new project

  It is NOT for creating a new Python project - it is for onboarding a developer
  to an existing project.

It performs the setup of the *environment* for development of an existing project 
by first checking whether a developer's existing environment is already setup
with all the tools and PyPI modules needed to develop in the project.

If the environemtnt is already setup appropriately, it does not change anything and just exits.

If their environment *does not* meet the requirements for project development it
creates a virtual environment and performs the bootstrap installation of all required
tooling from PyPI.

It performs this installation to a virtual environment so as to prevent messing up the
developer's own environment.

That's it. That's what it does.
