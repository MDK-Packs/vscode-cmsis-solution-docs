# Run external tools

VS Code uses the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and [tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files to integrate with external tools. The following section shows how to configure these files for typical use cases.

## Variables

VS Code supports [variable substitution](https://code.visualstudio.com/docs/editor/variables-reference) in the [Debugging](https://code.visualstudio.com/docs/editor/debugging) and [Tasks](https://code.visualstudio.com/docs/editor/tasks) configuration files and selected settings. Variable substitution uses the `${variableName}` syntax, for example in `launch.json` and `tasks.json` files.
In addition to the [VS Code built-in variables](https://code.visualstudio.com/docs/editor/variables-reference), the CMSIS Solution extension provides the following variables.

| Variable  | Description |
|:----------|:------------|
| `${command:cmsis-csolution.getBinaryFile}`     | The path and name of the first ELF/DWARF file available for the Active Target |
| `${command:cmsis-csolution.getBinaryFiles}`    | The paths and names of the ELF/DWARF files (comma separated) available for the Active Target |
| `${command:cmsis-csolution.getBoardName}`      | The board name for the Active Target as specified in the csolution.yml |
| `${command:cmsis-csolution.getBspName}`        | The Board Support Pack (BSP) for the Active Target |
| `${command:cmsis-csolution.getBspPath}`        | The path to the content of the BSP for the Active Target |
| `${command:cmsis-csolution.getCbuildRunFile}`  | The path to the cbuild-run.yml file for the Active Target |
| `${command:cmsis-csolution.getDeviceName}`     | The device name for the Active Target as specified in the csolution.yml |
| `${command:cmsis-csolution.getDfpName}`        | The Device Family Pack (DFP) for the Active Target |
| `${command:cmsis-csolution.getDfpPath}`        | The path to the content of the DFP for the Active Target |
| `${command:cmsis-csolution.getProcessorName}`  | The name of the processor for the Active Target; for multi-processor configurations start-pname |
| `${command:cmsis-csolution.getSolutionFile}`   | The path to the csolution.yml file for the Active Solution |

!!! Note
    - Active Solution refers to the *csolution project* that is currently loaded.
    - Active Target refers to the target that is currently selected in the [Manage Solution](./manage_settings.md) view.

### Substitution examples

The following table illustrates the variable substition using the [DualCore csolution example](https://github.com/Open-CMSIS-Pack/csolution-examples/tree/main/DualCore). Note that `...` stands for the absolute path on the host computer that stores the *csolution project* or the [CMSIS pack content](https://open-cmsis-pack.github.io/cmsis-toolbox/installation/#environment-variables).

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

<!--### Programmer

ToDo show usage of command-line programmer (i.e. STCube Programmer)

### Debug server

ToDo show usage of Cortex Debug configured for JLink-->

### Use µVision for debugging

The [µVision debugger](https://developer.arm.com/documentation/101407/0541/Debugging) offers advanced debug features such as
Event Recorder and Component Viewer to analyze applications.

To call µVision with the *csolution project* that you are using in VS Code, add the following task to the `.vscode\tasks.json`  file. The `command:` is the path to the µVision executable on your computer.

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
