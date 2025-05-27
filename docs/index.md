# CMSIS Solution extension

The **CMSIS Solution** extension available for VS Code allows to create projects and build embedded applications that
use [CMSIS-Packs](https://www.keil.arm.com/packs/). 
It is a user interface for the [CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/) that supports various compilation tools including Arm Compiler 6, GCC, IAR, and LLVM.

## Contents

- [**Installation**](installation.md) explains how to install the CMSIS Solution extension along with a build
  environment for embedded applications that are based on Arm Cortex-M processors.

- [**User interface**](userinterface.md) shows the main features available in the CMSIS Solution extension GUI.

- [**Create an embedded project**](create_app.md) explains how to start a project from scratch.

- [**Manage software components**](./manage_components.md) shows how to add or remove software components in a
  solution.

- [**Manage solution settings**](./manage_settings.md) explains how to configure a *csolution project* for run and
  debug.

- [**Build**](build.md) describes how to build a project.

- [**Load and run**](./flash.md) explains how to load and run an application on your hardware.

- [**Debug**](debug.md) explains how to debug a project.

- [**Configuration**](configuration.md) explains how to manage the extension settings and some specific configuration
  options, for example for run and debug.

- [**Import µVision project**](./importuv.md) explains how to convert uvprojx-based files to the CMSIS Solution format.

- [**Run external tools**](./runexternal.md) describes how to use external tools, such as debuggers and flash
  programmers.

- [**Tips and tricks**](./tipsandtricks.md) provides tips and tricks to help you solve specific issues.

## Revision history

Version            | Description
:------------------|:-------------------------
1.54.0             | Added CMSIS-Toolbox Run and Debug Management
1.48.0             | Initial release for the CMSIS Solution extension version 1.48.0
