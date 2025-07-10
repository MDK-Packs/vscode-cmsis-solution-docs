# Debug the application

Debugging is an essential task for every embedded developer. The [**CMSIS view**](./userinterface.md#cmsis-view) offers
[action buttons](./userinterface.md#3-actions-available-through-the-cmsis-view) to start a debug session. The
[**Run and Debug View**](./userinterface.md#run-and-debug-view) lets you connect to the target.

Refer to the
[Arm CMSIS Debugger extension](https://marketplace.visualstudio.com/items?itemName=Arm.vscode-cmsis-debugger) for a
detailed description of debug features.

<!--
## CMSIS View

![CMSIS View Action buttons](./images/CMSIS-View-ConfDebug.png)

The CMSIS View offers these action buttons:

- **Load & Run** a *csolution* application which downloads and starts the application images in the target.
- **Load & Debug** a *csolution* application which downloads the application images and starts the debugger.
- **Manage Solution** configures the debug setup with the `target-set:` node. It also supports multiple configurations
  using a `set:` name.

The action button:

- **Load & Run** executes from `tasks.json` the command `CMSIS Load+Run`.
- **Load & Debug** executes from `launch.json` the first section with `"request": "launch"` and `cmsis:`. If this is
  not present it uses from `tasks.json` the command `CMSIS Load+Debug`.

Further commands are available under `...`:

- **Load** executes from `tasks.json` the command `CMSIS Load`.
- **Erase** executes from `tasks.json` the command `CMSIS Erase`.
- **Run** executes from `tasks.json` the command `CMSIS Run`.
## Run and Debug View

The **Run and Debug View** in VS Code connects to the target using the request selection shown below.

![Debug View Debugger request](./images/Debug-View-ConfDebug.png)

The **CMSIS Solution** extension handles multiple processor cores using one debug connection for each core.

![Generate launch.json and tasks.json](./images/multicore-debug.png)
-->

## Debug on hardware

!!! Attention
    Make sure that your project and target are set up correctly and that the project can be
    [loaded and run](./create_app.md#load-and-run).

Keil Studio extension handles debugging as follows:

![Generate launch.json and tasks.json](./images/multicore-debug.png)

For each processor core, one debug server port is created. The underlying protocol is GDB MI using a GDB server. The
server accesses the processor core via JTAG or SWD through a corresponding debug adapter.

### Debug adapter support

Keil Studio support various debug adapters and and GDB server implementations from different vendors:

- Most of the debug adapters (including ST-Link) are served by [pyOCD](#using-pyocd) using the
  [Arm CMSIS Debugger extension](https://marketplace.visualstudio.com/items?itemName=Arm.vscode-cmsis-debugger).
- Segger [J-Link Server](#using-j-link-server) is supported.
- [Arm Debugger](#arm-debugger) and the
  [Arm Debugger extension](https://marketplace.visualstudio.com/items?itemName=Arm.arm-debugger) are supported.
- You can also use Arm [Keil µVision](#keil-uvision) for debugging a project.

### Using pyOCD

[pyOCD](https://pyocd.io/) is a Python-based tool and API for debugging and programming. It supports many debug
adapters via the [CMSIS-DAP](https://arm-software.github.io/CMSIS_6/latest/DAP/index.html) protocol.

In the **CMSIS view**, open the [Manage Solution dialog](./manage_settings.md) and go to the
[Debug Adapter section](./manage_settings.md#debug-adapter). Select one of the debug adapters named `xyz@pyOCD`.

The following JSON files are created automatically:

- In the `launch.json` file, `attach` and `launch` configurations are added that let you attach the debug adapter
  to an already running GDB instance (for example when you have issued a [`load and run`](./create_app.md#load-and-run)
  before) or launch a new debug session.
- In the `tasks.json` file, the tasks `CMSIS Erase`, `CMSIS Load`, and `CMSIS Run` are created.

!!! Note
    Before entering a debug session, make sure that you have met the
    [prerequisites](./tipsandtricks.md#installing-debug-adapters) of your debug adapter.

#### Command line usage

pyOCD can be also used on the command line. In a **Terminal**, issue for example:

```sh
pyocd list      --cbuild-run MyProject+TargetHW.cbuild-run.yml   // details of debug connection (scan JTAG, SWD)
pyocd gdbserver --cbuild-run MyProject+TargetHW.cbuild-run.yml   // start debug server, load command: flash
pyocd load      --cbuild-run MyProject+TargetHW.cbuild-run.yml   // flash and run application
pyocd erase     --cbuild-run MyProject+TargetHW.cbuild-run.yml   // erase image on device
```

#### Selecting a debug adapter

!!! ToDo
    Explain how to select a CMSIS-DAP probe in case multiple are connected.

### Using J-Link Server

!!! Attention
    Make sure that the [J-Link software](./tipsandtricks.md#segger-j-link) is installed on your machine before
    attempting to use a J-Link adapter.

In the **CMSIS view**, open the [Manage Solution dialog](./manage_settings.md) and go to the
[Debug Adapter section](./manage_settings.md#debug-adapter). Select "JLink Server".

The following JSON files are created automatically:

- The `tasks.json` file is populated with `CMSIS Erase`,  `CMSIS Load`, and `CMSIS Run` tasks.
- The `launch.json` file is populated with `JLink (launch)` and `JLink (attach)` configurations.

### Arm Debugger

You can use the [Arm Debugger](https://developer.arm.com/Tools%20and%20Software/Arm%20Debugger) with Keil Studio.

#### Prerequisites

Before you can launch a debug session using Arm Debugger, you need to:

1. Install the [Arm Debugger VS Code extension](https://marketplace.visualstudio.com/items?itemName=Arm.arm-debugger).
2. Add the Arm Debugger to your `vcpkg-configuration.json` file, for example:  
   `  "arm:debuggers/arm/armdbg": "6.6.0"`

#### Setup for Arm Debugger

In the **CMSIS view**, open the [Manage Solution dialog](./manage_settings.md) and go to the
[Debug Adapter section](./manage_settings.md#debug-adapter). Select one of the debug adapters named `xyz@Arm-Debugger`.

The following JSON files are created automatically:

- In the `launch.json` file, `attach` and `launch` configurations are added that let you attach the debug adapter
  to an already running GDB instance (for example when you have issued a [`load and run`](./create_app.md#load-and-run)
  before) or launch a new debug session.
- In the `tasks.json` file, the tasks `CMSIS Erase`, `CMSIS Load`, and `CMSIS Run` are created.

### Keil uVision

!!! Attention
    This only works on a Windows PC as µVision runs on Windows.

## Debug in simulation
