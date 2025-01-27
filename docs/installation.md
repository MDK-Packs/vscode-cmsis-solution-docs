# Setup

<!-- markdownlint-disable MD036 -->

The **Keil Studio Pack** extension pack is a set of extensions that you can use to work with CMSIS solution projects.
It also contains the CMSIS Solution extension.

1. In Visual Studio Code, open the **Extensions** view and enter "Keil Studio Pack" in the search bar.
2. Click the Install button to start the installation.
3. Once finished, the CMSIS View icon appears on the activity bar.

You can [create your first application](./create_app.md) or [download an example project](#find-an-example-project)
to verify the correct operation of the IDE.

!!!Note
    If you do not wish to install the whole suite of extensions, you can install the CMSIS Solution extension standalone.
    In this case, search for "CMSIS Solution"

## Find an example project

The [CMSIS boards list](https://www.keil.arm.com/boards/) contains many examples that can be used to verify the correct
operation of the extension. The following demonstrates how to use an example based on the
[NXP FRDM-K32L3A6 development board](https://www.keil.arm.com/boards/nxp-frdm-k32l3a6-989d2e5/projects/). Please adapt
to your development board.

1. In your browser, open the [CMSIS boards list](https://www.keil.arm.com/boards/).
2. In the search bar, enter "frdm-k32" for example. Alternatively, you may search for a board using the filters
   **Vendor** and **Core**.
3. In the list, click on **FRDM-K32L3A6**.
4. The board page opens on the **Projects** tab. This tab shows the list of available example projects.
5. Enter "hello" in the search bar.
6. Select **Open in Keil Studio for VS Code** in the **Get Project** drop-down to download and open the example directly
   to your computer.
   ![Download and open hello example in VS Code](./images/frdm-hello.png)
7. Visual Studio Code will ask for permissions to open the URI:  
   ![Allow extension to open URI](./images/allow-open.png)  
   Click **Open**.
8. Next, select a download and unzip location.
9. Finally, Visual Studio Code ask to open the unzipped folder, to open it in a new window, or to add it to the workspace.  
   ![Open the unzipped folder](./images/open-folder.png)  
   It is recommended to open the folder in a new window.

Once opened, you can continue to [build](./build.md) and [debug](./debug.md) the example project.
