# Software Architecture

- Dependency diagram of libraries that make up the micromouse motherboard firmware:
![software-architecture.drawio](_images/software-architecture.drawio.png)

## `runtime_diagnositcs`

![runtime_diagnostics](_images/runtime_diagnostics.drawio.png)

- Minimal library for reporting runtime telemetry, warnings, and errors
- Allows for code w/ command-query separation and clean runtime handling across all libraries

## `at32uc3l0256_drivers`

- AT32UC3L0256 drivers wrapped to adhere to the hardware abstraction layer
- This layer changes upon switching the motherboard MCU/processor
- The HAL implementation changes if any HAL contracts are modified

## `hardware_abstraction_layer`

![hardware_abstraction_layer](_images/hardware_abstraction_layer.drawio.png)

- Middleware to abstract hardware peripherals/components on a processor like adc, clock, gpio, etc
- Forces low level drivers to adhere to this HAL via dependency inversion
- This layer may expand to support new hardware peripherals on the current processor or new processors, but shouldn't be swapped otherwise

## `device_drivers`

![device_drivers](_images/device_drivers.drawio.png)

- Defines all external hardware components, as well as the processor itself
- This layer may expand to support new hardware components on the motherboard, but shouldn't be swapped otherwise

## `mouse_drivers`

![mouse_drivers](_images/mouse_drivers.drawio.png)

- Interface to control the micromouse for movement and control
- Also provides interfaces for calibration and testing to a particular maze

## `maze_solver`

![maze_solver](_images/maze_solver.drawio.png)

- Maze solving interface to solve a micromouse maze

## `shell`

![shell](_images/shell.drawio.png)

- Command line interface for calibration and testing

## `mouse`

![mouse](_images/mouse.drawio.png)

- Final executable to be deployed to micromouse hardware
- Includes a minimal firmware version module to print the version of all libraries that make up the final binary, provided by the build configuration system

## `mouse_simulator`

![mouse_simulator](_images/mouse_simulator.drawio.png)

- C++ executable to simulate a micromouse in a virtual maze to generate optimal parameters
