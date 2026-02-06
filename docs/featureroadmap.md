# Roadmap

## Project management

### Project creation and organization

| Feature                                                                   | Description                                                                 |
| ------------------------------------------------------------------------- | --------------------------------------------------------------------------- |
| &#128994; [Project creation](./create_app.md)                             | Create, open, and manage CMSIS solution projects                            |
| &#128994; [Multi-project solution](./create_app.md)                       | Manage multiple related projects within a single CMSIS solution             |
| &#128994; Multi-solution workspace                                        | Manage multiple solutions within one workspace (Timeline: VS Code built-in) |
| &#128994; [Target types](./manage_settings.md)                            | Multiple targets (e.g., HW, models) within one solution                     |
| &#128994; [Build types](./manage_settings.md)                             | Multiple build types (e.g., Debug, Release) within one solution             |
| &#128994; [File groups](./userinterface.md#cmsis-view)                    | Logical grouping of source, header, and library files                       |
| &#128994; [Layer support](./create_app.md#configuration)                  | Easily retarget hardware connections                                        |
| &#128994; [Software components](./create_app.md#software-components)      | Manage software components on a project/layer level                         |
| &#128993; Manage packs                                                    | Manage CMSIS-Packs and versions graphically                                 |
| &#128994; [Zephyr project support](./zephyr.md)                           | Build and debug Zephyr-based applications                                   |
| &#128994; [Configuration Wizard](./userinterface.md#configuration-wizard) | GUI-assisted generation and modification of configuration code              |

### Build system

| Feature                                                                        | Description                                                           |
| ------------------------------------------------------------------------------ | --------------------------------------------------------------------- |
| &#128994; [Integrated build](https://open-cmsis-pack.github.io/cmsis-toolbox/) | Based on CMSIS-Toolbox                                                |
| &#128994; [Incremental build](./build_run.md)                                  | Dependency tracking to rebuild only changed files                     |
| &#128994; Toolchain options                                                    | Per-target configuration of compiler, assembler, linker, and debugger |
| &#128994; west support                                                         | Build Zephyr projects natively                                        |

### Build output and feedback

| Feature                                                   | Description                                           |
| --------------------------------------------------------- | ----------------------------------------------------- |
| &#128994; Map file                                        | Memory map of the image                               |
| &#128994; [Build log](./build_run.md#build-output)        | Detailed output of errors, warnings, and build status |
| &#128994; [Error navigation](./build_run.md#build-output) | Direct navigation from build messages to source code  |

### Integration and extensibility

| Feature                                      | Description                                                                   |
| -------------------------------------------- | ----------------------------------------------------------------------------- |
| &#128994; [External tools](./runexternal.md) | Invoke third-party tools via configurable commands                            |
| &#128994; Version control                    | Excellent integration with Git (Timeline: VS Code built-in)                   |
| &#128994; AI coding agents                   | Integration with third-party coding agents (Timeline: via VS Code extensions) |
| &#128994; Additional extensions              | Use third-party extensions with Keil Studio (Timeline: VS Code built-in)      |

## Compiler support

| Feature                                          | Description                                          |
| ------------------------------------------------ | ---------------------------------------------------- |
| &#128994; Arm Compiler for Embedded (AC6)        | Professional toolchain from Arm                      |
| &#128994; Arm Toolchain for Embedded (ATfE)      | Open-source, LLVM-based toolchain from Arm           |
| &#128994; Arm GNU Toolchain (GCC)                | Open-source, GCC-based toolchain from Arm            |
| &#128994; Clangd support                         | For comprehensive code completion                    |
| &#128994; Library generation                     | Generate libraries using library manager             |
| &#128994; Compiler and assembler control options | Interface for configuring compiler flags and options |

## Debug

### Core debug control

| Category                                            | Debug Features                                   |
| --------------------------------------------------- | ------------------------------------------------ |
| &#128994; [Run control](./debug.md#debug-toolbar)   | Run, halt, reset, step into, step over, step out |
| &#128994; [Breakpoints](./debug.md#breakpoints)     | Various types of breakpoints                     |
| &#128993; Watchpoints                               | Data read/write/access breakpoints (DWT)         |
| &#128994; [Multi-core](./debug.md#multi-core-debug) | Single GUI for multiple cores in a device        |

### Register and memory inspection

| Category                                                   | Debug Features                     |
| ---------------------------------------------------------- | ---------------------------------- |
| &#128994; [Core registers](./debug.md#variables)           | R0–R15, PSR, MSP, PSP, CONTROL     |
| &#128993; Core peripheral registers                        | NVIC, SysTick, MPU                 |
| &#128994; [Peripheral registers](./debug.md#peripherals)   | CMSIS-SVD decoded peripheral views |
| &#128994; [Memory inspection](./debug.md#memory-inspector) | Configurable memory views          |
| &#128994; [Memory inspection](./debug.md#memory-inspector) | Memory access breakpoints          |
| &#128994; [Memory inspection](./debug.md#memory-inspector) | Memory window live update          |

### Source-level debugging

| Category                                              | Debug Features              |
| ----------------------------------------------------- | --------------------------- |
| &#128994; [Variables](./debug.md#call-stack)          | Call stack view             |
| &#128994; [Variables](./debug.md#variables)           | Local variable inspection   |
| &#128994; [Disassembly](./debug.md#disassembly)       | Disassembly window          |
| &#128993; Disassembly                                 | Sync Disassembly and source |
| &#128994; [Variable inspection](./debug.md#variables) | Inline variable display     |
| &#128994; [Variable inspection](./debug.md#variables) | Variable hover inspection   |
| &#128993; Execution flow                              | Function call trace         |

### Real-time and trace features

| Category                                       | Debug Features            |
| ---------------------------------------------- | ------------------------- |
| &#128993; Serial wire output                   | ITM `printf`-style output |
| &#128994; [Variable tracing](./debug.md#watch) | Real-time data watch      |
| &#128993; Event tracing                        | Exception trace           |
| &#128993; Event tracing                        | Interrupt trace           |
| &#128994; [Sampling](./debug.md#cpu-time)      | CPU time                  |
| &#128993; Embedded trace buffer                | ETB instruction trace     |
| &#128993; Micro trace buffer                   | MTB instruction trace     |
| &#128308; Instruction trace                    | Embedded trace macrocell  |

### Component Viewer and Event Recorder

| Category                   | Debug Features          |
| -------------------------- | ----------------------- |
| &#128993; Component Viewer | Display and live update |
| &#128993; Event Recorder   | Show event information  |
| &#128993; Event Recorder   | Save/log                |
| &#128993; Event Recorder   | Event filtering         |
| &#128993; Event Recorder   | Event statistics        |

### RTOS awareness

| Category                                             | Debug Features                        |
| ---------------------------------------------------- | ------------------------------------- |
| &#128994; [RTOS support](./debug.md#rtos-views)      | Keil RTX5, FreeRTOS, Zephyr awareness |
| &#128994; [Thread visibility](./debug.md#rtos-views) | Thread list and state display         |
| &#128994; [Stack usage](./debug.md#rtos-views)       | Per-task stack usage                  |

### Analysis and visualization

| Category                                              | Debug Features                                        |
| ----------------------------------------------------- | ----------------------------------------------------- |
| &#128993; Logic Analyzer                              | Graphical variable and signal display                 |
| &#128993; System Analyzer                             | Data trace, core clock, ITM, current/voltage          |
| &#128994; [Serial monitor](./debug.md#serial-monitor) | Communication via serial/TCP ports                    |
| &#128308; Performance analysis                        | Execution time analysis                               |
| &#128308; Performance analysis                        | Function profiling                                    |
| &#128308; Execution statistics                        | Code coverage                                         |
| &#128993; Execution statistics                        | Timing statistics (Timeline: only via Event Recorder) |

### Simulation

| Category                                            | Debug Features                      |
| --------------------------------------------------- | ----------------------------------- |
| &#128994; [Fast models (FVPs)](./debug.md#arm-fvps) | Instruction-accurate CPU simulation |
| &#128993; Debug FVPs                                | Debugging on FVPs                   |

!!! Note
    FVP simulation models are not available in the MDK-Essential edition.

### Debug probe support

| Category                                                              | Debug Features           |
| --------------------------------------------------------------------- | ------------------------ |
| &#128994; [Debug probes](./debug.md#debug-adapter-support)            | ULINK2/UILNKplus support |
| &#128993; Debug probes                                                | UILNKpro support         |
| &#128994; [Debug probes](./debug.md#debug-adapter-support)            | CMSIS-DAP support        |
| &#128994; [Debug probes](./debug.md#debug-adapter-support)            | J-Link support           |
| &#128994; Debug interfaces                                            | SWD                      |
| &#128994; Debug interfaces                                            | JTAG                     |
| &#128994; [Debug interfaces](./build_run.md#check-target-information) | Target detection         |
| &#128993; Debug interfaces                                            | Connect configuration    |
| &#128994; [Flash programming](./build_run.md#load-and-run)            | Flash download           |
| &#128993; Flash programming                                           | Flash verification       |
| &#128993; Flash programming                                           | Configuration            |

> **Legend**
>
> &#128994; available  
> &#128993; feature implementation progressing  
> &#128308; investigating for alternative solution  
