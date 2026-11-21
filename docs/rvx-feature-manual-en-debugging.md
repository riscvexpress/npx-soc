# NPX Manual: Debugging Methods on FPGA Prototypes

## Overview

- This manual introduces methods for debugging an SoC built with NPX on FPGA prototypes.

## Prerequisite

- [Tutorial: Hello](rvx-tutorials-hello.md)

- An FPGA board connected to your computer - [Manual](rvx-fpga-manual-en.md)

## Software-based Debugging

- Variables can be printed using `printf` for debugging purposes.

- Include the header file `ervp_printf.h` to use this functionality.

- Several debugging functions, which are extensions of `printf`, are available as listed below:

    | Function Name | Description |
    | :---: | :---: |
    | debug_printx(var) | Prints `var` in `%08x` format. |
    | debug_printd(var) | Prints `var` in `%d` format. |
    | debug_printf(var) | Prints `var` in `%f` format. |
    | debug_printc(var) | Prints `var` in `%c` format. |
    | debug_prints(var) | Prints `var` in `%s` format. |
    | debug_printn() | Prints a blank line. |
    | debug_print_line() | Prints only the current code location. |

## CPU Debugger-based Debugging (NOT supported)

- If a RISC-V CPU includes JTAG functionality (via the RISC-V Debug Module), users can use OpenOCD or GDB for debugging.

- None of the CPUs provided by NPX include this functionality.

- If users want to use this feature, they must obtain a CPU that supports it.

## NoC Debugger-based Debugging

This method can only read values based on the memory address.

## Vivado ILA-based Debugging

### Overview

- This method requires some understanding of Vivado ILA to use.

- The ILA is a technique that allows you to monitor specific signals defined during design time for debugging purposes.

- While it enables observation of many signals, the ILA module becomes part of the design itself, which limits both the number of signals and the time span that can be captured.

- NPX provides a feature that automatically generates and integrates an ILA into the design once the debugging signals are specified.

### Location of an Example Platform

- `#(cloned directory)/rvx_platform_example/test_ila`

- This directory will hereafter be referred to as `#(example dir)`.

### Defining Debugging Signals

- Run `make user` in `#(platform dir)` if `#(platform dir)/user` does not exist.

- Define the signals in `#(platform dir)/user/ila/common`.

    - Or, `#(platform dir)/user/ila/#(fpga name)`.

    - All XML files in these directories will be converted into ILA modules.

    - The names of the XML files can be chosen based on readability.

- An example is provided in `#(example dir)/user/ila/common/core.xml`.

- The `<clock>` tag sets the clock signal used for sampling.

- The `<signal>` block defines a signal to be monitored.

    - `<name>` specifies the display name shown in the ILA GUI,

    - `<value>` defines the actual signal to be monitored, and

    - `<width>` indicates its bit width.

- The signal paths for `<clock>` and `<value>` should be specified based on `#(platform name).v`.

    - It can be specified using a hierarchical path even if it is not declared as a port.

    - For reference, the file `ila_description.vh` is generated from the XML file, which is a part of `#(platform name).v`.

### Generating ILAs from XML Files

```text
cd #(fpga dir)
make ila
```

### Generating an FPGA Bitstream Including ILAs

Assume that you already have the platform for debugging.

```text
cd #(fpga dir)
```

change IMP_MODE from 'release' to 'debug' in '#(fpga dir)/set_design.tcl'

```text
make imp
```

### Debugging Applications on FPGA Prototypes

```text
make program // The Vivado GUI will be launched
```

Set the trigger conditions of ILAs in the GUI

Open another terminal in the same directory.

```text
make printf
make #(app name).all
```
