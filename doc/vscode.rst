VSCode
======

Pytest is supported by the excellent Python plugin of VSCode, so pynvme is! User can develop and run test scripts in this excellent IDE, with pynvme plugin. 

Layout
------

.. image:: pic/vscode_area.png
   :target: pic/vscode_area.png
   :alt: vscode screenshot

A. Activity Bar: you can select the last Test icon for pytest and pynvme extensions.
#. pytest panel: collects all test files and cases in scripts directory.
#. pynvme panel: displays all active qpairs in all controllers. Click qpair to open or refresh its cmdlog viewer.
#. editor: edit test scripts here.
#. cmdlog viewer: displays the latest 128 commands and completion dwords in one qpair.
#. log viewer: displays pytest log.

Setup
-----

#. First of all, install vscode here: https://code.visualstudio.com/

#. Root user is not recommended in vscode, so just use your ordinary non-root user. It is required to configure the user account to run sudo without a password.

   .. code-block:: shell

      sudo visudo

#. In order to monitor qpairs status and cmdlog along the progress of testing, user can install vscode extension pynvme-console. The extension provides DUT status and cmdlogs in VSCode UI.

   .. code-block:: shell

      code --install-extension pynvme-console-1.x.x.vsix

#. Before start vscode, modify .vscode/settings.json with the correct pcie address (bus:device.function listed in `lspci` command) of your DUT device.

   .. code-block:: shell

      lspci
      # 01:00.0 Non-Volatile memory controller: Lite-On Technology Corporation Device 2300 (rev 01)

#. Then in pynvme folder, we can start vscode to edit, debug and run scripts:

   .. code-block:: shell

      make setup; code .  # make sure to enable SPDK nvme driver before starting vscode

#. Users can add their own script files under `scripts` directory. Import following packages in new test script files.

   .. code-block:: python

      import pytest
      import logging
      import nvme as d    # import pynvme's python package


Now, we can edit, debug and run test scripts in VSCode! It time to learn more pynvme features and write our own scripts for NVMe testing in VSCode. 
