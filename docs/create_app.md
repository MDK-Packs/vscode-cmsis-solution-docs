# Create new solution

This section explains how to create a *CMSIS solution-based project* that is using CMSIS-Packs.

In the ![CMSIS view](./images/CMSISView.png) **CMSIS** view, click **Create a New Solution**. If you already have a
solution opened, use the menu (**...**) item **Create a Solution**.

![Create New Solution](./images/CreateNewSolution.png)

The **Create new solution** dialog allows to start projects based on a **Target Board** or **Target Device** selection.

Examples, templates, and reference applications depend on the selected board or device and on installed CMSIS-Packs.

- **Examples** are created for a specific hardware or evaluation board. These are typically complete projects that
  directly interface with board and device peripherals.
- **Reference Applications** use defined interfaces (APIs) and are therefore hardware agnostic. These projects require
  the installation of related CMSIS-Packs and additional software layers for an evaluation board.
- **Templates** are stub projects that help you getting started. Some CMSIS-Packs may contain device-specific
  templates.

The **Solution Sub Folder** is typically a sub-directory in your workspace.

The **Solution Base Folder** specifies your workspace location that may contain multiple projects.

With **Initialize Git repository** the related `.gitignore` file is created.

**Show project opening options** allows you to open the spolution a new instance of VS Code. By default, the solution
is loaded into the current VS Code instance.

## Work with examples

Click the **Target Board (Optional)** drop-down list. Enter a search term (here: "U5"), and then select a board
(here: "B-U585-IOT02A"). The details of the selected board are displayed.

![Hardware Picker](./images/hardware-picker.png)

Click **Select**.

Next, select the example project. There are two types of example projects:

- **Csolution Examples** are using Keil Studio's native project format.

- **uVision Examples** are in `*.uvprojx` format and are converted automatically.

!!! Note
    You may see examples from **Local** packs and/or from the **Web**.

To verify the Keil Studio installation, select a **Blinky** project for example.

Specify a **Solution Base Folder** and click **Create**.

Continue to ["build the project"](#build).

## Work with reference applications

**Reference applications** show the usage of middleware, software libraries, and custom code that can run on many
different target hardware boards. Examples display only if you selected a board and a software layer is available for
that board. Reference applications are not dependent on specific hardware. You can deploy them to various evaluation
boards using additional software layers that provide driver APIs for specific target hardware. Layers are provided
using CMSIS-Packs.

Reference applications are available with these CMSIS-Packs:

- [MDK-Middleware](https://www.keil.arm.com/packs/mdk-middleware-keil/overview/): use software components for IPv4 and
  IPv6 networking, USB Host and Device communication, and file system for data storage.

- [SDS Framework](https://www.keil.arm.com/packs/sds-arm/overview/): record real-world data off a device and playing it
  back on Arm Virtual Hardware.

- [LiteRT](https://www.keil.arm.com/packs/tensorflow-lite-micro-tensorflow/overview/): demonstrates the fundamental
  integration and usage of the LiteRT stack for ML inference on a microcontroller.

Once you have selected the reference application, continue to ["build the project"](#build).

## Work with templates

Templates help you to get started without application-specific code.

- **Blank solution**: Start a project from scratch with an empty `main.c` file and the CMSIS device startup component
  selected

- **TrustZone solution**: If the board or device that you selected is compatible, you can use TrustZone and define
  whether projects in the solution use secure or non-secure zones

Continue to ["build the project"](#build).

## Project contents

Once you have selected an example/template/reference application, the solution is created automatically. If a uVision
example is converted, check the **Output** tab. Conversion errors and warnings are displayed in the **CMSIS Solution**
category. You can also check the `uv2csolution.log` file.

!!! Note
    If you are using Keil Studio for the first time, the **Arm Tools Environment Manager** needs to download required
    tools from the Internet. While may take a couple of minutes (depending on your internet connection), it is only
    required once.

The following files are created for the solution:

- A `<solution_name>.csolution.yml` file.

- One or more `<project_name>.cproject.yml` files, each available in a separate folder.

- A `cdefault.yml` file containing default toolchain setting for the selected toolchain.

- A `<solution_name>.cbuild-idx.yml` file which contains overall information for the application.

- A `<solution_name>.cbuild-pack.yml` file listing all the packs that are used by the application. Missing CMSIS-Packs
  are installed automatically.

- A `<solution_name>.cbuild-set.yml` file which specifies the context set of projects, target-types, and build-types
  that are used to generate the application image

- A `<solution_name>+<target_name>.cbuild-run.yml` file which contains a build description of a single `cproject.yml`
  input file for each context.

- A main `<filename>.c` template file for each project.

- A `vcpkg-configuration.json` file to download required tools automatically.

!!! CAUTION
    If you see this warning:
    ![Task errors output](./images/task-errors.png)
    Click **Show output** to configure the solution. You can add board, shield, or socket layers to your reference
    application. You can also select a compiler for reference applications and other solution types.

Depending on the selected example, you might need to [configure the solution](./configuration.md#configure-a-solution)
first.

First time users may need to confirm that the **Arm Tools Environment Manager** extension can automatically activate
the workspace and download the tools specified in the `vcpkg-configuration.json` file included in a project.

## Build

Before you can download the application on your target device, you need to build it. There are various ways to trigger
a build:

- In the **Explorer** view ![Explorer icon](./images/ExplorerView.png), right-click the `*.csolution.yml` file and
  select **Build solution**.

- In the **CMSIS** view ![CMSIS view](./images/CMSISView.png), click ![Build icon](./images/build-icon.png).

You can configure a build task in a `tasks.json` file to customize the behavior of the build button. All the examples
on [keil.arm.com](https://www.keil.arm.com) include a `tasks.json` file. See
[Configure a build task](./configuration.md#configure-a-build-task) for more details.

Continue to [load and run](#load-and-run) the solution.

### Build output

After you initiate the build process, a Terminal window opens and displays the build operation:

```txt
Execute: cbuild /Users/user/03_work/02_Projects/ST/Nucleo-F756ZG/Blinky/Blinky.csolution.yml --active NUCLEO-F756ZG --packs
+---------------------------------------------------
(1/1) Building context: "Blinky.Debug+NUCLEO-F756ZG"
Using AC6 V6.24.0 compiler, from: '/Users/user/.vcpkg/artifacts/2139c4c6/compilers.arm.armclang/6.24.0/bin/'
Building CMake target 'Blinky.Debug+NUCLEO-F756ZG'
[1/51] Building C object CMakeFiles/Group_Source_Files_retarget_stdio_c.dir/Users/user/03_work/02_Projects/ST/Nucleo-F756ZG/Blinky/retarget_stdio.o
[2/51] Building ASM object CMakeFiles/Group_CubeMX.dir/Users/user/03_work/02_Projects/ST/Nucleo-F756ZG/Blinky/STM32CubeMX/NUCLEO-F756ZG/STM32CubeMX/MDK-ARM/startup_stm32f756xx.o
Warning: A1950W: The legacy armasm assembler is deprecated. Consider using the armclang integrated assembler instead.
0 Errors, 1 Warning
[3/51] Building C object CMakeFiles/Group_CubeMX.dir/Users/user/03_work/02_Projects/ST/Nucleo-F756ZG/Blinky/STM32CubeMX/NUCLEO-F756ZG/STM32CubeMX/Src/stm32f7xx_hal_timebase_tim.o
...
[49/51] Building C object CMakeFiles/Keil_CMSIS_Driver_USART_3_0_0.dir/Users/user/.cache/arm/packs/ARM/CMSIS-Driver_STM32/1.1.0/Drivers/USART_STM32.o
[50/51] Building C object CMakeFiles/ARM_CMSIS_RTOS2_Keil_RTX5_Source_5_9_0.dir/Users/user/.cache/arm/packs/ARM/CMSIS-RTX/5.9.0/Source/rtx_thread.o
[51/51] Linking C executable /Users/user/03_work/02_Projects/ST/Nucleo-F756ZG/Blinky/out/Blinky/NUCLEO-F756ZG/Debug/Blinky.axf
Program Size: Code=31972 RO-data=1076 RW-data=512 ZI-data=38760  
+------------------------------------------------------------
Build summary: 1 succeeded, 0 failed - Time Elapsed: 00:00:04
+============================================================
Completed: cbuild succeed with exit code 0
Build complete
```

The output directory usually contains an ELF (`.axf`) and a HEX (`.hex`) file.

!!! Note
    If the build fails with an `ENOENT` error, follow the instructions in the pop-up message that displays in the
    bottom right-hand corner to install CMSIS-Toolbox.

## Load and Run

Make sure that your target is connected, before loading the application onto it. You can use `pyOCD` to verify target
connectivity.

1. Open a **Terminal**, and enter `pyOCD list` to check attached hardware:
   ![Check connected hardware with pyOCD](./images/pyOCDlist.png)
2. In the **CMSIS** view, click ![Run icon](./images/run-icon.png). This executes the "Load & Run application" command
   that flashes the project onto the target and issues a reset to start the application.
3. To verify that the step has run correctly, check the **Terminal** output:
   ![Flash download output](./images/flash-dwnl-output.png)

!!! Notes
    - When you have several solutions in one folder, VS Code ignores the `tasks.json` and `launch.json` files that
    you created for each solution. Instead, VS Code generates new JSON files at the root of the workspace in a
    `.vscode` folder and ignores the other JSON files. As a workaround, open one solution first, then add other
    solutions to your workspace with the **File** > **Add Folder to Workspace** option.
    - If you are using a multi-core device and you did not specify a `"processorName"` in the `launch.json` file,
      select the appropriate processor for your project in the **Select a processor** drop-down list at the top of the
      window.

### Monitoring printf messages

Keil Studio includes the **Serial Monitor** extension that connects to the target's serial output port. If your example
contains `printf` statements, use the Serial Monitor to observe them.

![Serial Monitor showing printf messages](./images/serial-monitor.png)