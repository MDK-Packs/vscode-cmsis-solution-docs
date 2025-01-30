# Run external tools

Visual Studio Code uses the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and [tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files to integrate with external tools. The following section shows how to configure these files for typical use cases.

[Variables and commands](#variables-and-commands) provide access to parameters of the current active *csolution project*.

## Programmer

ToDo show usage of command-line programmer (i.e. STCube Programmer)

## Debug server

ToDo show usage of Cortex Debug configured for JLink

## Use µVision for debugging

The [µVision debugger](https://developer.arm.com/documentation/101407/0541/Debugging) offers advanced debug features such as
Event Recorder and Component Viewer to analyze applications.

To call µVision with the *csolution project* that you are using in Visual Studio Code, add the following task to the `.vscode\tasks.json`  file. The `command:` is the path to the µVision executable on your computer.

```json
    "tasks": [
        {
            "label": "Start uVision",
            "type": "process",
            "command": "C:\\Keil_v5\\UV4\\UV4.exe",
            "args": [
                "${command:cmsis-csolution.getSolutionPath}"
            ],
            "problemMatcher": []
        }
    ]
```

!!! Note
    This only works in Windows environments with µVision installed on the local machine.

## Variables and commands

Visual Studio Code supports variable and command substitution in the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and
[tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files as well as some select settings. In
addition to the [Visual Studio Code built-in variables](https://code.visualstudio.com/docs/editor/variables-reference), the CMSIS
Solution extension provides the following commands to access parameters of the current active *csolution project*.

| Command  | Description |
|----------|-------------|
| The `${command:cmsis-csolution.getBinaryFile}`               | Elf/Dwarf location of the currently selected context |
| The `${command:cmsis-csolution.getBinaryFiles}`              | Elf/Dwarf location of all files in the current solution |
| `${command:cmsis-csolution.getBspName}`                  | The name and version of the [Board Support Pack (BSP)](https://www.keil.arm.com/boards/) |
| `${command:cmsis-csolution.getBspPath}`                  | Path to [Board Support Pack (BSP)](https://www.keil.arm.com/boards/) file of the current active target |
| `${command:cmsis-csolution.getCbuildRunPath}`            | Path to the `cbuild-run.yml` file |
| `${command:cmsis-csolution.getDeviceName}`               | Device name of the active target |
| `${command:cmsis-csolution.getDfpName}`                  | Name and version of the [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) |
| `${command:cmsis-csolution.getDfpPath}`                  | Path to the [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) file of the current active target |
| `${command:cmsis-csolution.getHardwareAndToolchainInfo}` | Target hardware and toolchain for the active solution |
| `${command:cmsis-csolution.getProcessorName}`            | The processor name for the currently selected context |
| `${command:cmsis-csolution.getSolutionPath}`             | Path to the active solution file |
| `${command:cmsis-csolution.getTargetPack}`               | The [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) for the currently selected context |

### Substitution examples

**launch.json**

Use the following `launch.json` file to start Arm Debugger:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Arm Debugger",
            "type": "arm-debugger",
            "request": "launch",
            "serialNumber": "${command:device-manager.getSerialNumber}",
            "programs": "${command:cmsis-csolution.getBinaryFiles}",
            "cmsisPack": "${command:cmsis-csolution.getTargetPack}",
            "deviceName": "${command:cmsis-csolution.getDeviceName}",
        }
    ]
}
```

For an STMicroelectronics B-U585-IOT02A board, the commands might resolve to:

- `${command:cmsis-csolution.getBinaryFiles}:` /Users/user/Blinky/out/Blinky/B-U585I-IOT02A/Debug/Blinky.axf

- `${command:cmsis-csolution.getTargetPack}:` Keil::STM32U5xx_DFP@3.0.0

- `${command:cmsis-csolution.getDeviceName}:` STM32U585AIIx

Use the following `launch.json` file to start debugging with pyOCD:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "gdbtarget",
            "request": "launch",
            "name": "Debug with pyOCD",
            "program": "${command:cmsis-csolution.getBinaryFile}",
            "cwd": "${workspaceFolder}",
            "verbose": true,
            "gdb": "/Applications/ArmGNUToolchain/13.3.rel1/arm-none-eabi/bin/arm-none-eabi-gdb",
            "initCommands": [
                "monitor set reset-type SW_EMULATED",
                "monitor reset halt"
            ],
            "target": {
                "server": "python",
                "serverParameters": [
                    "-mpyocd",
                    "gdbserver",
                    "--target",
                    "${command:cmsis-csolution.getDeviceName}",
                    "--pack",
                    "${command:cmsis-csolution.getDfpPath}",
                    "--port",
                    "3333"
                ],
                "port": "3333"
            }
        }
    ]
}
```

For a NXP LPCXpresso55S69 board, the commands might resolve to:

- `${command:cmsis-csolution.getBinaryFiles}:` /Users/user/hello_world/cm33_core1/armgcc/debug/core1_image.elf, /Users/user/hello_world/cm33_core0/armgcc/debug/hello_world_cm33_core0.elf

- `${command:cmsis-csolution.getDeviceName}:` LPC55S69JBD100

- `${command:cmsis-csolution.getDfpPath}:` /Users/user/.cache/arm/packs/NXP/LPC55S69_DFP/19.0.0
