# NPX Installation Manual: Step 1

## Overview

Clone the NPX design git repository and set up a Python3 environment for NPX.

Check whether Python3 is installed and configured properly.

## Git Repository Cloning

### Instruction @ Any OS

Open a terminal (bash on Linux, [PowerShell](conventions.md#opening-powershell-in-a-specific-directory) on Windows).

Navigate to the parent directory where you want to clone.

```text
git clone --recursive #(design repository URL)
cd #(cloned directory)
git submodule init
git submodule update
```

## Python3 Setup for NPX

### Objective

Install Python3 dedicated to NPX and set the python3 command used in NPX.

### Instruction

=== "Any OS"

    ```text
    cd #(cloned directory)
    make setup_python
    ```

    > If uv is not installed, it is installed first.  
    > Python 3.9.18 is installed using uv.  
    > A virtual environment is created in '#(cloned directory)/.rvx_venv'.

    Verify that 'rvx_config_python.mh' is generated.

    If the parent directory of #(cloned directory) has 'rvx_config_python.mh',  
    it is copied instead, and Python3 is NOT installed.

=== "Any OS (Alternative)"

    To use a Python3 already installed in your system, run the following instead.

    ```text
    cd #(cloned directory)
    make setup_python_manual
    ```

    > The Python3 executables found in your system are listed in 'rvx_config_python.mh'.  
    > The line that does NOT start with '#' is the one used in NPX.

    To use another one, open 'rvx_config_python.mh' in a text editor

    > Add '#' at the beginning of the current line.  
    > Remove '#' from the line you intend to use.  
    > Only one line must be left without '#'.

## Python3 Check

### Objective

Check the python3 command used in NPX.

### Instruction @ Any OS

```text
cd #(cloned directory)
make check_python
```

> Check that the path of the python3 command and its version are printed.
