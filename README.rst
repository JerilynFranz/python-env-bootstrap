python-env-bootstrap
====================

A zero-dependency script skeleton for robustly bootstrapping a developer's
environment for onboarding to an existing Python project.

Who is this for?
-------------------
This is for Python project maintainers who want to make it as easy as possible
for new developers to get their development environment setup and ready to go
with as little friction as possible.

Overview
--------
Designed to work with Python 3.8 or later, it handles the bootstrapping of
the tooling and modules environment for developing in a project without any
dependencies except for Python's built-in libraries and network access.

It automatically creates a virtual environment and installs
all required PyPI modules into that virtual environment while handling
common issues such as platform, Python version, and pip version differences.

.. note:: It **DOES NOT** setup a new project

  It is NOT for creating a new Python project - it is just for onboarding a developer
  to an existing project.

If the environment is already setup appropriately, it does not change anything
and just exits, letting the developer know they are good to go.

If their environment *does not* meet the requirements for project development it
creates a virtual environment and performs the bootstrap installation of all required
tooling from PyPI.

It performs this installation to a virtual environment so as to prevent messing up the
developer's own local environment.


Customization and Usage
-----------------------

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

The copy of the script here is configured to install `tox <https://tox.wiki/en/latest/>`_
and `uv <https://docs.astral.sh/uv/>`_.

But you can use it to setup anything installable via pip. 

.. note:

If you use it to install 'uv', it will bootstrap `uv` first and use it to install everything
else much faster than pip does (highly recommended).

It does not try to be a build system or a project kickstarter. It does one thing
and does it pretty well: Get the environment for the developer up and running.
If you need additional things done such as running post-environment install actions,
they are easily added to it using the 'run_command' function so as to
keep the 'one-stop-setup' vibe.

Why not just use `pip -r requirements.txt`?
-------------------------------------------

In some degree it is just a matter of taste.

I like the 'run just one thing' to completely setup an environment approach.

Using requirements.txt takes running *at least* three things to do it
safely and reliably (creating a virtual environment, activating the virtual
environment, then runnning pip -r requirements.txt) and
possibly more steps depending on the complexity of the environment. 

And it takes work to make the instructions and/or scripts for doing that
robust across different OS platforms, system constraints, and python versions.

So why not make it *one* step that does it all efficiently without making anyone
think much about what is happening 'under the hood' to get there?

But if you don't see it as a big thing, that's cool too :)
