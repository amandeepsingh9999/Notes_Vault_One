# Linux

## What is Linux?

Linux is a free and open-source, Unix-like operating system created by Linus Torvalds in 1991. He developed it as a free operating system for his personal computer. Today, Linux is widely used across different devices, from servers to smartphones.

---

## Key Concepts

### Kernel

The kernel is the core part of an operating system. It acts as a bridge between software and hardware, managing communication and ensuring that programs can interact with the hardware efficiently.

### Distribution (Distro)

Linux comes in many flavors, known as distributions or "distros." Each distro offers a different experience. Here’s a simple guide for beginners:
- **Start with**: **Linux Mint** (user-friendly and beginner-friendly).
- **Next step**: Try **Ubuntu** (popular and widely supported).
- **Advanced**: Explore **Arch Linux** (a build-it-yourself distro that teaches you how Linux works in-depth).

### Shell

A shell is a program that allows users to interact with the operating system via commands, either through a graphical user interface (GUI) or a terminal. Popular shell types include:
- **Bash**: The most widely used shell.
- **Fish**: The most beginner-friendly shell.
- **Z shell (Zsh)**: A highly customizable shell, preferred by advanced users.

### Files and Directories

- **File**: A file contains data such as text, images, videos, or executable code.
- **Directory**: A directory is like a folder that stores files or other directories. In Linux, directories are used to organize and structure all files and programs.

---

## Linux Directory Structure Overview

Linux has a standardized **File System Hierarchy**. Below is a summary of the key directories and their purposes:

### Root Directory (`/`)
The root directory is the top-level directory in the Linux file system. You can navigate to it using the command:
```bash
cd /
```

### Important Directories

| Directory       | Purpose                                                                                      | Examples/Notes                                  |
|-----------------|----------------------------------------------------------------------------------------------|------------------------------------------------|
| `/bin`          | Essential binaries (executables) for all users.                                             | Commands like `ls`, `gzip`, `curl`.            |
| `/sbin`         | System binaries for administrative tasks (root user only).                                  | Commands like `mount`, `userdel`.              |
| `/lib`          | Shared libraries required by binaries.                                                      | Common code libraries.                         |
| `/usr`          | Non-essential user applications and binaries.                                               | Contains its own `bin` and `sbin` directories. |
| `/usr/local`    | Locally compiled binaries, safe from package manager conflicts.                             | Custom software installations.                 |
| `/etc`          | Configuration files, usually text-based (`*.conf`).                                         | Editable system and software settings.         |
| `/home`         | User home directories, one per registered user.                                             | User-specific files and configurations.        |
| `/boot`         | Files needed to boot the system, including the Linux kernel.                                | Kernel and bootloader files.                   |
| `/dev`          | Device files representing hardware and drivers.                                             | Interface with hardware as files.              |
| `/opt`          | Optional or add-on software packages.                                                       | Rarely interacted with directly.               |
| `/var`          | Variable files that change during system operation, like logs and caches.                   | Dynamic system data.                           |
| `/tmp`          | Temporary files, cleared on reboot.                                                        | Short-lived files.                             |
| `/proc`         | Virtual filesystem created in memory by the kernel to track running processes.              | Does not exist on disk; kernel interface.      |

---

## Key Commands

Here are some essential Linux commands to get you started:

- `cd`: Change directory.
- `ls`: List the contents of a directory.
- `which <binary>`: Show the full path of a binary executable.

### Tips
- The `PATH` environment variable combines binaries from various directories, allowing you to run them from anywhere.
- The home directory shortcut `~` refers to your user's home folder.

---

This guide is designed to give you a friendly overview of Linux basics. Happy exploring!
