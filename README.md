# CTF101 - Binary Exploitation (0)
> author: [@gatari](https://github.com/gatariee) & [@duckupus](https://github.com/duckupus)

## Introduction
Binary exploitation is one of the more "niche" CTF categories that is often overlooked by beginners, if not outright ignored due to its perceived difficulty; the goal of this guide is to provide a comprehensive introduction to binary exploitation, and to help beginners get started with this category.

## What is Binary Exploitation?
Binary exploitation involves finding vulnerabilities, and exploiting them over a **remote** server (not to be confused with [Reverse Engineering](https://ctf101.org/reverse-engineering/overview/)) to gain control over the server, or cause unintended behavior. This is done by manipulating the memory of the program to execute arbitrary code, or to change the flow of the program.

## Why Binary Exploitation?
Because it's very satisfying to pwn stuff, and if you get good enough at it; maybe you can find vulnerabilities for the NSA - [EternalBlue](https://en.wikipedia.org/wiki/EternalBlue#:~:text=EternalBlue%20is%20computer%20exploit%20software,computers%20connected%20to%20a%20network.) - [metasploit module]((https://github.com/rapid7/metasploit-framework/blob/master/modules/exploits/windows/smb/ms17_010_eternalblue.rb))

## Setup
For the benefit of those who have never touched pwn before, we'll start all the way from the beginning. 

We will **not** be going through the installation of any of the tools as the official documentation for the tools will probably do it better than I ever could.

### Linux Distribution
First, you'll definitely need a Linux machine. If you're on Windows, you can use the [Windows Subsystem for Linux (WSL)](https://learn.microsoft.com/en-us/windows/wsl/install), or a [Virtual Machine (VM)](https://www.vmware.com/topics/glossary/content/virtual-machine.html).

**SP DCDF Students**
* You most likely have access to [VMWare Workstation Pro](https://www.vmware.com/products/workstation-pro.html), which you can use to virtualize a Virtual Machine.

**Everyone Else**
* If you don't have access to VMWare Workstation Pro, you can use [VirtualBox](https://www.virtualbox.org/), which is free.

The Linux distribution you choose doesn't really matter, but I'd recommend using [Kali Linux](https://www.kali.org/), as it comes pre-installed with most of the tools you'll need for binary exploitation and cybersecurity in general.

### Tools
* **GDB** - The GNU Project Debugger, we'll be using this to debug our programs but you can use whatever debugger you're comfortable with.
    * Optional: [pwndbg](https://github.com/pwndbg/pwndbg) - A GDB plugin for exploit development.
* [**Pwntools**](https://github.com/Gallopsled/pwntools) - A CTF framework and exploit development library with Python bindings, which makes our lives a lot easier.
* [**Ghidra**](https://github.com/NationalSecurityAgency/ghidra) - A software reverse engineering (SRE) framework created and maintained by the NSA, otherwise known as a decomplier.
    * Useful for challenges that don't give you the source code, or for finding addresses from a Graphical User Interface (GUI).

* If the CTF you're participating in gives you local service files, you'll probably need:
    * [**Docker**](https://www.docker.com/) - A platform for developing, shipping, and running applications in containers.
        * Some CTFs give service files to the participants that are identical to those on their servers, I'd recommend virtualizing these containers locally so you don't overload the CTF server.
        * More on this later!~
    * [**Docker Compose**](https://docs.docker.com/compose/) - A tool for defining and running multi-container Docker applications.
        * In CTF101, most of the pwn challenges will have a `docker-compose.yml` file that you can use to run the challenge locally.
        * docker-compose is generally used to run complex applications with multiple services, but we'll be using it to dumb down the process of running a single pwn challenge locally (port mapping, bla bla bla).

* If you're doing a challenge that requires a [specific libc version](https://shellblade.net/files/docs/ret2libc.pdf), usually you'll have to patch the binary to use that libc locally on your own.
    * I like to use: [pwninit](https://github.com/io12/pwninit), but you can patch them manually with [patchelf](https://github.com/NixOS/patchelf) or [LD_PRELOAD](https://man7.org/linux/man-pages/man8/ld.so.8.html).

Next: [Pwning](./1.%20Pwning.md)