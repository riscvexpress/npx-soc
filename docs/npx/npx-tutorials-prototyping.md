# Tutorial 3: From Spike-Based Learning to FPGA Prototyping

## Overview

This tutorial offers step-by-step guidance covering the process from spike-based learning to FPGA prototyping.

## Prerequisites

- <https://github.com/riscvexpress/npx-xarvis.git>

- <https://github.com/rvx-etri/npx-tutorials.git>

- [Tutorial 1: Training with snnForge](npx-tutorials-xarvis.md)

- [Tutorial 2: Hello](../rvx-tutorials-hello.md)

- An RTL simulator with mixed-language support

- A Genesys2 FPGA board connected to your computer - [Manual](../rvx-fpga-manual-en.md)

## Installing the snnForge and NPX Environment

Follow the two tutorials in the Prerequisites to install both the snnForge and NPX.  
The directories cloned from `npx-xarvis.git` and `npx-tutorials.git` are called `${XARVIS_HOME}` and `#(tutorial dir)`, respectively.  
In this tutorial, we’ll use `#(tutorial dir)/platform/starc_neugemm` as the platform directory, referred to as `#(platform dir)`.

## Synchronizing with snnForge

```text
source #(tutorial dir)/rvx_setup.sh
source ${XARVIS_HOME}/rvx_setup.sh
cd #(platform dir)/util/npx
make setup
```

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

## Running an NPX Application via RTL Simulation

Not recommended because it takes a long time.

```text
source #(tutorial dir)/rvx_setup.sh
cd #(platform dir)
make sim_rtl
cd sim_rtl
make test_npx_app.all
```

## Prototyping the Processor on the Genesys2 Board

```text
source #(tutorial dir)/rvx_setup.sh
cd #(platform dir)
make genesys2 // replace with your board name
cd imp_genesys2_YYYY-MM-DD // referred to as #(fpga dir)
make imp
```

## Running an NPX Application on the Genesys2 Board

```text
source #(tutorial dir)/rvx_setup.sh
cd #(fpga dir)
make program
make printf
make test_npx_app.all
```
