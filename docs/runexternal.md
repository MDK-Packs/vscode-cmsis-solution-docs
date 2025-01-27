# Run External Tools

VS Code uses the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and
[tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files to integrate external tools. The following
section shows how to configure these files for typical use cases.

[Variables and commands](#variables-and-commands) provide access to parameters  of the current active *csolution project*.

## Programmer

ToDo show usage of command-line programmer (i.e. STCube Programmer)

## Debug Server

ToDo show usage of Cortex Debug configured for JLink

## Using uVision for Debugging

The [µVision Debugger](https://developer.arm.com/documentation/101407/0541/Debugging) offers advanced debug features such as
Event Recorder and Component Viewer to analyze applications.

To call µVision with the *csolution project* that you are using in VS Code, add to the file `.vscode\tasks.json` the
following task. The `command:` is the path to the uVision executable on your computer.

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

VS Code supports variable and command substitution in [launch.json](https://code.visualstudio.com/docs/editor/debugging) and
[tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files as well as some select settings. In
addition to the [VS Code built-in variables](https://code.visualstudio.com/docs/editor/variables-reference), the CMSIS
Solution extension provides the following commands to access parameters of the current active *csolution project*.

| Command  | Description |
|----------|-------------|
| `cmsis-csolution.getBinaryFile`               | Elf/Dwarf location of currently selected context |
| `cmsis-csolution.getBinaryFiles`              | Elf/Dwarf location of all files in current solution |
| `cmsis-csolution.getBspName`                  | Name and version of the [Board Support Pack (BSP)](https://www.keil.arm.com/boards/) |
| `cmsis-csolution.getBspPath`                  | Path to [Board Support Pack (BSP)](https://www.keil.arm.com/boards/) file of the current active target |
| `cmsis-csolution.getCbuildRunPath`            | Path to `cbuild-run.yml` file |
| `cmsis-csolution.getDeviceName`               | Device name of active target |
| `cmsis-csolution.getDfpName`                  | Name and version of the [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) |
| `cmsis-csolution.getDfpPath`                  | Path to [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) file of the current active target |
| `cmsis-csolution.getHardwareAndToolchainInfo` | Target hardware and toolchain for the active solution |
| `cmsis-csolution.getProcessorName`            | The processor name for the currently selected context |
| `cmsis-csolution.getSolutionPath`             | Path to active solution file |
| `cmsis-csolution.getTargetPack`               | The [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) for the currently selected context |

### Substitution examples

tbd