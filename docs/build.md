# Build a project

Before you can download the application on your target device, you need to build it. There are various ways to trigger
a build.

## From the Explorer view

In the **Explorer** view ![Explorer icon](./images/explorer-icon.png), right-click the `*.csolution.yml` file and
select **Build solution**.

These options are also available in the right-click menu:

- **Rebuild solution**: Cleans the output directories before building the cproject

- **Clean all out and tmp directories**: Cleans the output and tmp directories for the active solution

## From the CMSIS view

In the **CMSIS** view's **Solution** outline header ![CMSIS view](./images/CMSISView.png), click
![Build icon](./images/build-icon.png).

The **Clean all out and tmp directories** and **Rebuild solution** options are also available with
![Views and More Actions icon](./images/more-actions-icon.png).

You can configure a build task in a `tasks.json` file to customize the behavior of the build button. All the examples
on [keil.arm.com](https://www.keil.arm.com) include a `tasks.json` file. See
[Configure a build task](./configuration.md#configure-a-build-task) for more details.

## Build output

After you initiate the build process, a Terminal window opens and displays the build operation:

![Build output in Terminal](./images/build-output.png)

The output directory usually contains an ELF (`.axf`) and a HEX (`.hex`) file.

!!! Note
    If the build fails with an `ENOENT` error, follow the instructions in the pop-up message that displays in the
    bottom right-hand corner to install CMSIS-Toolbox.
