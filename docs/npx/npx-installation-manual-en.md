# snnForge: Installation

snnForge is installed automatically when you install RVX.  
Follow this page only when you use snnForge alone, without RVX (e.g., [Training with snnForge](npx-tutorials-xarvis.md)).

## Prerequisite

- [Requirements](../requirements.md)

- Git and make: [Install - Prerequisite](../rvx-installation-manual-en-prerequisite.md)

## Cloning the snnForge Repository

```text
git clone --recursive https://github.com/riscvexpress/xarvis.git
```

> snnForge is in the `snn-forge` submodule, so `--recursive` is required.  
> If you have already cloned without it, run `git submodule update --init` in #(cloned directory).

On Windows, clone into a short path (e.g., `D:\work`).  
PyTorch installs files with long paths, and the installation fails if the full path exceeds 260 characters.

## Python3 Setup for snnForge

```text
cd #(cloned directory)
make setup_python
```

> Python 3.9.18 is installed using uv.  
> A virtual environment is created in '#(cloned directory)/.rvx_venv'.

If the parent directory of #(cloned directory) has 'rvx_config_python.mh',  
it is copied instead, and the same Python3 as the parent is used.  
To use a Python3 already installed in your system, run `make setup_python_manual` instead.  
For details, see [Install - Step1](../rvx-installation-manual-en-step1.md) of the NPX Installation Manual.

## Python3 Check

```text
cd #(cloned directory)
make check_python
```

## Installing snnTorch and Python Packages

### Instruction

=== "Linux"

    ```text
    cd #(cloned directory)
    make preinstall
    ```

    > The system libraries are installed using yum or apt, which may ask for your sudo password.

    ```text
    make install
    ```

=== "Windows"

    ```text
    cd #(cloned directory)
    make install
    ```

> The PyTorch build (CPU or CUDA) is selected automatically from `nvidia-smi`, and printed as `torch backend: ...`.  
> To choose it yourself, run e.g. `make install TORCH_BACKEND=cpu`.

## Setting Up Environment

### Instruction

=== "Linux"

    ```text
    cd #(cloned directory)
    make config
    ```

    > Check that the file ./rvx_setup.sh has been created.

    Add the line source #(cloned directory)/rvx_setup.sh to your .bashrc.

    > Be sure to replace #(cloned directory) with the absolute path before adding it.

    To apply the changes to .bashrc, close and reopen the terminal.

    > Now, #(cloned directory) is registered as ${XARVIS_HOME}.

=== "Windows"

    ```text
    cd #(cloned directory)
    make config
    ```

    > The environment variable XARVIS_HOME is set.

    To apply the changes to the environment variable, close and reopen the terminal.

    > Now, #(cloned directory) is registered as ${XARVIS_HOME}.
