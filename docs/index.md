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

- [**Work with CMSIS solutions**](./create_app.md) explains how to start an embedded project from scratch or use
  pre-built examples.

- [**Work with Zephyr applications**](./zephyr.md) explains how to build applications based on Zephyr.

- [**Manage solutions**](./manage_settings.md) explains how to configure *csolution projects*.

- [**Build and run**](./build_run.md) shows how to build and run a CMSIS solution or Zephyr application.

- [**Debug**](./debug.md) explains how to debug a CMSIS solution or Zephyr application.

- [**Import µVision project**](./importuv.md) explains how to convert uvprojx-based files to the csolution format.

- [**Run external tools**](./runexternal.md) describes how to use external tools, such as debuggers and flash
  programmers.

- [**Tips and tricks**](./tipsandtricks.md) provides tips and tricks to help you solve specific issues.

- [**Related documentation**](./reldocs.md) contains links to supporting documentation, videos, and webinars.

- [**Features and roadmap**](./featureroadmap.md) presents the implemented features and our current feature roadmap.

## Revision history

Version            | Description
:------------------|:-------------------------
1.66.0             | Added **Software pack**, **Related Documentation**, and **Features and roadmap** chapters
1.64.0             | Added **Work with Zephyr applications** and reworked other chapters
1.62.0             | Reworked **Manage solutions** and **Debug** chapters
1.55.0             | Rework for better clarity
1.54.0             | Added CMSIS-Toolbox Run and Debug Management
1.48.0             | Initial release for the CMSIS Solution extension version 1.48.0
