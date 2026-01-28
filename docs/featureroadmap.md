# Roadmap

For the following tables, this legend applies:

- &#128994; available
- &#128993; feature implementation progressing
- &#128308; investigating for alternative solution

## Project management

### Project creation and organization

| Feature                  | Description                                                     | Timeline                                                |
| ------------------------ | --------------------------------------------------------------- | ------------------------------------------------------- |
| Project creation         | Create, open, and manage CMSIS solution projects                | &#128994;/[link](./create_app.md)                         |
| Multi-project solution   | Manage multiple related projects within a single CMSIS solution | &#128994;/[link](./create_app.md)                         |
| Multi-solution workspace | Manage multiple solutions within one workspace                  | &#128994; (VS Code built-in)                              |
| Target types             | Multiple targets (e.g., HW, models) within one solution         | &#128994;/[link](./manage_settings.md)                    |
| Build types              | Multiple build types (e.g., Debug, Release) within one solution | &#128994;/[link](./manage_settings.md)                    |
| File groups              | Logical grouping of source, header, and library files           | &#128994;/[link](./userinterface.md#cmsis-view)           |
| Layer support            | Easily retarget hardware connections                            | &#128994;/[link](./create_app.md#configuration)           |
| Software components      | Manage software components on a project/layer level             | &#128994;/[link](./create_app.md#software-components)     |
| Manage packs             | Manage CMSIS-Packs and versions graphically                     | Early 2026                                              |
| Zephyr project support   | Build and debug Zephyr-based applications                       | &#128994;/[link](./zephyr.md)                             |
| Configuration Wizard     | GUI-assisted generation and modification of configuration code  | &#128994;/[link](./userinterface.md#configuration-wizard) |

### Build system

| Feature           | Description                                                           | Timeline                                                         |
| ----------------- | --------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Integrated build  | Based on CMSIS-Toolbox                                                | &#128994;/[link](https://open-cmsis-pack.github.io/cmsis-toolbox/) |
| Incremental build | Dependency tracking to rebuild only changed files                     | &#128994;/[link](./build_run.md)                                   |
| Toolchain options | Per-target configuration of compiler, assembler, linker, and debugger | &#128994;                                                          |
| west support      | Build Zephyr projects natively                                        | &#128994;                                                          |

### Build output and feedback

| Feature          | Description                                           | Timeline                                    |
| ---------------- | ----------------------------------------------------- | ------------------------------------------- |
| Map file         | Memory map of the image                               | &#128994;                                     |
| Build log        | Detailed output of errors, warnings, and build status | &#128994;/[link](./build_run.md#build-output) |
| Error navigation | Direct navigation from build messages to source code  | &#128994;/[link](./build_run.md#build-output) |

### Integration and extensibility

| Feature               | Description                                        | Timeline                         |
| --------------------- | -------------------------------------------------- | -------------------------------- |
| External tools        | Invoke third-party tools via configurable commands | &#128994;/[link](./runexternal.md) |
| Version control       | Excellent integration with Git                     | &#128994; (VS Code built-in)       |
| AI coding agents      | Integration with third-party coding agents         | &#128994; (via VS Code extensions) |
| Additional extensions | Use third-party extensions with Keil Studio        | &#128994; (VS Code built-in)       |

## Compiler support

| Feature                                | Description                                          | Timeline |
| -------------------------------------- | ---------------------------------------------------- | -------- |
| Arm Compiler for Embedded (AC6)        | Professional toolchain from Arm                      | &#128994;  |
| Arm Toolchain for Embedded (ATfE)      | Open-source, LLVM-based toolchain from Arm           | &#128994;  |
| Arm GNU Toolchain (GCC)                | Open-source, GCC-based toolchain from Arm            | &#128994;  |
| Clangd support                         | For comprehensive code completion                    | &#128994;  |
| Library generation                     | Generate libraries using library manager             | &#128994;  |
| Compiler and assembler control options | Interface for configuring compiler flags and options | &#128994;  |

## Debug

### Core debug control

| Category    | Debug Features                                   | Timeline                                    |
| ----------- | ------------------------------------------------ | ------------------------------------------- |
| Run control | Run, halt, reset, step into, step over, step out | &#128994;/[link](./debug.md#debug-toolbar)    |
| Breakpoints | Various types of breakpoints                     | &#128994;/[link](./debug.md#breakpoints)      |
| Watchpoints | Data read/write/access breakpoints (DWT)         | &#128993;                                   |
| Multi-core  | Single GUI for multiple cores in a device        | &#128994;/[link](./debug.md#multi-core-debug) |

### Register and memory inspection

| Category                  | Debug Features                     | Timeline                                    |
| ------------------------- | ---------------------------------- | ------------------------------------------- |
| Core registers            | R0–R15, PSR, MSP, PSP, CONTROL     | &#128994;/[link](./debug.md#variables)        |
| Core peripheral registers | NVIC, SysTick, MPU                 | &#128993;                                  |
| Peripheral registers      | CMSIS-SVD decoded peripheral views | &#128994;/[link](./debug.md#peripherals)      |
| Memory inspection         | Configurable memory views          | &#128994;/[link](./debug.md#memory-inspector) |
| Memory inspection         | Memory access breakpoints          | &#128994;/[link](./debug.md#memory-inspector) |
| Memory inspection         | Memory window live update          | &#128994;/[link](./debug.md#memory-inspector) |

### Source-level debugging

| Category            | Debug Features              | Timeline                               |
| ------------------- | --------------------------- | -------------------------------------- |
| Variables           | Call stack view             | &#128994;/[link](./debug.md#call-stack)  |
| Variables           | Local variable inspection   | &#128994;/[link](./debug.md#variables)   |
| Disassembly         | Disassembly window          | &#128994;/[link](./debug.md#disassembly) |
| Disassembly         | Sync Disassembly and source | &#128993;                              |
| Variable inspection | Inline variable display     | &#128994;/[link](./debug.md#variables)   |
| Variable inspection | Variable hover inspection   | &#128994;/[link](./debug.md#variables)   |
| Execution flow      | Function call trace         | &#128993;                                    |

### Real-time and trace features

| Category              | Debug Features            | Timeline                            |
| --------------------- | ------------------------- | ----------------------------------- |
| Serial wire output    | ITM `printf`-style output | &#128993;                          |
| Variable tracing      | Real-time data watch      | &#128994;/[link](./debug.md#watch)    |
| Event tracing         | Exception trace           | &#128993;                            |
| Event tracing         | Interrupt trace           | &#128993;                            |
| Sampling              | CPU time                  | &#128994;/[link](./debug.md#cpu-time) |
| Embedded trace buffer | ETB instruction trace     | &#128993;                            |
| Micro trace buffer    | MTB instruction trace     | &#128993;                           |
| Instruction trace     | Embedded trace macrocell  | &#128308;                            |

### Component Viewer and Event Recorder

| Category         | Debug Features          | Timeline   |
| ---------------- | ----------------------- | ---------- |
| Component Viewer | Display and live update | &#128993; |
| Event Recorder   | Show event information  | &#128993;   |
| Event Recorder   | Save/log                | &#128993;   |
| Event Recorder   | Event filtering         | &#128993;   |
| Event Recorder   | Event statistics        | &#128993;   |

### RTOS awareness

| Category          | Debug Features                        | Timeline                              |
| ----------------- | ------------------------------------- | ------------------------------------- |
| RTOS support      | Keil RTX5, FreeRTOS, Zephyr awareness | &#128994;/[link](./debug.md#rtos-views) |
| Thread visibility | Thread list and state display         | &#128994;/[link](./debug.md#rtos-views) |
| Stack usage       | Per-task stack usage                  | &#128994;/[link](./debug.md#rtos-views) |

### Analysis and visualization

| Category             | Debug Features                               | Timeline                                  |
| -------------------- | -------------------------------------------- | ----------------------------------------- |
| Logic Analyzer       | Graphical variable and signal display        | &#128993;                                 |
| System Analyzer      | Data trace, core clock, ITM, current/voltage | &#128993;                                 |
| Serial monitor       | Communication via serial/TCP ports           | &#128994;/[link](./debug.md#serial-monitor) |
| Performance analysis | Execution time analysis                      | &#128308;                                  |
| Performance analysis | Function profiling                           | &#128308;                                  |
| Execution statistics | Code coverage                                | &#128308;                                  |
| Execution statistics | Timing statistics                            | only via Event Recorder                   |

### Simulation

| Category           | Debug Features                      | Timeline                            |
| ------------------ | ----------------------------------- | ----------------------------------- |
| Fast models (FVPs) | Instruction-accurate CPU simulation | &#128994;/[link](./debug.md#arm-fvps) |
| Debug FVPs         | Debugging on FVPs                   | &#128993;                            |

!!! Note
    FVP simulation models are not available in the MDK-Essential edition.

### Debug probe support

| Category          | Debug Features           | Timeline                                                |
| ----------------- | ------------------------ | ------------------------------------------------------- |
| Debug probes      | ULINK2/UILNKplus support | &#128994;/[link](./debug.md#debug-adapter-support)        |
| Debug probes      | UILNKpro support         | &#128993;                                               |
| Debug probes      | CMSIS-DAP support        | &#128994;/[link](./debug.md#debug-adapter-support)        |
| Debug probes      | J-Link support           | &#128994;/[link](./debug.md#debug-adapter-support)        |
| Debug interfaces  | SWD                      | &#128994;                                                 |
| Debug interfaces  | JTAG                     | &#128994;                                                 |
| Debug interfaces  | Target detection         | &#128994;/[link](./build_run.md#check-target-information) |
| Debug interfaces  | Connect configuration    | &#128993;                                              |
| Flash programming | Flash download           | &#128994;/[link](./build_run.md#load-and-run)             |
| Flash programming | Flash verification       | &#128993;                                                |
| Flash programming | Configuration            | &#128993;                                               |
