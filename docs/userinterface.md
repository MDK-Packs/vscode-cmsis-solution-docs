# User Interface

The **CMSIS Solution** extension provides the Keil Studio GUI for project management and build tools with the
[CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/). Combined with other Arm and third-party extensions,
it implements a powerful embedded development environment.

![CMSIS view](./images/solution-outline.png)

The GUI consists of these views:

| View | Description |
|:----:|-------------|
| ![Explorer view](./images/ExplorerView.png) | [**Explorer** view](https://code.visualstudio.com/docs/getstarted/userinterface#_explorer-view) lists all local files. |
| ![Search view](./images/SearchView.png) | **Search** view enables [search/replace](https://code.visualstudio.com/docs/editing/codebasics#_search-across-files) across all files. |
| ![Source Control view](./images/SourceControlView.png) | [**Source Control** view](https://code.visualstudio.com/docs/sourcecontrol/overview) allows you to work with git. |
| ![Extensions view](./images/ExtensionsView.png) | [**Extensions** view](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace) lets you work with VS Code extensions. |
| ![Run and Debug view](./images/RunDebugView.png) | **Run and Debug** view switches the GUI to a dedicated [debug view](./debug.md#debugger-user-interface). |
| ![CMSIS view](./images/CMSISView.png) | [**CMSIS** view](#cmsis-view) is the main view for working with CMSIS solution-based projects. |
| ![Trace and live view](./images/TraceLiveView.png) | [**Trace and Live** view](./debug.md#trace-and-live-view) shows trace and live data during debugging. |

!!! Note
    The ordering of the icons may be different in your VS Code environment.

## CMSIS view

The CMSIS view ![CMSIS icon](./images/cmsis-icon.png) shows the content of the active projects included in the
solution. Each project contains configuration settings, source code files, build settings, and other project-specific
information. The main area of the **CMSIS** view shows:

- **Board** and **device** information and related documentation.
- **Groups and files**: Groups and user files that you add to the project and that you can edit
- **constructed-files**: Contains generated files such as the `RTE_Components.h` header file for each context
- **linker**: Contains a linker script file and a &lt;regions&gt;.h file (or other user-defined header files)
- **Components**: Shows the software components selected for the project with their source files, user code templates, and
  APIs. Click the files to open them in the editor. Click the book icon of a component to open the related documentation.
  If you are using a generator to configure your device or board, then a **Run Configuration Generator** option is available to start a
  generator session.
- **Layer Type** (if available): The software layers in the project with their source files, preconfigured software
  components, and configuration files

### Actions available through the **CMSIS** view

| Action | Description |
|:------:|-------------|
| ![Build solution](./images/build-icon.png) | [**Build solution**](./build_run.md) calls the compiler toolchain and builds the solution. |
| ![Load and Run Application](./images/run-icon.png) | [**Load & Run application**](./build_run.md#load-and-run) flashes the binary onto the target and starts the application. |
| ![Load & Debug application](./images/debug-icon.png) | [**Load & Debug application**](./debug.md) flashes the binary onto the target and starts a debug session. |
| ![Open csolution.yml file](./images/openFile.png) | **Open csolution.yml file** opens the CMSIS solution YML file for editing. |
| ![Manage Solution Settings](./images/ManageSWComonents.png) | [**Manage Solution Settings**](./manage_settings.md) allows you to manage the solution settings. |
| ![Views and more actions](./images/more-actions-icon.png) | Shows further views and more actions. |

### Main area icons

Depending on the file and the context, various icons may appear:

| Action | Description |
|:------:|-------------|
| ![clangd information active](./images/clangdInfo.png) | IntelliSense is active for this cproject file. |
| ![Open file](./images/openFile.png) | Open the file. |
| ![Manage software components](./images/ManageSWComonents.png) | Manage the software components of the cproject file. |
| ![Add groups or files](./images/AddGroupsFiles.png) | Add groups or files to the cproject file. |

### Configuration Wizard

[Configuration Wizard annotations](https://open-cmsis-pack.github.io/Open-CMSIS-Pack-Spec/main/html/configWizard.html)
help creating GUI-like elements in IDEs for configuration files. Using a GUI-like approach makes it easier for the user
to check and adapt configuration files to the application needs.

For files containing configuration wizard annotations, open the GUI view by using the **Open Preview** button
![Open Preview](./images/open-conf-wiz-view-icon.png) in the top right corner of the file window.

The view will be opened next to the original source file. You can switch back using the **Show Source** button
![Open source file view](./images/open-source-file-view-icon.png).

![RTE_Device.h file in configuration wizard view](./images/rte-devce-config-wiz-view.png)

## Status bar

The VS Code status bar displays information about the status of your development environment and the project. The number of extensions installed might vary.

- Status message of the clangd extension (used for IntelliSense).

- You can inspect errors and warnings for the active project when you move your cursor over the **Target Set** in the
  status bar. The indicator is red for errors and yellow in case of warnings. Click the indicator to open the
  **Output** tab for the **CMSIS Solution** category. If you previously closed the **Manage Solution** view, then this
  action also re-opens the view.  
  ![Target Set errors and warnings](./images/target-set-popup.png)

- The **Arm Tools Environment Manager** extension shows information about the tools installed. Move your mouse over **Arm Tools** to review the list. Click **Arm Tools** to get more options.
  ![Arm Tools](./images/arm-tools.png)

- If you are using licensed Arm tools, the **active license** displays. Click the active license to manage it.

## Run and Debug view

Refer to the [Debugger user interface](./debug.md#debugger-user-interface) section for more information.

<!--
!!! Tip
    The [Arm CMSIS Debugger README](https://marketplace.visualstudio.com/items?itemName=Arm.vscode-cmsis-debugger)
    contains a more detailed description of the usage of this view.

The **Run and Debug View** ![Run and Debug view](./images/RunDebugView.png) in Keil Studio connects to the target using
the request selection shown below.

![Debug View Debugger request](./images/run-debug-view.png)

1. Select the core you want to **launch** (start an application) or **attach** to (connect to a running application).
2. Interact with the cores.

### Run and Debug controls

Depending on the target device (number of cores etc.), a similar run and debug control bar will be visible:

![Run and Debug controls](./images/debug-full-controls.png) or

![Run and Debug controls in a multicore environment](./images/debug-full-controls-multicore.png)

The icons enable access to:

| Icon | Action | Description |
|:----:|--------|-------------|
| ![Continue](./images/debug-continue.png) | Continue | Resume normal program execution (up to the next breakpoint). |
| ![Pause](./images/debug-pause.png) | Pause | Inspect code executing at the current location. |
| ![Step over](./images/debug-step-over.png) | Step over | Execute the next statement as a single command without inspecting or following its component steps. |
| ![Step into](./images/debug-step-into.png) | Step into | Enter the next statement to follow its execution line-by-line. |
| ![Step out](./images/debug-step-out.png) | Step out | When inside a function, return to the earlier execution context by completing remaining lines of the current method as though it were a single command. |
| ![Restart](./images/debug-restart.png) | Restart | Terminate the current program execution and start debugging again using the current run configuration. |
| ![Stop](./images/debug-stop.png) | Stop |  Terminate the current debug session. |
| ![Disconnect](./images/debug-disconnect.png) | Disconnect |  Detach debugger from a core without changing the execution status (running/pause). |
| ![Reset](./images/debug-reset-target.png) | Reset | Reset target device. |

## Trace and Live view

The **Trace and Live View** ![Trace and Live view](./images/TraceLiveView.png) contains the **LIVE WATCH** section that
continuously displays the value of an expression while the program is running.  Future versions of this view will also
show trace information.

You can add expressions to the **LIVE WATCH** by:

1. Pressing the `+` sign and entering an expression.
2. Using the context menu item **Add to Live Watch** in the editor or the the **Run and Debug** view.

![Displaying a variable in the LIVE WATCH](./images/lw-counter.gif)
-->
## Available commands

You can access commands to manage your solution and the projects it includes in the following ways:

- From the **CMSIS** view.

- When you right-click the `*.csolution.yml` file from the **Explorer** view.

- When you click the [Context Set status bar item](#status-bar).

- When you press Ctrl+Shift+P (Windows and Linux) or Cmd+Shift+P (macOS) to open the Command Palette.

| Command | Description |
|---------|-------------|
| [Create a Solution](./create_app.md) | Create a new *csolution project*.  |
| [Configure Solution](./create_app.md#configure-a-solution) | Set a compiler and add software layers |
| [Manage Solution Settings](./manage_settings.md) | Configure the build context and debug setup. |
| [Manage Software Components](./create_app.md#software-components) | Review, add, or remove software components |
| Run Configuration Generator                            | Open a configuration tools such as CubeMX |
| [Build solution](./build_run.md) | Build the solution with the current context set |
| Rebuild solution                         | Rebuild the solution with the current context set |
| [Debug](./debug.md)                      | Debug the solution with the current context set |
| [Run](./build_run.md#load-and-run)      | Run the solution on your target |
| Focus on Solution View                   | Open the CMSIS view |
| Select Active Solution from workspace           | If you have several solutions in your workspace, switch between solutions and select the active solution |
| [Convert µVision project to CMSIS solution](./importuv.md) | Convert uvprojx files to *csolution project* format |
| Refresh (reload packs, update RTE)       | Reload information from all installed packs and run `cbuild setup update-rte` |
| Clean all out and tmp directories        | Clean all out and tmp directories for the active solution |
