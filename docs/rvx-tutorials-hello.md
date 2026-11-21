# Tutorial 2: Hello

## Overview

- This tutorial is intended to verify the most basic functionality of NPX.

## Prerequisite

- <https://github.com/rvx-etri/rvx-tutorials.git>

- [Installation Manual](rvx-installation-manual-en.md)

- An RTL simulator with mixed-language support (Not provided)

- An FPGA board connected to your computer - [Manual](rvx-fpga-manual-en.md) (Not provided)

## Installing NPX (Cloning the Repository Included)

Install NPX by following the instructions in the installation manual, using the tutorial repository for cloning.

## Understating SoCs

Typically, an SoC means a chip that integrates a small computer within itself.  
Simply put, it is a chip that runs your computer program.  
It is used in environments where a general-purpose computer cannot be employed because of its size and power constraints.  
To achieve these advantages, both hardware and software for SoCs are co-designed from the outset, focusing on the execution of a limited set of application programs.  
NPX is a CAD tool for developing both hardware and software for SoC design.  
Its primary purpose is to run and accelerate C programs on hardware operating at around 100 MHz.  
For this purpose, this tutorial demonstrates how to run the simplest 'Hello, World' C program on hardware.

## Running the C Program Using RTL Simulation

```text
cd #(cloned directory)
source ./rvx_setup.sh
cd ./platform/tip_hello
make clean
make syn
make sim_rtl
cd sim_rtl
make hello.all
```

## Running the C Program Using FPGA Prototyping

```text
cd #(cloned directory)
source ./rvx_setup.sh
cd ./platform/tip_hello
make clean
make syn
make arty-100t // or the FPGA board you have
cd imp_arty-100t_XXXX // referred to as #(fpga dir)
make imp
```

Connect the FPGA board to your computer.

```text
make program
make printf
make hello.all
```
