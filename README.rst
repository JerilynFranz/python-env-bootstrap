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
   to an existing project quickly and easily.

Customization and Usage
-----------------------

You use it by copying the `bootstrap.py <bootstrap.py>`_ standalone script
into your own project's repository and updating the `POST_INSTALL_MESSAGE` string,
the `TOOL_USAGE_INSTRUCTIONS` string, and the `BOOTSTRAP_MODULES` list
of `InstallSpec` instances to match your project's PyPI modules environment
requirements.

It has no external dependencies except that it requires at least Python 3.8.

To setup an environment you just run

.. code-block:: shell

  python3 bootstrap.py

with the appropriate path to the script.

It has sensible defaults for virtual environment location,
module versions, and other settings but you can customize them
by modifying the constants at the top of the script.

It has the following command-line options:
- `-h, --help` : Show help message and exit.
- `--yes, -y` : Automatically confirm and proceed without prompting.
- `--debug` : Enable debug output.
- `--no-debug` : Disable debug output.
- `-q, --quiet` : Suppress non-error output.
- `-v, --verbose` : Enable verbose output (default).

That's it. That's everything.

The copy of the script here is configured to install `tox <https://tox.wiki/en/latest/>`_
and `uv <https://docs.astral.sh/uv/>`_ but you can easily use it to setup
anything installable via pip. 

.. note::

   If you use it to install ``uv``, it will bootstrap ``uv`` first and use it to
   install everything else much faster than ``pip`` does (highly recommended).

It does not try to be a build system or a project kickstarter. It does one thing
and does it pretty well: Get the environment for the developer up and running.
If you need additional things done such as running post-environment install actions,
they are easily added to it using the 'run_command' function so as to
keep the 'one-stop-setup' vibe.

Why not just use `pip -r requirements.txt`?
-------------------------------------------

This script is not trying to replace `pip` or `requirements.txt` files.
It is trying to complement them (not replace them) by providing
a zero-dependency, frictionless way to get a developer's environment
set up and ready to go with minimal effort.

It is designed to be a single script that you can run to get everything
set up without having to worry about whether `pip` is installed,
whether the right version of Python is being used, whether the virtual
environment is activated, whether the right platform-specific issues
are handled, installation order of dependencies, etc. It works
with requirements.txt files under the hood if you want to use them,
but it abstracts away all the common issues that come up when
setting up a Python development environment.

I like the 'run just one thing' approach to completely setup a developer's environment.

This script handles a lot of the common issues that come up when
setting up a Python development environment such as:

- Creating and managing a virtual environment automatically
- Handling platform differences (Windows vs Unix-like)
- Handling different Python versions
- Ensuring pip is up to date before installing anything
- Optionally using `uv <https://docs.astral.sh/uv/>`_ to speed up installations
- Providing clear and actionable error messages when things go wrong
- Customizable post-install messages and instructions
- Minimal dependencies (only requires Python 3.8+)
