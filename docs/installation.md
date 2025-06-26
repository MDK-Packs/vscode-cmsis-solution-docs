# Installation

<!-- markdownlint-disable MD036 -->

## Prerequisites

1. As Keil Studio is a set of extensions for [Microsoft Visual Studio Code](https://code.visualstudio.com/), make sure
   this is installed on your machine.
2. If you are using a third-party debug adapter, make sure that the latest drivers are installed on your machine:
    - For ST-LINK support on Windows, visit [STSW-LINK009](https://www.st.com/en/development-tools/stsw-link009.html).
    - For J-Link support, visit [J-Link/J-Trace Downloads](https://www.segger.com/downloads/jlink/).

   Make sure the debug adapters are running the latest firmware and that the `PATH` variable is set correctly.

For J-Link, you can verify the correct operation by entering the command `jlink` (Windows) or `jlinkexe` (Linux, macOS)
in a Terminal window. The output should similar to this:

```sh
SEGGER J-Link Commander V8.24 (Compiled Mar 26 2025 15:34:18)
DLL version V8.24, compiled Mar 26 2025 15:33:37

Connecting to J-Link via USB...FAILED: Cannot connect to J-Link.
J-Link>
```

## Installing Keil Studio

The [**Arm Keil Studio Pack (MDK v6)**](https://marketplace.visualstudio.com/items?itemName=Arm.keil-studio-pack)
extension pack includes the extensions that are required to work with CMSIS solution projects.

1. In VS Code, open the **Extensions** view and type `Keil Studio Pack` in the search bar.

2. Click **Install** to start the installation. When the installation is finished, the CMSIS view icon appears in the
   activity bar.

You can [create your first application](./create_app.md) or
[verify the installation with an example project](#verify-the-installation) and then check that you can build, run, and
debug the application.

!!!Note
    If you do not want to install all the extensions available in the pack, you can install the
    [Arm CMSIS Solution](https://marketplace.visualstudio.com/items?itemName=Arm.cmsis-csolution) extension standalone.
    Search for `CMSIS Solution` in the **Extensions** view.

## Verify the installation

Once you have installed Keil Studio, you can verify your installation using one of the examples provided in a
CMSIS-Pack.

Start [creating a new solution](./create_app.md) based on a Blinky example, which typically flashes an LED on a target
board.
