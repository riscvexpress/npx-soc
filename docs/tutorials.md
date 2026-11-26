# Tutorials

Follow the tutorials in order, from running "Hello, World" on an RVX SoC to running a trained SNN on an FPGA.

## Before You Begin

1. Check the [Requirements](requirements.md).

1. Install RVX: [RVX: Installation](rvx-installation-manual-en.md)

    - snnForge is installed automatically, so it does not need to be installed separately.

## Tutorial List

| Step | Tutorial | Component | What you do |
| :---: | --- | --- | --- |
| 1 | [Hello](rvx-tutorials-hello.md) | RVX | Generate an SoC and print "Hello, World" in RTL simulation |
| 2 | [From Spike-Based Learning to FPGA Prototyping](npx/npx-tutorials-prototyping.md) | snnForge + RVX | Train an SNN and run it on the NeuGEMM SoC on an FPGA |
| 3 | [Running Software on a Prebuilt FPGA Prototype](npx/npx-tutorials-fpga-prototype.md) | snnForge + RVX | Train an SNN and run it on a prebuilt FPGA prototype, without license tools |
| 4 | [Training with snnForge](npx/npx-tutorials-xarvis.md) | snnForge | Train an example SNN with snnForge only, without hardware |

More RVX examples are in the [Example Platforms](rvx-tutorials-example.md).
