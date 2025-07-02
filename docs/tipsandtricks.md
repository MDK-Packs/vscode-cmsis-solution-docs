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

- Uninstall the Snap package. For example, run `sudo snap remove firefox` in a Terminal.

- Download the installer from the browser's web site.

- Install it on your machine.

## Installing debug adapters

If you are using a third-party debug adapter, make sure that the latest drivers are installed on your machine

Make sure the debug adapters are running the latest firmware and that the `PATH` variable is set correctly.

### Infineon KitProg3

Make sure that the latest [firmware is installed](https://community.infineon.com/t5/Knowledge-Base-Articles/ModusToolbox-Updating-the-KitProg3-MiniProg4-firmware-from-modus-shell/ta-p/625419#.).

### Microchip PICKit Basic

Use the Python utility [pycmsisdapswitcher](https://pypi.org/project/pycmsisdapswitcher/) to switch the firmware to a
CMSIS-DAP v2 implementation.

### NXP MCU-Link

Make sure that the latest
[firmware is installed](https://community.nxp.com/t5/MCUXpresso-General-Knowledge/MCU-Link-installation/ta-p/1180326).

### SEGGER J-Link

For J-Link support, visit [J-Link/J-Trace Downloads](https://www.segger.com/downloads/jlink/).

Set the `PATH` variable to the `bin` directory of the installation.

Verify the correct operation by entering the command `jlink` (Windows) or `jlinkexe` (Linux, macOS) in a Terminal. The
output should similar to this:

```sh
SEGGER J-Link Commander V8.24 (Compiled Mar 26 2025 15:34:18)
DLL version V8.24, compiled Mar 26 2025 15:33:37

Connecting to J-Link via USB...FAILED: Cannot connect to J-Link.
J-Link>
```

### STMicroelectronics ST-Link

For ST-LINK/V2 and ST-LINK/V2-1 support on Windows, download the USB driver here:
[STSW-LINK009](https://www.st.com/en/development-tools/stsw-link009.html).
