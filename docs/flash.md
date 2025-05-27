# Load and Run

!!! Attention
    Make sure that your project is set up correctly for [run and debug](./configuration.md#configure-run-and-debug).

Make sure that your target is connected, before loading the application onto it. You can use `pyOCD` to verify target
connectivity.

1. Open a **Terminal**, and enter `pyOCD list` to check attached hardware:
   ![Check connected hardware with pyOCD](./images/pyOCDlist.png)
2. In the **Solution** outline header, click ![Run icon](./images/run-icon.png). This executes the "load and run"
   command that flashes the project onto the target and issues a reset to start the application.
3. To verify that the step has run correctly, check the **Terminal** output:
   ![Flash download output](./images/flash-dwnl-output.png)

!!! Notes
    - When you have several solutions in one folder, VS Code ignores the `tasks.json` and `launch.json` files that
    you created for each solution. Instead, VS Code generates new JSON files at the root of the workspace in a
    `.vscode` folder and ignores the other JSON files. As a workaround, open one solution first, then add other solutions to your workspace with the **File** > **Add Folder to Workspace** option.
    - If you are using a multicore device and you did not specify a `"processorName"` in the `launch.json` file, select the
      appropriate processor for your project in the **Select a processor** drop-down list at the top of the window.
