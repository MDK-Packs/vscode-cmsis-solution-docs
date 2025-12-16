# Work with CMSIS solutions

This section explains how to create a *CMSIS solution-based project* that is using CMSIS-Packs.

In the ![CMSIS view](./images/CMSISView.png) **CMSIS** view, click **Create a New Solution**. If you already have a
solution opened, use the menu (**...**) item **Create a Solution**.

![Create New Solution](./images/CreateNewSolution.png)

The **Create new solution** dialog allows to start projects based on a **Target Board** or **Target Device** selection.

Examples, templates, and reference applications depend on the selected board or device and on installed CMSIS-Packs.

- [**Examples**](#examples) are created for a specific hardware or evaluation board. These are typically
  complete projects that directly interface with board and device peripherals.

- [**Reference applications**](#reference-applications) use defined interfaces (APIs) and are therefore
  hardware agnostic. These projects require the installation of related CMSIS-Packs and additional software layers for
  an evaluation board.

- [**Templates**](#templates) are stub projects that help you getting started. Some CMSIS-Packs may contain
  device-specific templates.

- [**GitHub repositories**](#github-repositories) may contain projects showcasing a specific use case. These repos can
  be cloned directly into VS Code. The **Source Control** view ![Source control icon](./images/SourceControlView.png)
  helps maintaining these repos.

Further settings include:

- The **Solution Sub Folder** is typically a sub-directory in your workspace.

- The **Solution Base Folder** specifies your workspace location that may contain multiple projects.

- With **Initialize Git repository** the related `.gitignore` file is created.

- **Show project opening options** allows you to open the solution a new instance of VS Code. By default, it is loaded
  into the current VS Code instance.

## Examples

1. Click the **Target Board (Optional)** drop-down list.
2. Enter a search term tp filter the list and then select your board. The details of the selected board are displayed.
3. Click **Select**.

Next, select the example project. There are two types of example projects (available either from **Local** packs and/or
from the **Web**):

- **Csolution Examples** are using Keil Studio's native project format.

- **uVision Examples** are in `*.uvprojx` format and are converted automatically.

To verify the Keil Studio installation, select a **Blinky** project for example.

Specify a **Solution Base Folder** and click **Create**.

!!! Note
    First time users may need to confirm that the **Arm Tools Environment Manager** extension can automatically
    activate the workspace and download the tools specified in the `vcpkg-configuration.json` file included in a
    project.

A typical Blinky example includes a `REAMDE.md` file that contains valuable information about the hardware setup and
specific tasks that need to be done before working with the target board:

![Alif E7 Blinky-HP example](./images/blinky-hp.png)

Continue to [build the project](./build_run.md).

## Reference applications

**Reference applications** show the usage of middleware, software libraries, and custom code that can run on many
different target hardware boards. Examples display only if you selected a board and a software layer is available for
that board. Reference applications are not dependent on specific hardware. You can deploy them to various evaluation
boards using additional software layers that provide driver APIs for specific target hardware. Layers are provided
using CMSIS-Packs.

Reference applications are available with these CMSIS-Packs:

- [MDK-Middleware](https://www.keil.arm.com/packs/mdk-middleware-keil/overview/): use software components for IPv4 and
  IPv6 networking, USB Host and Device communication, and file system for data storage.

- [SDS Framework](https://www.keil.arm.com/packs/sds-arm/overview/): record real-world data off a device and playing it
  back on Arm Virtual Hardware.

- [LiteRT](https://www.keil.arm.com/packs/tensorflow-lite-micro-tensorflow/overview/): demonstrates the fundamental
  integration and usage of the LiteRT stack for ML inference on a microcontroller.

!!! Attention
    You need to have the CMSIS-Packs installed before you can create a new reference application. Please follow the
    instruction for [installing packs](./installation.md#pack-installation).

### Configuration

Reference applications use
[software layers](https://open-cmsis-pack.github.io/cmsis-toolbox/build-overview/#software-layers) that help scaling
example projects to many different target boards. To be able to use the selected board with the reference application,
you need to [configure the solution](#configure-a-solution) and select an appropriate layer.

More information about the layer requirements and other configuration options can be found in the documentation:

- [MDK-Middleware](https://arm-software.github.io/MDK-Middleware/latest/General/index.html)
- [SDS Framework Documentation](https://arm-software.github.io/SDS-Framework/main/index.html)

Continue to [build the project](./build_run.md).

## Templates

Templates help you to get started without application-specific code.

- **Blank solution**: Start a project from scratch with an empty `main.c` file and the CMSIS device startup component
  selected

- **TrustZone solution**: If the board or device that you selected is compatible, you can use TrustZone and define
  whether projects in the solution use secure or non-secure zones

Continue to [build the project](./build_run.md).

<!--
## Project contents

Once you have selected an example/template/reference application, the solution is created automatically. If a uVision
example is converted, check the **Output** tab. Conversion errors and warnings are displayed in the **CMSIS Solution**
category. You can also check the `uv2csolution.log` file.

The following files are created for the solution:

- A `<solution_name>.csolution.yml` file.

- One or more `<project_name>.cproject.yml` files, each available in a separate folder.

- A `cdefault.yml` file containing default toolchain setting for the selected toolchain.

- A `<solution_name>.cbuild-idx.yml` file which contains overall information for the application.

- A `<solution_name>.cbuild-pack.yml` file listing all the packs that are used by the application. Missing CMSIS-Packs
  are installed automatically.

- A `<solution_name>.cbuild-set.yml` file which specifies the context set of projects, target-types, and build-types
  that are used to generate the application image

- A `<solution_name>+<target_name>.cbuild-run.yml` file which contains a build description of a single `cproject.yml`
  input file for each context.

- A main `<filename>.c` template file for each project.

- A `vcpkg-configuration.json` file to download required tools automatically.

!!! CAUTION
    If you see this warning:
    ![Task errors output](./images/task-errors.png)
    Click **Show output** to configure the solution. You can add board, shield, or socket layers to your reference
    application. You can also select a compiler for reference applications and other solution types.

Depending on the selected example, you might need to [configure the solution](./configuration.md#configure-a-solution)
first.
-->

## GitHub repositories

Nowadays, many projects are available in GitHub repositories. VS Code provides easy access to these repos with the
[built-in Git support](https://code.visualstudio.com/docs/sourcecontrol/overview). The easiest way to do so is to clone
a repository directly in VS Code:

- In the **Explorer** view ![Explorer icon](./images/ExplorerView.png), click **Clone Repository** (you can do the same
  in the **Source Control** view ![Source control icon](./images/SourceControlView.png)).
- Open the **CMSIS** view ![CMSIS view](./images/CMSISView.png) and use the ... menu to choose an example via
  **Select Active Solution from workspace**.
- The related tools and software packs are downloaded and installed.

Continue to [build the project](./build_run.md).

!!! Note
    - You can also download the repository content as a ZIP file. In that case, extract the content and open the
      top-level folder in VS Code (**File - Open Folder...**).
    - Ready-to-run examples are available on [GitHub](https://github.com/Arm-Examples#keil-mdk-version-6-examples).

## Configure a solution

The **Configure Solution** view opens automatically, if:

- Your solution has a `select-compiler:` node, but no `compiler:` node is set in the `csolution.yml` file, or
- You are working with a reference application that requires the configuration of a software layer.

![Configure a solution](./images/configure-solution.png)

- Click **Next** to display the different options available.

- You can indicate where the layers should be copied to in the **Board-Layer**, **Shield-Layer**, and **Socket-Layer**
  fields. Click **Default** to reset the paths to their default values. If there are no compatible layers, errors display.

- If no compiler is set for the reference application, **Select Compiler** displays under the layers selection and shows the
  compilers available in your environment. Select a compiler. For example, AC6 or GCC.

- If you are working with another solution type, only **Select Compiler** displays. Select a compiler.

- Click **OK**.

For reference applications only, a `Board.clayer.yml` file, a `Shield.clayer.yml` file, or a `Socket.clayer.yml` file, along
with other files that make up the layer, are added in the folders that you selected. The files are available from the
**Explorer** view. The `.clayer.yml` files come from the CMSIS-Pack. Layers are automatically added in the `csolution.yml`
file of your solution under `target-types: variables:` for the active target.

For all solution types, the compiler is added with the `compiler:` key in the `csolution.yml` file.

!!! Note
    - Not all Board Support Packs (BSPs) have board layers.
    - Not all layers are compatible with the connections that your reference application requires.
    - The CMSIS-Packs which contain reference applications and layers generally provide an `Overview.md` file where the
      connections are detailed.

## Software components

A [software component](https://open-cmsis-pack.github.io/cmsis-toolbox/CreateApplications/#software-components)
encapsulates a set of related functions. The **Software Components** view shows all the software components selected in
the active project of a solution.

You can:

- Modify the software components of the project.

- Manage the dependencies between components for each target type defined in your solution, or for all the target types at
  once.

### Software Components view

Open the **CMSIS view** and click ![Manage software components](./images/software-components-icon.png) to open the
**Software Components** view:

![The 'Software Components' ](./images/software-components-view.png)

You can:

1. Switch between *components* and *software packs*.
2. View only components that are *part of the csolution* or components from *all installed packs*.
3. Set the *context* for which the component selection applies (including layers).
4. *Select/remove* software components.
5. View *more information* about the component (name, pack, version, and description).
6. Select different *variants* of a component.
7. Open *related documentation*.

<!--
Layer icons ![Layer icon](./images/layer-icon.png) indicate which components are used in layers. In the current version,
layers are read-only, so you cannot select or clear them. Click the layer icon of a component to open the `*.clayer.yml`
file or associated files.

## Modify the software components in your project

You can add components from all the packs available, not just the packs that are already selected for a project.

### Modify the context displayed

- In the **Project** drop-down list, select the project for which you want to modify software components.

- In the **Target** drop-down list, select a specific target type. If you want to modify all the target types at once,
  select **All Targets**. Note that you might have only one target.

- In the **Software packs** drop-down list, you can filter on the components available from the packs listed in your
  solution with the **Solution: &lt;Solution-name&gt;** option. You can display the components from all installed packs with
  the **All installed packs** option.

### Select components

Check that the **All** toggle button is selected to display all the components available. Switch to **Selected** to display
only the components that are already selected.

Use the checkboxes to select or clear components as required. For some components, you can also select a vendor, variant,
or version. The `cproject.yml` file is automatically updated.
-->

#### Validation

In the **Software Components view**, you can manage the dependencies between components and solve validation issues.
Issues are highlighted with a yellow exclamation mark icon ![Issue icon](./images/issue-icon.png).

![Validation errors](./images/validation-error.png)

If there are validation issues:

1. Either click on ![Issue icon](./images/issue-icon.png) and select the issue in the pop-up box (a) or
2. Click the "Resolve" button for access to the pop-up box (a).
3. Once a components with validation issues is opened, you can use the "eye" icon to see which component is
   missing/affected (b).
4. Use the "Apply" button to select the missing components (only available if there is no choice between different
   components available).

When done, don't forget to **Save** the changes!
