# Requirements

- License Tools

    - Mixed-language RTL Simulator

        - Modelsim/QuestaSim

        - Xcelium/NCSim/Incisive

        - XSim (included with AMD Vivado)

    - AMD Vivado FPGA Tool

        - The required version depends on the FPGA board used ([FPGA Manual](rvx-fpga-manual-en.md)).

- A High-Performance Computer

    - A capable machine is required to run license tools efficiently.

    - The actual performance needed depends on the specific license tools being used.

    - Note: the NPX engine itself does not require a high-performance machine.

- Recommended OS Version

    - Must be compatible with license tools, not just NPX.

    - NPX-compatible OS

        - CentOS 7 / 8

        - Redhat 8 / 9

        - Ubuntu 18 / 20 / 22 (recommended) / 24

        - Windows 10 Home / Enterprise

        - Windows 11 Home

    - Virtualization environments are NOT recommended.

        - WSL and VirtualBox

        - USB-connected FPGA devices are not accessible.

- For Linux systems, the locale setting must be `en_US.UTF-8`.

    - If using a GUI, set the language format to United States.

    - Or, comment out the line `SendEnv LANG LC*` in `/etc/ssh/ssh_config`

        - i.e., add a `#` at the beginning).

- For Windows systems, Smart App Control must be turned off.

    - RVX uses unsigned binaries, which Smart App Control blocks.

    - On some versions of Windows 11, once it is turned off, it cannot be turned back on without reinstalling Windows.

    - Open **Windows Security** → **App & browser control** → **Smart App Control settings**, and select **Off**.

    - Smart App Control exists only on Windows 11. If it is not shown, nothing needs to be done.

- User Account

    - Linux: Requires `sudo` privileges

    - Windows: Requires administrator rights

- NPX Design Git Repository

    - Build your own design repository (See [Repository Setup Manual](rvx-repository-manual-en.md))

    - Or, use the repository provided by the instructor for the lecture
