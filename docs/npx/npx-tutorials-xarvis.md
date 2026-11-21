# Tutorial 1: Training with snnForge

## Overview

snnForge is a neuromorphic training environment for NPX, based on snnTorch.  
This tutorial trains an example application with snnForge.

## Prerequisite

- [snnForge: Installation](npx-installation-manual-en.md)

## Checking Application Files

snnForge uses text-based configuration files to define preprocessing steps, training parameters, and network structures.  
These files are located in `#(cloned directory)/npx_trainer/app`.  
An example configuration file is `mnist_app.cfg`.

## Training an Example Application

```text
cd #(cloned directory)/npx_trainer
make mnist_app
```

## Checking the Trained Results

The training results will be generated in `#(cloned directory)/npx_trainer/result`.
