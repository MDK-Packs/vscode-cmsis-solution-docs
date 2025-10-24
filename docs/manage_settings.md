# Manage solutions

In the **Manage Solution** view, you can select the [active target](#active-target),
[projects and images](#projects-and-images), and the [debug adapter](#debug-adapter) that you are using for target
connectivity.

In the **CMSIS view**, click ![Cogwheel icon](./images/cogwheel-icon.png) to open the **Manage Solution** view:

![Manage Solution view](./images/manage-solution-view.png)

## Active Target

In this section, select the **target type** that is used for build, run, and debug. The **target set** stores selected
projects, images, and debug adapter configuration.

To specify your target types by editing the YAML file directly, click **Edit csolution.yml**.

## Projects and images

In this section, select the projects, build types, and additional images that are included in the target set.

Select the **project(s)** that are part of the solution.

Select a **build type** for each project. You can set different build types for different projects in your solution.

Set the **load settings**:

- *Image & Symbols* (default): debug adapter loads debug (DWARF) information and project output image.
- *Symbols*: debug adapter loads only debug (DWARF) information.
- *Image*: debug adapter loads only project output image.
- *None*: debug adapter does not use the output, however the project is included in build.

Add further **images** with specific **load settgings**.

To specify your projects and images by editing the YAML file directly, click **Edit cproject.yml**.

!!! Note
    The projects and build types that you can select are defined by contexts for a particular target. Some options
    might be unavailable if they have been excluded for the target selected. To learn more about contexts and how to
    modify them, see the
    [Context](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/YML-Input-Format.md#context) and
    [Conditional build](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/YML-Input-Format.md#conditional-build)
    information in the CMSIS-Toolbox documentation.  
    For example, you can use `for-context` and `not-for-context` to include or exclude target types at the `project:`
    level in the `*.csolution.yml` file.

### Errors and warnings

You can inspect errors and warnings for a target set. For active projects in the target set, errors and warnings
display when you move your cursor over the **Target Set** in the status bar. The indicator is red for errors and yellow
in case of warnings.

![Target Set errors and warnings](./images/target-set-popup.png)

Click the indicator to open the **Output** tab for the **CMSIS Solution** category. If you previously closed the
**Manage Solution** view, then this action also re-opens the view.

You can also go to the **Problems** tab and check for errors.

## Debug Adapter

Use this drop-down to select the debug adapter that you are using within the target set. A broad range of adapters is
supported:

- CMSIS-DAP
- [Arm ULINKplus](./tipsandtricks.md#arm-ulinkplus)
- [Infineon KitProg3](./tipsandtricks.md#infineon-kitprog3)
- [NXP MCU-Link](./tipsandtricks.md#nxp-mcu-link)
- [Nuvoton NuLink](./tipsandtricks.md#nuvoton-nulink)
- [Microchip PICkit Basic](./tipsandtricks.md#microchip-pickit-basic)
- [Raspberry Pi Debugprobe](./tipsandtricks.md#raspberrry-pi-debugprobe)
- [STMicroelectronics ST-Link](./tipsandtricks.md#stmicroelectronics-st-link)
- [Segger J-Link](./tipsandtricks.md#segger-j-link)
- AVH-FVP
- Keil µVision

!!! Note
    Some of the debug adapters require further setup steps.
