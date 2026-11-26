# Tutorial 2: From Spike-Based Learning to FPGA Prototyping

## Overview

This tutorial offers step-by-step guidance covering the process from spike-based learning to FPGA prototyping.

## Prerequisites

- <https://github.com/riscvexpress/npx-tutorials>

- [Tutorial 1: Hello](../rvx-tutorials-hello.md)

- An RTL simulator with mixed-language support

- A Genesys2 FPGA board connected to your computer - [Manual](../rvx-fpga-manual-en.md)

## Installing NPX

Install NPX with the `npx-tutorials` repository by following [Tutorial 1: Hello](../rvx-tutorials-hello.md).
snnForge is installed automatically in `#(cloned directory)/snn_forge`, so it does not need to be installed separately.
In this tutorial, we'll use `#(cloned directory)/platform/starc_neugemm` as the platform directory, referred to as `#(platform dir)`.

> On Linux, run `source #(cloned directory)/rvx_setup.sh` in every new terminal.

## Synthesizing the Processor

```text
cd #(platform dir)
make syn
```

## Training an Example Application

```text
cd #(platform dir)/util/npx
make mnist_app
```

> The application is defined in `#(platform dir)/util/npx/app/mnist_app.snn.jsonc`.
> The network is trained with snnForge, and the results are written to `#(platform dir)/util/npx/result`.

## Running an NPX Application via RTL Simulation

Not recommended because it takes a long time.

```text
cd #(platform dir)
make sim_rtl
cd sim_rtl
make profile_npx_app_fpga.all
```

## Prototyping the Processor on the Genesys2 Board

```text
cd #(platform dir)
make genesys2 // replace with your board name
cd imp_genesys2_YYYY-MM-DD // referred to as #(fpga dir)
make imp
```

> `make fpga_list` in #(platform dir) shows the supported boards.

## Running an NPX Application on the Genesys2 Board

```text
cd #(fpga dir)
make program
make printf
make profile_npx_app_fpga.all
```

## Using the RVX-EB Board

If you have an RVX-EB board, use `genesys2-eb` instead of `genesys2` in the steps above (e.g., `make genesys2-eb`).  
See [Genesys2 + RVX-EB](../rvx-fpga-manual-en.md#genesys2-rvx-eb) in the FPGA Setup Manual.
