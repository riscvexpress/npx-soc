# Tutorial 1: Hello

## Overview

- This tutorial generates an SoC and prints 'Hello, World' using RTL simulation.

## Prerequisite

- <https://github.com/riscvexpress/npx-tutorials>

- [Requirements](requirements.md)

- Git and make: [Install - Prerequisite](rvx-installation-manual-en-prerequisite.md)

- An RTL simulator with mixed-language support (Not provided)

## Installing NPX

Clone the tutorial repository and install NPX in it.

```text
git clone https://github.com/riscvexpress/npx-tutorials.git
cd npx-tutorials
git submodule init
git submodule update
make setup_python
make check_python
make install
```

> The cloned directory is referred to as #(cloned directory).  
> For details of each step, see the [Installation Manual](rvx-installation-manual-en.md).

If `make install` fails with `No rule to make target 'install'`, the submodules are missing.  
Run `git submodule update --init` and try again.

=== "Linux"

    Run `source #(cloned directory)/rvx_setup.sh` in every new terminal.

=== "Windows"

    Close and reopen the terminal, since the environment variables are registered with `setx`.

## Understanding SoCs

Typically, an SoC means a chip that integrates a small computer within itself.  
Simply put, it is a chip that runs your computer program.  
It is used in environments where a general-purpose computer cannot be employed because of its size and power constraints.  
To achieve these advantages, both hardware and software for SoCs are co-designed from the outset, focusing on the execution of a limited set of application programs.  
NPX is a CAD tool for developing both hardware and software for SoC design.  
Its primary purpose is to run and accelerate C programs on hardware operating at around 100 MHz.  
For this purpose, this tutorial demonstrates how to run the simplest 'Hello, World' C program on the SoC using RTL simulation.

## Running the C Program Using RTL Simulation

This tutorial uses the `starc_neugemm` platform, the NeuGEMM SoC.

```text
cd #(cloned directory)/platform/starc_neugemm
make clean
make syn
make sim_rtl
cd sim_rtl
make hello.all
```

> The C program is in `#(cloned directory)/platform/starc_neugemm/app/hello/src/main.c`.

At the end of the simulation, the following is printed.

```text
[INFO/SYSTEM] start SIM@RTL
Hello World!

<SIM:INFO>  1 cores have finished @             4454520 ns


[INFO/SYSTEM] end
```
