# Tutorial 1: Hello

## Overview

- This tutorial generates an SoC and prints 'Hello, World' using RTL simulation.

## Prerequisite

- <https://github.com/rvx-etri/rvx-tutorials.git>

- [Installation Manual](rvx-installation-manual-en.md)

- An RTL simulator with mixed-language support (Not provided)


## Installing NPX (Cloning the Repository Included)

Install NPX by following the instructions in the installation manual, using the tutorial repository for cloning.

## Understating SoCs

Typically, an SoC means a chip that integrates a small computer within itself.  
Simply put, it is a chip that runs your computer program.  
It is used in environments where a general-purpose computer cannot be employed because of its size and power constraints.  
To achieve these advantages, both hardware and software for SoCs are co-designed from the outset, focusing on the execution of a limited set of application programs.  
NPX is a CAD tool for developing both hardware and software for SoC design.  
Its primary purpose is to run and accelerate C programs on hardware operating at around 100 MHz.  
For this purpose, this tutorial demonstrates how to run the simplest 'Hello, World' C program on the SoC using RTL simulation.

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
