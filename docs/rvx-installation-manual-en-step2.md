# NPX Installation Manual: Step 2

## Overview

Install the NPX environment in the cloned repository.

Check which installation process has issues.

## Install

### Objective

Install the Python3 libraries and set up the NPX environment.  
snnForge is installed automatically, so it does not need to be installed separately.

### Instruction

=== "Linux"

    ```text
    cd #(cloned directory)
    make install
    ```

    > The Python3 libraries are installed using pip.  
    > The NPX modules are downloaded, including snnForge in '#(cloned directory)/snn_forge'.  
    > 'rvx_config_path.mh' is generated.  
    > The udev rules are copied to /etc/udev/rules.d, which may ask for your sudo password.  
    > Check that the file ./rvx_setup.sh has been created.

    Add the line source #(cloned directory)/rvx_setup.sh to your .bashrc.

    > Be sure to replace #(cloned directory) with the absolute path before adding it.

    To apply the changes to .bashrc, close and reopen the terminal.

    > Now, #(cloned directory) is registered as ${RVX_RELEASE_HOME}.

=== "Windows"

    ```text
    cd #(cloned directory)
    make install
    ```

    > The Python3 libraries are installed using pip.  
    > The NPX modules are downloaded, including snnForge in '#(cloned directory)/snn_forge'.  
    > 'rvx_config_path.mh' is generated.  
    > The environment variable RVX_RELEASE_HOME is set.

    To apply the changes to the environment variable, close and reopen the terminal.

    > Now, #(cloned directory) is registered as ${RVX_RELEASE_HOME}.

## Install Check

### Objective

Check which installation process has issues.

### Instruction @ Any OS

```text
cd #(cloned directory)
make check_install
```

> Python3, pip, Git, make, and the shell used by make are checked.  
> Each result is printed with [ OK ], [WARN], or [FAIL].  
> The number of errors and warnings is printed at the end.

If [FAIL] is printed, follow the message and run this command again.
