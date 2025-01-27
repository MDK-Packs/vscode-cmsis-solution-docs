# Quick start

The CMSIS Solution is an extension for Visual Studio Code that offers a GUI for the underlying
[CMSIS-Toolbox](https://open-cmsis-pack.github.io/cmsis-toolbox/) project management and build tools. Together with other
extensions provided by Arm and third parties, this results in a powerful embedded development environment.

This quick start guide gives you an overview of the project management capabilities in the [CMSIS view](#cmsis-view)
and shows how the [status bar](#status-bar) helps to understand the project and environment set up.

## Available commands

You can access commands to manage your solution/project when you take the following actions:

- Directly from the [**CMSIS**](#cmsis-view) view.

- When you right-click the `*.csolution.yml` file from the **Explorer** view.

- When you click the [context set status bar item](#status-bar).

- When press CTRL+Shift+P (CMD+Shift+P on MacOS).

| Command | Description |
|---------|-------------|
| [Manage Solution Settings](./manage_settings.md) | Set a context for your solution |
| [Build solution](./build.md)                     | Build the solution with the current context set |
| Clean all out and tmp directories        | for the active solution |
| [Configure Solution](./configuration.md#configure-a-solution) | Set compiler and add layers |
| [Convert µVision project to CMSIS solution](./importuv.md) | Convert uvprojx files to CMSIS solution format |
| [Create a Solution](./create_app.md)     | Start from scratch |
| [Debug](./debug.md)                      | the solution with the current context set |
| Focus on Solution View                   | Shows the CMSIS view |
| [Manage software components](./manage_components.md) | Review, add, and remove software components |
| Rebuild solution                         | Rebuild the solution with the current context set |
| Refresh (reload packs, update RTE)       | Reload information from all installed packs and run `cbuild setup update-rte` |
| [Run](./flash.md)                        | Flash and run the solution on your target |
| Run Generator                            | Open generator program with the current target |
| Select solution from workspace           | Set current solution if you have several of them in your workspace |

## CMSIS View

The CMSIS view (![CMSIS icon](./images/cmsis-icon.png)) shows the content of the active projects in the solution. Each
project contains configuration settings, source code files, build settings, and other project-specific information. The
extension uses these settings and files to manage and build a software project for a board or device.

![CMSIS view](./images/solution-outline.png)

The main area shows:

- **Groups and files** are added to the project by the user.

- **constructed-files** contains generated files such as the `RTE_Components.h` header file for each context.

- **linker** contains a linker script file and a &lt;regions&gt;.h file (or other user-defined header files).

- **Components** shows the software components selected for the project with their source files, user code templates, and
  APIs. Click the files to open them in the editor. Click the book icon of a component to open the related documentation.
  If you are using a generator to configure your device or board, then a **Run Generator** option is available to start a
  generator session.

- **Layer Type** (if available): The software layers in the project with their source files, preconfigured software
  components, and configuration files.

## Status bar

The Visual Studio Code status bar displays information about the status of your development environment and the project.

Depending on the number of installed extensions, you see something like the following:

![Status bar](./images/status-bar.png)

- If you have a development board attached, the **connected hardware** is shown via the **Arm Device Manager** extension.
  Click to open the extension.

- Using the **Arm Debugger** extension, the **current debug configuration** is displayed.

- You can inspect errors and warnings for a context set. For active projects in the context set, errors and warnings display
  when you move your cursor over the **Context Set** in the status bar. The indicator is red for errors and yellow in case
  of warnings. Click the indicator to open the **Output** tab for the **CMSIS Solution** category. If you previously closed
  the **Manage Solution** view, then this action also re-opens the view.  
  ![Context Set errors and warnings](./images/context-set-popup.png)

- The **Arm Environment Manager** extension shows information about the number of installed tools. Hover over to review the
  list. Click it to get further options.  
  ![Arm Tools](./images/arm-tools.png)

- If you are using licensed Arm tools, the active license is shown. Click it to manage the license.
