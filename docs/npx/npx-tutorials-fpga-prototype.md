# Tutorial 3: Running Software on a Prebuilt FPGA Prototype

## Overview

This tutorial runs NPX applications on an FPGA prototype whose bitstream is already included in the repository.  
The hardware cannot be changed, but you can train SNNs and develop and run software on it.  
Since the processor is not synthesized or implemented, no license tools are required.

## Prerequisites

- <https://github.com/riscvexpress/npx-fpga-prototype>

- [Requirements](../requirements.md)

- Git and make: [Install - Prerequisite](../rvx-installation-manual-en-prerequisite.md)

- AMD Vivado, to program the FPGA board (No license is required)

- A Genesys2 FPGA board connected to your computer - [Manual](../rvx-fpga-manual-en.md)

## Installing NPX

Clone the repository and install NPX in it.

```text
git clone https://github.com/riscvexpress/npx-fpga-prototype.git
cd npx-fpga-prototype
git submodule init
git submodule update
make setup_python
make check_python
make install
```

> The cloned directory is referred to as #(cloned directory).  
> snnForge is installed automatically in `#(cloned directory)/snn_forge`.  
> For details of each step, see the [Installation Manual](../rvx-installation-manual-en.md).

If `make install` fails with `No rule to make target 'install'`, the submodules are missing.  
Run `git submodule update --init` and try again.

=== "Linux"

    Run `source #(cloned directory)/rvx_setup.sh` in every new terminal.

=== "Windows"

    Close and reopen the terminal, since the environment variables are registered with `setx`.

In this tutorial, we'll use `#(cloned directory)/platform/starc_vera1` as the platform directory, referred to as `#(platform dir)`.  
The bitstream is in `#(platform dir)/imp_genesys2_YYYY-MM-DD`, referred to as `#(fpga dir)`.

> Do not run `make syn` or `make imp`, since the prebuilt hardware is used as it is.

## Training an Example Application

```text
cd #(platform dir)/util/npx
make mnist_app
```

> The application is defined in `#(platform dir)/util/npx/app/mnist_app.snn.jsonc`.  
> The network is trained with snnForge, and the results are written to `#(platform dir)/util/npx/result`.

## Setting Up the Paths

The prebuilt FPGA prototype requires the paths to be set up once before programming the board.

```text
cd #(fpga dir)
make path
```

## Running an NPX Application on the Genesys2 Board

Connect the FPGA board to your computer.

```text
cd #(fpga dir)
make program
make printf
make profile_npx_app_fpga.all
```

> `make program` downloads the prebuilt bitstream to the FPGA board.  
> To check the board first, run `make hello.all` instead of the last command.

## Using the RVX-EB Board

If you have an RVX-EB board, use `#(platform dir)/imp_genesys2-eb_YYYY-MM-DD` as #(fpga dir) instead.  
See [Genesys2 + RVX-EB](../rvx-fpga-manual-en.md#genesys2-rvx-eb) in the FPGA Setup Manual.
