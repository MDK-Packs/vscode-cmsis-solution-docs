# Run external tools

Visual Studio Code uses the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and [tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files to integrate with external tools. The following section shows how to configure these files for typical use cases.

## Variables

Visual Studio Code supports [variable substitution](https://code.visualstudio.com/docs/editor/variables-reference) in the [Debugging](https://code.visualstudio.com/docs/editor/debugging) and
[Tasks](https://code.visualstudio.com/docs/editor/tasks) configuration files and selected settings. Variable substitution uses the `${variableName}` syntax, for example in `launch.json` and `tasks.json` files.
In addition to the [Visual Studio Code built-in variables](https://code.visualstudio.com/docs/editor/variables-reference), the CMSIS Solution extension provides the following variables.

| Variable  | Description |
|:----------|:------------|
| `${command:cmsis-csolution.getBinaryFile}`     | Path and name of first ELF/DWARF file in Active Target |
| `${command:cmsis-csolution.getBinaryFiles}`    | Path and name of ELF/DWARF files (comma separated) in Active Target |
| `${command:cmsis-csolution.getBoardName}`      | Board name of Active Target as specified in csolution.yml |
| `${command:cmsis-csolution.getBspName}`        | Board Support Pack (BSP) used in Active Target |
| `${command:cmsis-csolution.getBspPath}`        | Path to content of BSP used in Active Target |
| `${command:cmsis-csolution.getCbuildRunFile}`  | Path and name to cbuild-run.yml file of Active Target |
| `${command:cmsis-csolution.getDeviceName}`     | Device name of Active Target as specified in csolution.yml |
| `${command:cmsis-csolution.getDfpName}`        | Device Family Pack (DFP) used in Active Target |
| `${command:cmsis-csolution.getDfpPath}`        | Path to content of DFP used in Active Target |
| `${command:cmsis-csolution.getSolutionFile}`   | Path and name to csolution.yml file of Active Solution |

The term:

- Active Solution refers to the *csolution project* that is currently loaded.
- Active Target refers to the target that is currently selected in the [Manage Solution](manage_settings.md) view.

### Substitution examples

The following table examplifies the variable substition using the [DualCore csolution example](https://github.com/Open-CMSIS-Pack/csolution-examples/tree/main/DualCore). Note that `...` stands for the absolute path on the host computer that stores the *csolution project* or the [CMSIS pack content](https://open-cmsis-pack.github.io/cmsis-toolbox/installation/#environment-variables).

| Variable  | Substitution |
|:----------|:-------------|
| `${command:cmsis-csolution.getBinaryFile}`    | .../DualCore/out/HelloWorld_cm4/FRDM-K32L3A6/Debug/HelloWorld_cm4.axf |
| `${command:cmsis-csolution.getBinaryFiles}`   | .../DualCore/out/HelloWorld_cm4/FRDM-K32L3A6/Debug/HelloWorld_cm4.axf, .../DualCore/out/HelloWorld_cm0plus/FRDM-K32L3A6/Debug/HelloWorld_cm0plus.axf |
| `${command:cmsis-csolution.getBoardName}`     | K32L3A60VPJ1A |
| `${command:cmsis-csolution.getBspName}`       | NXP::FRDM-K32L3A6_BSP@19.0.0 |
| `${command:cmsis-csolution.getBspPath}`       | .../NXP/FRDM-K32L3A6_BSP/19.0.0 |
| `${command:cmsis-csolution.getCbuildRunFile}` | .../DualCore/DualCore+FRDM-K32L3A6.cbuild-run.yml |
| `${command:cmsis-csolution.getDeviceName}`    | K32L3A60VPJ1A |
| `${command:cmsis-csolution.getDfpName}`       | NXP::K32L3A60_DFP@19.0.0 |
| `${command:cmsis-csolution.getDfpPath}`       | .../NXP/K32L3A60_DFP/19.0.0  |
| `${command:cmsis-csolution.getSolutionFile}`  | .../DualCore/HelloWorld.csolution.yml |

## Examples

### pyOCD

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

### Arm Debugger

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
            "cmsisPack": "${command:cmsis-csolution.getDfpPack}",
            "deviceName": "${command:cmsis-csolution.getDeviceName}",
        }
    ]
}
```

### Programmer

ToDo show usage of command-line programmer (i.e. STCube Programmer)

### Debug server

ToDo show usage of Cortex Debug configured for JLink

### Use µVision for debugging

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
                "${command:cmsis-csolution.getSolutionFile}"
            ],
            "problemMatcher": []
        }
    ]
```

!!! Note
    This only works in Windows environments with µVision installed on the local machine.

