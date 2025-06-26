# Tips and tricks

This chapter contains useful information to help you solve specific issues.

## Create vcpkg configuration file

If your solution does not contain the `vcpkg-configuration.json`, right-click anywhere in the workspace and select
**Configure Arm Tools Environment**. The **Arm Tools Environment Manager** extension then generates this file.

## Set current solution in workspace

To activate a solution in the **Solution** outline view, use the **Select Active Solution from workspace** option in
**Views and More Actions** ![Views and More Actions icon](./images/more-actions-icon.png).

## Documentation does not open

If you are using a Linux machine that uses the Snap package manager, your web browser will not be able to open
documentation that is shipped in CMSIS-Packs as the `CMSIS_PACK_ROOT` directory is in `${HOME}/.cache/arm/packs` which
is not accessible to Snaps. Likewise, the Keil Studio help is located in `${HOME}/.vscode/extensions` which is also not
available.

To get this working, use a browser that is not installed as a Snap package:

- Uninstall the Snap package. For example, run `sudo snap remove firefox` in a Terminal window.

- Download the installer from the browser's web site.

- Install it on your machine.
