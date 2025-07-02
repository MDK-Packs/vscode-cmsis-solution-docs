# User Interface

The **CMSIS Solution** extension provides the Keil Studio GUI for project management and build tools with the
[CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/). Combined with other Arm and third-party extensions,
it implements a powerful embedded development environment.

## Overview

![CMSIS view](./images/solution-outline.png)

The GUI consists of these elements:

### 1. Dedicated views from the side bar

| View | Description |
|:----:|-------------|
| ![Explorer view](./images/ExplorerView.png) | [**Explorer** view](https://code.visualstudio.com/docs/getstarted/userinterface#_explorer-view) lists all local files. |
| ![Search view](./images/SearchView.png) | **Search** view enables [search/replace](https://code.visualstudio.com/docs/editing/codebasics#_search-across-files) across all files. |
| ![Source Control view](./images/SourceControlView.png) | [**Source Control** view](https://code.visualstudio.com/docs/sourcecontrol/overview) allows you to work with git. |
| ![Extensions view](./images/ExtensionsView.png) | [**Extensions** view](https://code.visualstudio.com/docs/configure/extensions/extension-marketplace) lets you work with VS Code extensions. |
| ![Run and Debug view](./images/RunDebugView.png) | **Run and Debug** view switches the GUI to a dedicated [debug view](./debug.md#run-and-debug-view). |
| ![CMSIS view](./images/CMSISView.png) | [**CMSIS** view](#2-main-area-of-the-cmsis-view) is the main view for working with CMSIS solution-based projects. |

!!! Note
    The ordering of the icons may be different in your VS Code environment.

### 2. Main area of the **CMSIS** view

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

### 3. Actions available through the **CMSIS** view

| Action | Description |
|:------:|-------------|
| ![Build solution](./images/build-icon.png) | [**Build solution**](./create_app.md#build) calls the compiler toolchain and builds the solution. |
| ![Load and Run Application](./images/run-icon.png) | [**Load & Run application**](./create_app.md#load-and-run) flashes the binary onto the target and starts the application. |
| ![Load & Debug application](./images/debug-icon.png) | [**Load & Debug application**](./debug.md) flashes the binary onto the target and starts a debug session. |
| ![Open csolution.yml file](./images/openFile.png) | **Open csolution.yml file** opens the CMSIS solution YML file for editing. |
| ![Manage Solution Settings](./images/ManageSWComonents.png) | [**Manage Solution Settings**](./manage_settings.md) allows you to manage the solution settings. |
| ![Views and more actions](./images/more-actions-icon.png) | Shows further views and more actions. |

### 4. Main area icons

Depending on the file and the context, various icons may appear:

| Action | Description |
|:------:|-------------|
| ![clangd information active](./images/clangdInfo.png) | IntelliSense is active for this cproject file. |
| ![Open file](./images/openFile.png) | Open the file. |
| ![Manage software components](./images/ManageSWComonents.png) | Manage the software components of the cproject file. |
| ![Add groups or files](./images/AddGroupsFiles.png) | Add groups or files to the cproject file. |

### 5. Status bar

The VS Code status bar displays information about the status of your development environment and the project. The number of extensions installed might vary.

- Status message of the clangd extension (used for IntelliSense).

- You can inspect errors and warnings for a context set. For active projects in the context set, errors and warnings display
  when you move your cursor over the **Context Set** in the status bar. The indicator is red for errors and yellow in case
  of warnings. Click the indicator to open the **Output** tab for the **CMSIS Solution** category. If you previously closed
  the **Manage Solution** view, then this action also re-opens the view.
  ![Context Set errors and warnings](./images/context-set-popup.png)

- The **Arm Tools Environment Manager** extension shows information about the tools installed. Move your mouse over **Arm Tools** to review the list. Click **Arm Tools** to get more options.
  ![Arm Tools](./images/arm-tools.png)

- If you are using licensed Arm tools, the **active license** displays. Click the active license to manage it.

## Available commands

You can access commands to manage your solution and the projects it includes in the following ways:

- From the **CMSIS** view.

- When you right-click the `*.csolution.yml` file from the **Explorer** view.

- When you click the [Context Set status bar item](#5-status-bar).

- When you press Ctrl+Shift+P (Windows and Linux) or Cmd+Shift+P (macOS) to open the Command Palette.

| Command | Description |
|---------|-------------|
| [Create a Solution](./create_app.md) | Create a new *csolution project*.  |
| [Configure Solution](./configuration.md#configure-a-solution) | Set a compiler and add software layers |
| [Manage Solution Settings](./manage_settings.md) | Configure the build context and debug setup. |
| [Manage Software Components](./manage_components.md) | Review, add, or remove software components |
| Run Configuration Generator                            | Open a configuration tools such as CubeMX |
| [Build solution](./create_app.md#build) | Build the solution with the current context set |
| Rebuild solution                         | Rebuild the solution with the current context set |
| [Debug](./debug.md)                      | Debug the solution with the current context set |
| [Run](./create_app.md#load-and-run)      | Run the solution on your target |
| Focus on Solution View                   | Open the CMSIS view |
| Select Active Solution from workspace           | If you have several solutions in your workspace, switch between solutions and select the active solution |
| [Convert µVision project to CMSIS solution](./importuv.md) | Convert uvprojx files to *csolution project* format |
| Refresh (reload packs, update RTE)       | Reload information from all installed packs and run `cbuild setup update-rte` |
| Clean all out and tmp directories        | Clean all out and tmp directories for the active solution |
