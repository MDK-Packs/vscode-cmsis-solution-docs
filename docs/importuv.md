# Import a Keil µVision project

With the CMSIS Solution extension, you can convert Keil μVision project to a CMSIS solution.

1. Open the folder that contains the `*.uvprojx` that you want to convert in Visual Studio Code. Alternatively, import a
   μVision project from [keil.arm.com](https://www.keil.arm.com/), or clone a project from GitHub.

2. Right-click the `*.uvprojx` file and select **Convert μVision project to CMSIS solution** from the **Explorer** view.

The conversion starts immediately.

Alternatively, if you are starting from an empty workspace, you can click ![CMSIS icon]( ./images/cmsis-icon.png) in the
**Activity Bar** to open the **CMSIS** view. Then choose one of the following two options:

- Click **Convert a μVision Project to CMSIS Solution** and open your `*.uvprojx` file to convert it.
- Move your cursor over the **Solution** outline, click **Views More Actions...**
  ![Views and More Actions icon](./images/more-actions-icon.png), then select **Convert μVision project to CMSIS solution**
  and open your `*.uvprojx` file to convert it.

A dialog box displays. You can carry out the following tasks:

- Open the solution in a new workspace with the **Open** option.
- Open the solution in a new window and new workspace with the **Open project in new window** option.

You can also run the **CMSIS: Convert μVision project to CMSIS solution** command from the Command Palette. In that case,
select the `*.uvprojx` that you want to convert on your machine and click Select.

If there are conversion errors, check the `uv2csolution.log` file.

1. Confirm that the **Arm Tools Environment Manager extension** can automatically
   activate the workspace and download the tools specified in your `vcpkg-configuration.json` file.

2. Check the Output tab. In the View menu, select **Output** to open the **Output** tab. Select
   **μVision to Csolution Conversion** in the drop-down list on the right side of the **Output** tab.

The `*.cproject.yml` and `*.csolution.yml` files are available in the folder where the `*.uvprojx` is stored.

!!! Attention
    The conversion does not work with Arm Compiler 5-based projects. Only projects using Arm Compiler 6 can be converted.
    As a workaround, you can update Arm Compiler 5 projects to Arm Compiler 6 in Keil μVision, then convert the projects to
    solutions in Visual Studio Code. For more information, see the
    [Migrate Arm Compiler 5 to Arm Compiler 6 application note](https://developer.arm.com/documentation/kan298/latest/) and
    the [Arm Compiler for Embedded Migration and Compatibility Guide](https://developer.arm.com/documentation/100068/0620/Migrating-from-Arm-Compiler-5-to-Arm-Compiler-for-Embedded-6).

