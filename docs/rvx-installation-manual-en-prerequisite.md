# NPX Installation Manual: Prerequisite

## Overview

Install the prerequisite programs: make and Git (and curl or wget on Linux).  
These are commonly used programs,  
so any installation method is acceptable as long as the [Objective] is met.

## Prerequisite Programs

=== "Linux"

    ### Objective

    Install make, curl or wget, and Git.

    ### Check

    ```text
    make --version
    curl --version or wget --version
    git --version
    ```

    ### Instruction @ CentOS

    ```text
    sudo yum install make curl git
    ```

    ### Instruction @ Ubuntu

    ```text
    sudo apt-get install make curl git
    ```

    Only one of curl and wget is required.

=== "Windows"

    ### Objective

    Install Scoop, and then install Git and make using it.

    ### Check

    ```text
    make --version
    git --version
    ```

    ### Instruction

    Open PowerShell ([how to](conventions.md#running-windows-powershell)).

    ```text
    Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
    Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
    scoop install git make
    ```

    close and reopen the terminal.
