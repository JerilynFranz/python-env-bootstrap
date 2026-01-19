=========
Changelog
=========

1.3.0-rc1- Misc improvements and fixes (2026-01-18)
===================================================
- Updated documentation in `README.rst` and `docs_source/index.rst` to clarify the purpose
  and usage of the `python-env-bootstrap` tool.
- Fixed an issue in `scripts/bootstrap-38.py` where the virtual environment
  directory names were inconsistent, ensuring both `VENV_DIR` and `ACTIVATED_VENV_DIR`
  are set to `.venv` for clarity.
- Ensured that both `scripts/bootstrap-310.py` and `scripts/bootstrap-38.py`
  include a call to `uv sync` after installing the project in editable mode
  to synchronize dependencies.
- Fixed various minor bugs and improved error handling in both bootstrap scripts
  to enhance robustness during the bootstrapping process.
- Fixed various linting and typing issues in the bootstrap scripts to improve code quality.

1.2.0-beta - Fixed defaults around removal of bootstrap virtual environment (2025-12-29)
========================================================================================
- Changed default value of `REMOVE_BOOTSTRAP_VENV_ON_EXIT` to `False`
  in `bootstrap-310.py` script to prevent accidental deletion of the created
  virtual environment after bootstrapping.
- Added support for installing git and hg hooks in the bootstrapped environment
  to facilitate better version control integration.

1.1.0-beta - Added scripts directorty with version specific bootstrap scripts (2025-12-29)
==========================================================================================

- Introduced `scripts/bootstrap-310.py` for projects requiring Python 3.10 or later.
- Introduced `scripts/bootstrap-38.py` for projects requiring Python 3.8 or later.
- Updated `README.rst` to document the new version-specific bootstrap scripts
  and their intended usage.
- Added post-bootstrap cleanup of temporary files created during the setup process
  to enhance script hygiene.


1.0.0-beta - Initial release of python-env-bootstrap (2025-12-27)
=================================================================

- First release of the python-env-bootstrap tool, providing a
  streamlined way to set up Python development environments with essential
  tools and configurations.
