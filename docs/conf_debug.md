# Configure Run and Debug

When using the CMSIS-Toolbox 2.9, the [Run and Debug Management](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#run-and-debug-management) file `*.cbuild-run.yml` provides all information to configure programmers or debuggers.
With this information the **CMSIS Solution** extension generates the [`launch.json`](https://code.visualstudio.com/docs/editor/debugging) and [`tasks.json`](https://code.visualstudio.com/docs/editor/tasks) configuration files for the
run and debug features of VS Code.

!!! Note
    The generation of the [`launch.json`](https://code.visualstudio.com/docs/editor/debugging) and [`tasks.json`](https://code.visualstudio.com/docs/editor/tasks) files is enabled when the *csolution project* contains a [`target-set:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-Input-Format/#target-set) node. Using `target-set:` uses the *cbuild* command option `--active` to select the configuration.  The option `--context-set` and the file `*.cbuild-set.yml` is no longer used.

In VS Code, there are two debug request modes that can be configured in `launch.json`:

- **Launch** starts a debug session and typically stops at the *main* function.
- **Attach** connects a debug session to a running system.

## CMSIS View - Action buttons

![CMSIS View Action buttons](./images/CMSIS-View-ConfDebug.png)

The CMSIS View offers these action buttons:

- **Load & Run** a *csolution* application which downloads and starts the application images in the target.
- **Load & Debug** a *csolution* application which downloads the application images and starts the debugger.
- **Manage Solution** configures the debug setup with the `target-set:` node. It also supports multiple configurations using a `set:` name.

The action button:

- **Load & Run** executes from `tasks.json` the command `CMSIS Load+Run`.
- **Load & Debug** executes from `launch.json` the first section with `"request": "launch"` and `cmsis:`. If this is not present it uses from `tasks.json` the command `CMSIS Load+Debug`.

Further commands are available under `...`:

- **Load** executes from `tasks.json` the command `CMSIS Load`.
- **Erase** executes from `tasks.json` the command `CMSIS Erase`.
- **Run** executes from `tasks.json` the command `CMSIS Run`.

## Run and Debug - Request

The **Run and Debug View** in VS Code connects to the target using the request selection shown below.

![Debug View Debugger request](./images/Debug-View-ConfDebug.png)

The **CMSIS Solution** extension handles multiple processor cores using one debug connection for each core.

![Generate launch.json and tasks.json](./images/multicore-debug.png)

## Example

The following `*.csolution.yml` file is configured for a CMSIS-DAP Debugger as shown below. Refer to the CMSIS-Toolbox users guide for details on [`target-set`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-Input-Format/#target-set).

```yml
solution:
    :
  target-types:
    - type: MyBoard_ROM                       # My evaluation kit (Execution from ROM)
      board: B-U585I-IOT02A                   # Board name as defined by the pack
      target-set:
        - set:                                # default configuration
          debugger:
            name: CMSIS-DAP                   # uses CMSIS-DAP
```

The related `*.cbuild-run.yml` file contains the information for the debugger setup. The **CMSIS Solution** extension uses this information with a template file for a debug adapter (in this case for CMSIS-DAP) to update the configuration information in `launch.json` and `tasks.json`.

![Generate launch.json and tasks.json](./images/configure-debug-run.png)

ToDo: add the generated launch.json + tasks.json from this example

## User Modifications to `launch.json`

By default, the **CMSIS Solution** extension updates the `launch.json` file to reflect the settings in the *csolution project*. Sometimes the user needs control over settings. The `cmsis:` - `updateConfiguration:` value in the `launch.json` file controls the update. Remove `auto` to manually control the settings and this section.

```json
            "cmsis": {
                "pname": cm33_core0
                "target-type": MCXN947 
                "updateConfiguration": auto     // without auto, this section is not modified
```

## Template Files

Template files for various debug adapters are included in the installation. For reference the template files are provided in the [Debug Adapter Registry](https://github.com/Open-CMSIS-Pack/debug-adapter-registry).

A template file in `*.json` format contains the following sections:

```json
    "launch":                           // section for launch.json
        "singlecore-launch":            // debugger launch request for single-core system
        "singlecore-attach":            // debugger attach request for single-core system
        "multicore-start-launch":       // debugger launch request for the start processor in multi-core system. 
        "multicore-start-attach":       // debugger attach request for the start processor in multi-core system. 
        "multicore-other":              // debugger attach request for other processors in multi-core system.
    "tasks":                            // section for tasks.json
        "label": "CMSIS Load+Run",      // command "CMSIS Load+Run"  
        "label": "CMSIS Run",           // command "CMSIS Run"
        "label": "CMSIS Load",          // command "CMSIS Load"
        "label": "CMSIS Erase",         // command "CMSIS Erase"
```

The template files are processed with the [Eta](https://eta.js.org/) template engine. It inserts data of the `*.cbuild-run.yml` file into the various sections of the template file using placeholders listed in the table below. Each section is processed depending on the system type.

Placeholder       | Description
:-----------------|:----------------
`template`        | Absolute path to the base directory of the template file. Used to access to additional files
`solution_folder` | Relative path from the workspace folder to the directory that stores the `*.csolution.yml` file
`device_name`  | From `*.cbuild-run.yml`: value of [`device:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#file-structure-of-cbuild-runyml)
`target_type`  | From `*.cbuild-run.yml`: value of [`target-type:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#file-structure-of-cbuild-runyml)
`start_pname`  | From `*.cbuild-run.yml`: value of [`start_pname:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#debugger)
`image_files`  | From `*.cbuild-run.yml`: value list of [`output:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#output) with `image` information
`symbol_files` | From `*.cbuild-run.yml`: value list of [`output:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#output) with `symbols` information
`ports`        | From `*.cbuild-run.yml`: value list of [`gdbserver:`](https://open-cmsis-pack.github.io/cmsis-toolbox/YML-CBuild-Format/#gdbserver)