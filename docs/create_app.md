# Create an embedded project

This chapter explains how to create a CMSIS solution-based application.

## Create new solution

In the **CMSIS** view, click **Create a New Solution** to open the **Create Solution** view.

!!! Note
    If you already have a solution opened in your workspace and want to create a new one in the same workspace, move your
    cursor over the three dots **...** in the **CMSIS** view, then **Create new solution**.

Click the **Target Board** drop-down list. Enter a search term, and then select a board. The details of the board that you
selected are shown.

![Picker](./images/hardware-picker.png)

Click **Select**. By default, the **Target Device** drop-down list and **Target Type** field show the name of the device
mounted on the board that you selected.

In the **Target Type** field, you can customize the name of the target that is used to deploy the solution. This is
displayed in the **Manage Solution** view and added to the `target-types:` section of the `<solution_name>.csolution.yml` file.

!!! Note
    Alternatively, you can directly select a device in the **Target Device** drop-down list, without selecting a board first.

## Select a template, reference application, or example

Depending on the board or device you have chosen, select one of the following options from the drop-down list. If there are
too many examples, enter a search term and then select an example.

### Templates

Templates help you getting started without application-specific code.

- **Blank solution**: starts a project from scratch with an empty `main.c` file and the CMSIS device startup component
  selected.

- **TrustZone solution**: If the board or device that you selected is compatible, you can use TrustZone, and define
  whether projects in the solution use secure or non-secure zones.

### Reference Applications

**Reference applications** show the usage of middleware, software libraries, and custom code that can run on many different
target hardware boards. Examples display only if you selected a board and a software layer is available for the board.
Reference applications are not dependent on specific hardware. You can deploy them to various evaluation boards using
additional software layers that provide driver APIs for specific target hardware. Layers are provided using CMSIS-Packs.

Reference applications are available with the
[MDK-Middleware](https://www.keil.arm.com/packs/mdk-middleware-keil/versions/). These examples show you how to use software
components for IPv4 and IPv6 networking, USB Host and Device communication, and file system for data storage. See
[MDK Middleware Reference Applications](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#mdk-middleware-reference-applications) and the
[MDK-Middleware](https://github.com/arm-software/MDK-Middleware) repository and
[documentation](https://arm-software.github.io/MDK-Middleware/latest/General/index.html) for more details.

Other reference applications that illustrate how to match sensor shields and boards are also available with the Sensor SDK pack. The examples use board and shield layers. See [Sensor Reference Applications](https://github.com/Open-CMSIS-Pack/cmsis-toolbox/blob/main/docs/ReferenceApplications.md#sensor-reference-applications) and the [Sensor-SDK-Example](https://github.com/open-cmsis-pack/Sensor-SDK-Example) repository for more details.

Reference applications that use socket layers are also available. See the [AWS MQTT demo](https://github.com/Arm-Examples/AWS_MQTT_Demo) as an example.

### Csolution Examples

Use a CMSIS solution example. CMSIS solution examples are targeted at a specific board or Fixed Virtual Platform (FVP) model. The examples are fully configured and ready for use.

### µVision Examples

Use a µVision example in `*.uvprojx` format as a starting point. µVision examples are converted automatically.

## Project Name

Once you have selected your solution template, you need to specify a **Project Name**.

If you selected **Blank solution** or **TrustZone solution**, one project for each processor is automatically added (in case
of TrustZone a `secure` and a `non-secure` project)). You can:

- change the project names.
- remove projects.
- decide to add `secure` or `non-secure` zones with the TrustZone drop-down list if the board or device is compatible. By
  default, TrustZone is `off`.

Click **Add Project** to add projects to your solution and configure them. For TrustZone, you can add as many `secure` or
`non-secure` projects as you need for a particular processor.

## Solution Name

In the **Solution Name** field, you can change the name for your solution. This will be used as the `SolutionName.csolution.yml` file name.

## Solution Sub Folder

In the **Solution Sub Folder** field, you can change the name of the subfolder where the solution files are stored.

## Solution Folder

- Click **Browse** next to the **Solution Base Folder** field and choose where to store the solution subfolder using the system
  dialog box.

- With the **Initialize Git repository** checkbox, you can initialize the solution as a Git repository. Clear the checkbox
  if you do not want to turn your solution into a Git repository.

- Select the **Show project opening options** checkbox to decide where to open the solution.

- Click **Create**.

The extension creates the solution and automatically converts examples that are available only in `*.uvprojx` format. If there are conversion errors, check the `uv2csolution.log` file.

Missing CMSIS-Packs are installed automatically.

The following files are created for the solution:

- A `<solution_name>.csolution.yml` file.
- One or more `<project_name>.cproject.yml` files, each available in a separate folder.
- For reference applications only, each `cproject.yml` file contains a `$Board-Layer$` variable.
- For reference applications with sensor shields, each `cproject.yml` file contains a `$Shield-Layer$` variable.
- For reference applications with a socket layer, each `cproject.yml` file contains a `$Socket-Layer$` variable. These
  variables are not yet defined.
- A main `<filename>.c` template file for each project.
- A `vcpkg-configuration.json` file to download required tools automatically.

!!! Attention
    If get this warning issued:  
    ![Task errors output](./images/task-errors.png)  
    Click **Show output** to configure the solution. You may add board, shield, or socket layers to your reference
    application. You can also select a compiler for reference applications and other solution types.

Depending on the selected example, you might need to [configure the solution](./configuration.md#configure-a-solution)
before you can continue with [building](./build.md) the project.
