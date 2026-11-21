# NPX Manual: Integrating User IPs into the Platform

## Overview

- This manual explains how to integrate user IPs into the SoC platform.

- After identifying the interfaces of a completed IP, or defining the interfaces of an IP to be developed, specify them in `#(platform xml)`.

- This will generate the corresponding NoC signals for connecting those interfaces.

- Then, instantiate your IP and connect it to the generated signals.

## Prerequisite

- [Example Platforms](rvx-tutorials-example.md)

## Types of the Interfaces of User IPs

### Library Names

The interfaces of user IPs are represented using the following naming convention:

user_XXX_YYY_ZZZ

- XXX {slaveif, masterif}: interface role

- YYY {apb, axi, axi4, axi4l, xmi}: communication protocol

- ZZZ {clkout, clkin}: clock direction toward the NoC, from the interface’s perspective

### `clkin`

- Indicates that the clock enters the interface from the NoC side.

- This applies when the interface operates in the same clock domain as the NoC, eliminating the need for a separate clock and CDC (Clock Domain Crossing) logic.

- In the Verilog code, it is sufficient to map the provided clock to the corresponding port of the user IP.

- This designation also applies when the user IP includes internal CDC logic for this interface.

### `clkout`

- Indicates that the clock used by the interface is forwarded to the NoC.

- This is used when the interface is driven by a separate clock provided by the user.

- A CDC is required between the interface and the NoC, and it is automatically handled by NPX.

- In the Verilog code, the clock to be used by the interface must be explicitly specified by the user.

- This designation is used when the user IP does not include internal CDC logic for the interface.

## Location of an Example Platform

- `#(cloned directory)/rvx_platform_example/test_user_ip`

- This directory will hereafter be referred to as `#(example dir)`.

## Specifying the Interfaces

- Define the interface descriptions in your `#(platform xml)`.

- An example is provided in `#(example dir)/test_user_ip.xml`.

## Connecting IPs to the NoC

- When you run `make syn`, a file named `#(platform name)_user_region.vh` is generated in `#(platform dir)/user/rtl/include`.

    - This file is called `#(user region file)`.

- Write the code to connect your IPs to the NoC in `#(user region file)`.

    - The example file is `#(example dir)/user/rtl/include/test_user_ip_user_region.vh`).

    - Because `#(user region file)` is part of a Verilog HDL file, only Verilog is allowed, not SystemVerilog.

- Use `rstnn_user` or `rstpp_user` for reset signals.

    - For the power-on reset, `global_rstnn` and `global_rstpp` are available.

- For clocks, you can use the predefined signals or create new ones.

    - [Example: test_clock](examples/test_clock.md)

    - `clk_system` is recommended for APB interfaces.

## Debugging User IPs on FPGA Prototypes

[Manual: Debugging Methods on FPGA Prototypes](rvx-feature-manual-en-debugging.md)

## Note on User IPs

- In `#(user region file)`, IPs must be instantiated and connected to ports using Verilog-style syntax. Therefore, if the IPs are designed in VHDL or SystemVerilog, additional work may be required.

- For parameter and port declarations in the IP top module, only features compatible with Verilog should be used. To ensure this, it may be necessary to modify the IP top module itself or create a new wrapper module as the top-level interface.

## Note on `#(user region file)`

- Once created, `#(user region file)` is not automatically updated when `#(platform xml)` is modified, in order to preserve any user modifications.

- Instead, the updated file reflecting the changes is generated in `#(platform dir)/user/template`. Therefore, you can review that file and manually apply the necessary changes to `#(user region file)`.
