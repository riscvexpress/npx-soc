# NPX Installation Manual: Miscellaneous

## Checking NPX Version

```text
cd ${RVX_RELEASE_HOME}
make rvx_version
```

## Changing RTL Simulators

The RTL simulator used in NPX is automatically selected based on  
the executable file found in the system's `PATH` environment variable.  
If automatic selection fails,  
the simulator's installation path has not been added to the `PATH`
([Linux](conventions.md#adding-a-directory-to-the-path-variable) / [Windows](conventions.md#setting-environment-variables)).  
If multiple simulators are installed,  
you can manually select one by modifying the settings as described below.

1. Open ${RVX_RELEASE_HOME}/.rvx_tool_config with a text editor.

1. Set the value of `rtl_simulator` to one of the following:

    - xcelium, ncsim, modelsim, xsim

## Regenerating Path Configuration

`rvx_config_path.mh` stores the absolute paths of the NPX modules,  
such as `RVX_UTIL_HOME`, `RVX_SSW_HOME`, and `RVX_HWLIB_BASIC_HOME`.  
It is generated during `make install`,  
so you do not need to run this command in most cases.  
Run it only when you want to regenerate the file,  
for example, after moving the repository or changing the location of a module.

### Instruction @ Any OS

```text
cd ${RVX_RELEASE_HOME}
make path
```

> The path of each module is printed in the form of 'RVX_XXX_HOME = #(absolute path)'.  
> If a module is NOT found, a message is printed and it is excluded from the file.

Verify that 'rvx_config_path.mh' is generated.

## Updating

After the update, you need to clean the platform and restart with `make syn`.

### Instruction @ Any OS

If you have any work in progress, backup it.

```text
cd ${RVX_RELEASE_HOME}
make update
```

close and reopen the terminal.
