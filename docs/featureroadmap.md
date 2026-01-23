# Roadmap

For the following tables, this legend applies: &#9989; available, &#10060; not planned

## Project management

### Project creation and organization

| Feature                  | Description                                                     | Timeline                                                |
| ------------------------ | --------------------------------------------------------------- | ------------------------------------------------------- |
| Project creation         | Create, open, and manage CMSIS solution projects                | &#9989;/[link](./create_app.md)                         |
| Multi-project solution   | Manage multiple related projects within a single CMSIS solution | &#9989;/[link](./create_app.md)                         |
| Multi-solution workspace | Manage multiple solutions within one workspace                  | &#9989; (VS Code built-in)                              |
| Target types             | Multiple targets (e.g., HW, models) within one solution         | &#9989;/[link](./manage_settings.md)                    |
| Build types              | Multiple build types (e.g., Debug, Release) within one solution | &#9989;/[link](./manage_settings.md)                    |
| File groups              | Logical grouping of source, header, and library files           | &#9989;/[link](./userinterface.md#cmsis-view)           |
| Layer support            | Easily retarget hardware connections                            | &#9989;/[link](./create_app.md#configuration)           |
| Software components      | Manage software components on a project/layer level             | &#9989;/[link](./create_app.md#software-components)     |
| CMSIS-Packs              | Manage CMSIS-Packs and versions graphically                     | Early 2026                                              |
| Zephyr project support   | Build and debug Zephyr-based applications                       | &#9989;/[link](./zephyr.md)                             |
| Configuration Wizard     | GUI-assisted generation and modification of configuration code  | &#9989;/[link](./userinterface.md#configuration-wizard) |

### Build system

| Feature           | Description                                                           | Timeline                                                         |
| ----------------- | --------------------------------------------------------------------- | ---------------------------------------------------------------- |
| Integrated build  | Based on CMSIS-Toolbox                                                | &#9989;/[link](https://open-cmsis-pack.github.io/cmsis-toolbox/) |
| Incremental build | Dependency tracking to rebuild only changed files                     | &#9989;/[link](./build_run.md)                                   |
| Toolchain options | Per-target configuration of compiler, assembler, linker, and debugger | &#9989;                                                          |
| west support      | Build Zephyr projects natively                                        | &#9989;                                                          |

### Build output and feedback

| Feature          | Description                                           | Timeline                                    |
| ---------------- | ----------------------------------------------------- | ------------------------------------------- |
| Map file         | Memory map of the image                               | &#9989;                                     |
| Build log        | Detailed output of errors, warnings, and build status | &#9989;/[link](./build_run.md#build-output) |
| Error navigation | Direct navigation from build messages to source code  | &#9989;/[link](./build_run.md#build-output) |

### Integration and extensibility

| Feature               | Description                                        | Timeline                         |
| --------------------- | -------------------------------------------------- | -------------------------------- |
| External tools        | Invoke third-party tools via configurable commands | &#9989;/[link](./runexternal.md) |
| Version control       | Excellent integration with Git                     | &#9989; (VS Code built-in)       |
| AI coding agents      | Integration with third-party coding agents         | &#9989; (via VS Code extensions) |
| Additional extensions | Use third-party extensions with Keil Studio        | &#9989; (VS Code built-in)       |

## Compiler support

| Feature                                | Description                                          | Timeline |
| -------------------------------------- | ---------------------------------------------------- | -------- |
| Arm Compiler for Embedded (AC6)        | Professional toolchain from Arm                      | &#9989;  |
| Arm Toolchain for Embedded (ATfE)      | Open-source, LLVM-based toolchain from Arm           | &#9989;  |
| Arm GNU Toolchain (GCC)                | Open-source, GCC-based toolchain from Arm            | &#9989;  |
| Clangd support                         | For comprehensive code completion                    | &#9989;  |
| Library generation                     | Generate libraries using library manager             | &#9989;  |
| Compiler and assembler control options | Interface for configuring compiler flags and options | &#9989;  |

## Debug

### Core debug control

| Category    | Debug Features                                   | Timeline                                    |
| ----------- | ------------------------------------------------ | ------------------------------------------- |
| Run control | Run, halt, reset, step into, step over, step out | &#9989;/[link](./debug.md#debug-toolbar)    |
| Breakpoints | Various types of breakpoints                     | &#9989;/[link](./debug.md#breakpoints)      |
| Watchpoints | Data read/write/access breakpoints (DWT)         | Late 2026                                   |
| Multi-core  | Single GUI for multiple cores in a device        | &#9989;/[link](./debug.md#multi-core-debug) |

### Register and memory inspection

| Category                  | Debug Features                     | Timeline                                    |
| ------------------------- | ---------------------------------- | ------------------------------------------- |
| Core registers            | R0–R15, PSR, MSP, PSP, CONTROL     | &#9989;/[link](./debug.md#variables)        |
| Core peripheral registers | NVIC, SysTick, MPU                 | Early 2026                                  |
| Peripheral registers      | CMSIS-SVD decoded peripheral views | &#9989;/[link](./debug.md#peripherals)      |
| Memory inspection         | Configurable memory views          | &#9989;/[link](./debug.md#memory-inspector) |
| Memory inspection         | Memory access breakpoints          | &#9989;/[link](./debug.md#memory-inspector) |
| Memory inspection         | Memory window live update          | &#9989;/[link](./debug.md#memory-inspector) |

### Source-level debugging

| Category            | Debug Features              | Timeline                               |
| ------------------- | --------------------------- | -------------------------------------- |
| Stack analysis      | Call stack view             | &#9989;/[link](./debug.md#call-stack)  |
| Stack analysis      | Local variable inspection   | &#9989;/[link](./debug.md#variables)   |
| Disassembly         | Disassembly window          | &#9989;/[link](./debug.md#disassembly) |
| Disassembly         | Sync Disassembly and source | Late 2026                              |
| Variable inspection | Inline variable display     | &#9989;/[link](./debug.md#variables)   |
| Variable inspection | Variable hover inspection   | &#9989;/[link](./debug.md#variables)   |
| Execution flow      | Function call trace         | tbd                                    |

### Real-time and trace features

| Category              | Debug Features            | Timeline                            |
| --------------------- | ------------------------- | ----------------------------------- |
| Serial wire output    | ITM `printf`-style output | Early 2026                          |
| Variable tracing      | Real-time data watch      | &#9989;/[link](./debug.md#watch)    |
| Event tracing         | Exception trace           | Mid 2026                            |
| Event tracing         | Interrupt trace           | Mid 2026                            |
| Sampling              | CPU time                  | &#9989;/[link](./debug.md#cpu-time) |
| Embedded trace buffer | ETB instruction trace     | Mid 2026                            |
| Micro trace buffer    | MTB instruction trace     | Late 2026                           |
| Instruction trace     | Embedded trace macrocell  | &#10060;                            |

### Component Viewer and Event Recorder

| Category         | Debug Features          | Timeline   |
| ---------------- | ----------------------- | ---------- |
| Component Viewer | Display and live update | Early 2026 |
| Event Recorder   | Show event information  | Mid 2026   |
| Event Recorder   | Save/log                | Mid 2026   |
| Event Recorder   | Event filtering         | Mid 2026   |
| Event Recorder   | Event statistics        | Mid 2026   |

### RTOS awareness

| Category          | Debug Features                        | Timeline                              |
| ----------------- | ------------------------------------- | ------------------------------------- |
| RTOS support      | Keil RTX5, FreeRTOS, Zephyr awareness | &#9989;/[link](./debug.md#rtos-views) |
| Thread visibility | Thread list                           | &#9989;/[link](./debug.md#rtos-views) |
| Thread visibility | Thread state display                  | &#9989;/[link](./debug.md#rtos-views) |
| Stack usage       | Per-task stack usage                  | &#9989;/[link](./debug.md#rtos-views) |

### Analysis and visualization

| Category             | Debug Features                               | Timeline                                  |
| -------------------- | -------------------------------------------- | ----------------------------------------- |
| Logic Analyzer       | Graphical variable and signal display        | Late 2026                                 |
| System Analyzer      | Data trace, core clock, ITM, current/voltage | Late 2026                                 |
| Serial monitor       | Communication via serial/TCP ports           | &#9989;/[link](./debug.md#serial-monitor) |
| Performance analysis | Execution time analysis                      | &#10060;                                  |
| Performance analysis | Function profiling                           | &#10060;                                  |
| Execution statistics | Code coverage                                | &#10060;                                  |
| Execution statistics | Timing statistics                            | only via Event Recorder                   |

### Simulation

| Category           | Debug Features                      | Timeline                            |
| ------------------ | ----------------------------------- | ----------------------------------- |
| Fast models (FVPs) | Instruction-accurate CPU simulation | &#9989;/[link](./debug.md#arm-fvps) |
| Debug FVPs         | Debugging on FVPs                   | Mid 2026                            |

!!! Note
    FVP simulation models are not available in the MDK-Essential edition.

### Debug probe support

| Category          | Debug Features           | Timeline                                                |
| ----------------- | ------------------------ | ------------------------------------------------------- |
| Debug probes      | ULINK2/UILNKplus support | &#9989;/[link](./debug.md#debug-adapter-support)        |
| Debug probes      | UILNKpro support         | Late 2026                                               |
| Debug probes      | CMSIS-DAP support        | &#9989;/[link](./debug.md#debug-adapter-support)        |
| Debug probes      | J-Link support           | &#9989;/[link](./debug.md#debug-adapter-support)        |
| Debug interfaces  | SWD                      | &#9989;                                                 |
| Debug interfaces  | JTAG                     | &#9989;                                                 |
| Debug interfaces  | Target detection         | &#9989;/[link](./build_run.md#check-target-information) |
| Debug interfaces  | Connect configuration    | Early 2026                                              |
| Flash programming | Flash download           | &#9989;/[link](./build_run.md#load-and-run)             |
| Flash programming | Flash verification       | Mid 2026                                                |
| Flash programming | Configuration            | Late 2026                                               |
