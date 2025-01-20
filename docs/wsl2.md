# Preparing the Windows environment

This guide has been written with :simple-apple: macOS and :simple-linux: Linux
operating systems in mind. If you use :fontawesome-brands-windows: Windows, you
might encounter issues.

This guide will help you to set up a Linux environment on your Windows computer
to be able to follow the workshop (and beyond), through the
[Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/).

## Install and configure Windows Subsystem for Linux (WSL)

This section will guide you through the process of installing and configuring
Windows Subsystem for Linux (WSL) on your Windows installation.

### Install WSL

WSL is a compatibility layer for running Linux binary executables natively on
Windows. It is a very useful tool for developers who want to use Linux tools and
utilities on Windows.

To install WSL, search "_PowerShell_" in the Start menu, right-click on it, and
select _"Run as administrator"_:

Then, run the following command in the terminal:

!!! warning

    If the following command displays the help message, proceed to the next section.

```powershell
# Install WSL without specifying a distribution
wsl --install --no-distribution
```

The output should be similar to this:

```text
Installing: Virtual Machine Platform
Virtual Machine Platform has been installed.
Installing: Windows Subsystem for Linux
Windows Subsystem for Linux has been installed.
Installing: Windows Subsystem for Linux
Windows Subsystem for Linux has been installed.
The requested operation is successful. Changes will not be effective until the system is rebooted.
```

Restart your computer once the installation is complete.

### Update WSL

WSL can still be in version 1 and must be updated to version 2.

To do so, open PowerShell as administrator and run the following command in the
terminal:

```powershell
# Check for WSL updates
wsl --update
```

If there are updates available, you will be prompted to download and install
them.

Set the WSL default version to 2 by running the following command in the
terminal:

```powershell
# Set WSL default version to 2
wsl --set-default-version 2
```

The output should be similar to this:

```text
For information on key differences with WSL 2 please visit https://aka.ms/wsl2
The operation completed successfully.
```

### Install a Linux distribution

WSL supports multiple Linux distributions, but we recommend installing Ubuntu if
you are not familiar with Linux as it is a very user-friendly distribution and
is widely used.

```powershell
# Install Ubuntu
wsl --install --distribution Ubuntu
```

Once the installation is complete, you can set up a username and password for
the Ubuntu distribution.

!!! tip

    While setting up your password,
    **it is expected that you will not see any characters on the screen**. This is a
    security feature of the terminal. Even though you do not see the characters you
    type (e.g., `p@ssw0rd`), they are still being entered. So, make sure to remember
    your password as you will need it later.

We recommend using an username in lowercase letters without space for
simplicity.

Once you have set up your username and password, Ubuntu will be started, and you
will be able to run Linux commands in the terminal.

The output should be similar to this:

```text
Installing: Ubuntu
Ubuntu has been installed.
Launching Ubuntu...
Installing, this may take a few minutes...
Please create a default UNIX user account. The username does not need to match your Windows username.
For more information visit: https://aka.ms/wslusers
Enter new UNIX username: ludelafo
New password:
Retype new password:
passwd: password updated successfully
Installation successful!
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

Welcome to Ubuntu 22.04.3 LTS (GNU/Linux 5.10.102.1-microsoft-standard-WSL2 x86_64)

 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage

This message is shown once a day. To disable it please create the
/home/ludelafo/.hushlogin file.
ludelafo@win-10:~$
```

To exit the Ubuntu terminal, you can run the following command:

```bash
# Exit the Ubuntu terminal
exit
```

WSL is now installed and configured on your Windows machine. You can use it to
run Linux commands and utilities on Windows.

## Linux and Windows filesystems

When you access the Ubuntu terminal, you will be in the home directory of your
Ubuntu user. Your Ubuntu home directory is located in the `/home` directory. The
`~` symbol represents the home directory of your Ubuntu user.

You can access your Windows files in the `/mnt` directory. For example, you can
access your Windows `C:\Users` drive in the `/mnt/c/Users` directory, however,
we do not recommend to manipulate your files from the File Explorer on Windows.
Check the [Tips and tricks](#tips-and-tricks) section for more information.

Windows has added an entry to the File Explorer sidebar for the Ubuntu
distribution. You can access your Ubuntu files in the
`\\wsl$\Ubuntu\home\YOUR_USERNAME` directory.

!!! danger

    We highly recommend to
    **never manipulate your files from the File Explorer on Windows**. Use the
    Ubuntu terminal instead to avoid permission issues and odd file behaviors.

## Install and configure Windows Terminal

### Install Windows Terminal

Windows comes with a terminal application called _"Command Prompt"_.

It is a very basic terminal application that does not support many features that
are available in modern terminal applications. Microsoft has developed a new
terminal application called Windows Terminal that is available for Windows
users.

The Windows Terminal is a new, modern, fast, efficient, powerful, and productive
terminal application for users of command-line tools and shells like Command
Prompt, PowerShell, and WSL.

You can download it from the Microsoft Store:
[Windows Terminal](https://www.microsoft.com/p/windows-terminal/9n0dx20hk701) or
the GitHub releases page:
[Windows Terminal Releases](https://github.com/microsoft/terminal/releases)
(download the `.msixbundle` file).

Install it and open it.

### Configure Windows Terminal

By default, Windows Terminal will open PowerShell. Now that you have installed
Windows Terminal, you can configure it to open WSL by default.

Access the settings by clicking on the down arrow in the title bar and selecting
"Settings". Set the two following settings:

- **Default profile**: Ubuntu
- **Default terminal application**: Windows Terminal

Press **Save** to save the settings.

Close Windows Terminal and open it again. It should now open Ubuntu by default.

You now have a modern terminal application that supports multiple tabs, multiple
shells, and many other features.

You now have access to a Linux distribution on your Windows machine. You can use
it to run Linux commands and utilities on Windows.

## Update Ubuntu

Before starting the installation of the development environment, make sure that
your Ubuntu installation is up to date. You can update Ubuntu by running the
following commands in the terminal. You might need to enter your password when
running the commands:

!!! tip

    The `sudo` command is used to run commands with superuser privileges. You will
    be prompted to enter your password when running a command with `sudo`.

    This is a security feature of Linux to prevent unauthorized access to the
    system.

!!! tip

    All Linux distributions come with a package manager that is used to install,
    update, and remove packages. The package manager for Ubuntu is called `apt`.

    The package manager uses a package list to know which packages are available for
    installation. You can then install any package from the package list using the
    package manager.

```bash
# Update the package list
sudo apt update

# Upgrade the installed packages
sudo apt upgrade
```

Press `y` when prompted to confirm the upgrade.

All packages will be upgraded to the latest version.
