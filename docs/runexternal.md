# Run External Tools

VS Code uses the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and
[tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files to integrate external tools. The following
section shows how to configure these files for typical use cases. [Variables](#variables) provide access to parameters  of
the current active *csolution project*.

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

## Variables

VS Code supports variable substitution in [launch.json](https://code.visualstudio.com/docs/editor/debugging) and
[tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files as well as some select settings. In
addition to the [VS Code built-in variables](https://code.visualstudio.com/docs/editor/variables-reference), the CMSIS
Solution extension provides the following variables to access parameters of the current active *csolution project*.

| Variable | Description | Example value |
|----------|-------------|---------|
| `cmsis-solution.getDfpName` | Name and version of the [Device Family Pack (DFP)](https://www.keil.arm.com/devices/) of the current active target. | ARM::V2M_MPS3_SSE_300_DFP@1.5.0 |
| `cmsis-solution.getBspName` | Name and version of the [Board Support Pack (BSP)](https://www.keil.arm.com/boards/) of the current active target. | ARM::V2M_MPS3_SSE_300_DFP@1.5.0 |
| `cmsis-solution.getDfpPath` | Path to Device Family Pack (DFP) file of the current active target. | |
| `cmsis-solution.getBspPath` | Path to Board Support Pack (BSP) file of the current active target. | |
| `cmsis-solution.getCbuildRunPath` | Path to the CMSIS-Toolbox `*.cbuild-run.yml` file of the current active target. | |