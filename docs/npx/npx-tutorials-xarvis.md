# Tutorial 3: Training with snnForge

## Overview

snnForge is a neuromorphic training environment for NPX, based on snnTorch.  
This tutorial trains an example application with snnForge only, without any hardware.  
To run the trained network on hardware, see [Tutorial 2](npx-tutorials-prototyping.md) instead.

## Prerequisite

- [snnForge: Installation](npx-installation-manual-en.md)

## Checking Application Files

snnForge uses a configuration file for each application, which defines preprocessing steps, training parameters, and network structures.
These files are located in `${XARVIS_HOME}/snn-forge/app`, in the `<name>.snn.jsonc` format (JSON with comments).
An example configuration file is `mnist_app.snn.jsonc`.

## Training an Example Application

```text
cd ${XARVIS_HOME}/snn-forge
make mnist_app
```

> The MNIST dataset is downloaded automatically into `${XARVIS_HOME}/dataset` on the first run.
> Training runs on the CPU by default. To use a GPU, run e.g. `make mnist_app GPU_ID=0`.

## Checking the Trained Results

The training results will be generated in `${XARVIS_HOME}/snn-forge/result/mnist_app`.

- `parameter`: the trained parameters for each epoch, in floating point and quantized
- `report`: the validation and test accuracy
- `riscv`: the quantized parameters for the NPX accelerator (`mnist_app_parameter_quant.bin`)
