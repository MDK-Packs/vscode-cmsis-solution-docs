# Run external tools

VS Code uses the [launch.json](https://code.visualstudio.com/docs/editor/debugging) and [tasks.json](https://code.visualstudio.com/docs/editor/tasks) configuration files to integrate with external tools. The following section shows how to configure these files for typical use cases.

## Variables

VS Code supports [variable substitution](https://code.visualstudio.com/docs/editor/variables-reference) in the [Debugging](https://code.visualstudio.com/docs/editor/debugging) and [Tasks](https://code.visualstudio.com/docs/editor/tasks) configuration files and selected settings. Variable substitution uses the `${variableName}` syntax, for example in `launch.json` and `tasks.json` files.
In addition to the [VS Code built-in variables](https://code.visualstudio.com/docs/editor/variables-reference), the CMSIS Solution extension provides the following variables.

| Variable  | Description |
|:----------|:------------|
| `${command:cmsis-csolution.getActiveTargetSet}`| Get name of active run and debug configuration (format: target-type@set) |
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

### Examples

#### Arm Debugger

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

## CMSIS tools environment

The CMSIS Solution extension exports the resolved tools environment of the active solution for use by external tools
and AI agents. The generated file is located at `<solution-dir>/.cmsis/tools-environment.yml`. It is created or
updated after the extension resolves the environment and processes the solution.

The file contains only the `PATH` entries and environment variables contributed or used by the Arm extensions and
the Arm Tools Environment Manager. Unrelated entries inherited from the host process are omitted. Entries in
`environment.path` are listed in their resolved precedence order. When launching a process, prepend them to `PATH` in
the same order.

The following example is shortened and uses generic paths:

```yml
cmsis-tools-environment:
  version: 1.0.0
  generated-by: arm.cmsis-csolution version 1.70.1
  solution: ../Hello-Ethos-U65.csolution.yml
  environment:
    path:
      - <user>/.vscode/extensions/arm.cmsis-csolution/tools/cmsis-toolbox/bin
      - <user>/.vcpkg/artifacts/<hash>/compilers.arm.armclang/6.24.0/bin
    variables:
      CMSIS_PACK_ROOT: <user>/AppData/Local/Arm/Packs
      AC6_TOOLCHAIN_6_24_0: <user>/.vcpkg/artifacts/<hash>/compilers.arm.armclang/6.24.0/bin
  tools:
    - name: CMSIS-Toolbox
      version: 2.14.1
      origin: built-in
      provider:
        type: vscode-extension
        id: arm.cmsis-csolution
      directory: <user>/.vscode/extensions/arm.cmsis-csolution/tools/cmsis-toolbox/bin
      manual: https://open-cmsis-pack.github.io/cmsis-toolbox/
    - name: compilers.arm.armclang
      version: 6.24.0
      origin: installed
      provider:
        type: vcpkg
        id: arm.environment-manager
      directory: <user>/.vcpkg/artifacts/<hash>/compilers.arm.armclang/6.24.0
```

### File structure

`cmsis-tools-environment:` | Content
--- | ---
&nbsp;&nbsp; `version:` | Version of the tools environment file format.
&nbsp;&nbsp; `generated-by:` | Extension ID and version that generated the file.
&nbsp;&nbsp; `solution:` | Path to the active `*.csolution.yml` file, relative to the generated file.
&nbsp;&nbsp; [`environment:`](#environment) | Resolved path entries and environment variables.
&nbsp;&nbsp; [`tools:`](#tools) | Tools provided by VS Code extensions or installed with vcpkg.

#### `environment:`

The `environment:` node contains the environment required to invoke the resolved tools.

`environment:` | Content
--- | ---
&nbsp;&nbsp; `path:` | List of directories in executable lookup order. Prepend the entries to the process `PATH` in the listed order.
&nbsp;&nbsp; `variables:` | Map of resolved CMSIS and tool-specific environment variables. `PATH` is not repeated in this map.

The `variables:` map includes `CMSIS_PACK_ROOT`, `CMSIS_COMPILER_ROOT`, variables configured with the CMSIS Solution
`Environment Variables` setting, and variables contributed by the Arm Tools Environment Manager. An entry is present
only when it applies to the resolved environment.

#### `tools:`

The `tools:` node contains one entry for each selected tool or tool suite. If built-in and installed tools provide the
same command, only the tool whose directory occurs first in `environment.path` is listed.

`tools:` | Content
--- | ---
`- name:` | Human-readable built-in tool name or canonical vcpkg package name.
&nbsp;&nbsp;&nbsp;&nbsp; `version:` | Tool or package version. This element can be omitted for an installed tool when its version cannot be resolved.
&nbsp;&nbsp;&nbsp;&nbsp; `origin:` | Tool origin: `built-in` or `installed`.
&nbsp;&nbsp;&nbsp;&nbsp; [`provider:`](#provider) | Provider type and identifier.
&nbsp;&nbsp;&nbsp;&nbsp; `directory:` | Tool directory. For a recognized vcpkg artifact, this is the package version root.
&nbsp;&nbsp;&nbsp;&nbsp; `manual:` | Documentation URL provided for a built-in tool.

##### `provider:`

`provider:` | Content
--- | ---
&nbsp;&nbsp; `type:` | Provider type: `vscode-extension` for a bundled tool or `vcpkg` for an installed tool.
&nbsp;&nbsp; `id:` | ID of the VS Code extension that provides or manages the tool.

!!! Attention
    The extension generates and updates `.cmsis/tools-environment.yml`; do not edit it manually. Environment variable
    values are stored as plain text. Do not configure credentials or other secrets as CMSIS Solution or vcpkg
    environment variables.

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
