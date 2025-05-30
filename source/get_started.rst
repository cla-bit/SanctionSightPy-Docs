====================
Getting Started
====================


System Requirements
-------------------
•	Python 3.13 or higher.
•	Supported operating systems: Windows, macOS, Linux.


Installation Steps
------------------

You can use `Poetry` or any dependency manager or use the general `pip install` command to install `SanctionSightPy`.

**Option 1: Install with Poetry**

First, make sure you have Poetry installed. You can install it using the following command:

    * Using **pip** command to install poetry:

    .. code-block:: console

        >>> pip install poetry

    * Using **pipx** command to install poetry:

    .. code-block:: console

        >>> pipx install poetry

    * Using **curl** command to install poetry:

    .. code-block:: console

        >>> curl -sSL https://install.python-poetry.org | python3 -

Create a project using poetry command. This will create a `pyproject.TOML` in your project.
Follow the instructions to finish creating your project:

    .. code-block:: console

        >>> poetry new project

Change directory to your project

   .. code-block:: console

        >>> cd project_name

Run the poetry command to add `SanctionSightPy`:

    .. code-block:: console

        >>> poetry add SanctionSightPy


**Option 2: Install with pip**

    .. code-block:: console

        >>> pip install SanctionSightPy



Use SanctionSightPy with Jupyter
--------------------------------

1. Open notebook in your project and install `SanctionSightPy` using `pip` command.

    .. code-block:: console

        >>> !pip install SanctionSightPy


----------------------------------


**How to use the latest version of `SanctionSightPy` in your terminal.**

   .. code-block:: console

        >>> pip install --upgrade SanctionSightPy

or

   .. code-block:: console

        >>> pip install SanctionSightPy==<latest version number here>


See examples on how to use `SanctionSightPy` to get financial statements :doc:`examples`
