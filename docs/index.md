# Arm Keil Studio

The **Arm® Keil Studio** extension pack for VS Code is a comprehensive software development platform for Arm Cortex-M
processor-based devices.

The IDE:

- supports single and multi-core processor systems, including Ethos-U NPUs.

- has wide software support for projects based on CMSIS, FreeRTOS, RTX, and Zephyr.

- utilizes CMSIS-Pack content to configure debug adapters and access re-usable software components.

- can be combined with other VS Code debug extensions, such as those for Linux application development.

## Contents

- [**Installation**](./installation.md) explains how to install Keil Studio along with a build
  environment for embedded applications that are based on Arm Cortex-M processors.

- [**User interface**](./userinterface.md) shows the main features available in the GUI.

- [**Create new solution**](./create_app.md) explains how to start an embedded project from scratch.

- [**Manage solution**](./manage_settings.md) explains how to configure a *csolution project*.

- [**Software components**](./manage_components.md) shows how to add or remove software components in a
  solution.

- [**Debug**](./debug.md) explains how to debug a project.

- [**Configuration**](./configuration.md) explains how to manage the extension settings and some specific configuration
  options, for example for run and debug.

- [**Import µVision project**](./importuv.md) explains how to convert uvprojx-based files to the csolution format.

- [**Run external tools**](./runexternal.md) describes how to use external tools, such as debuggers and flash
  programmers.

- [**Tips and tricks**](./tipsandtricks.md) provides tips and tricks to help you solve specific issues.

## Revision history

Version            | Description
:------------------|:-------------------------
1.5x.0             | Rework for better clarity
1.54.0             | Added CMSIS-Toolbox Run and Debug Management
1.48.0             | Initial release for the CMSIS Solution extension version 1.48.0
