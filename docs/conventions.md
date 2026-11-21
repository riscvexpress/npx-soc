# Conventions & Tips

Notation used in the manuals, and OS tips referenced from them.

## Conventions

- Any part starting with `#` should be replaced or modified according to your environment.
    - e.g. `cd #(cloned directory)` → `cd ~/work/rvx-tutorials`

- On Linux, use the `bash` shell for command-line operations.

- On Windows, use the `Windows Power Shell` for command-line operations.

## Skills for Linux

### Adding a Directory to the PATH Variable

1. Add the following line to your `.bashrc` file.

    ```text
    export PATH=$PATH:#(directory to add)
    ```

## Skills for Windows

### Running Windows PowerShell

1. Type `power` into the Windows Search bar.

1. Click on **Windows PowerShell**.

### Opening PowerShell in a Specific Directory

1. Navigate to the desired directory using Windows Explorer.

1. While holding down the Shift key, right-click in the folder.

1. Click on **Open PowerShell window here**.

### Setting Environment Variables

1. Open **System Properties**.

    - Type `SystemPropertiesAdvanced.exe` into the Windows Search bar, and run it.

    - Or, run `#(cloned directory)\install\open_system_properties.bat`.

    - Or, run `SystemPropertiesAdvanced.exe` from the command line.

1. Under the **Advanced** tab, click **Environment Variables**.

1. See the user variable section.

1. If the variable already exists, select it and click **Edit**.

1. If the variable doesn't exist, click **New** to create it.

1. Restart any open command prompts to apply the changes.
