# CAO-OS
source code for 64-bit x86 operating system kernel

# Sample Print Output
![SEECS](SEECS.PNG)

## Prerequisites

 - A text editor such as [VS Code](https://code.visualstudio.com/).
 - [Docker](https://www.docker.com/) for creating the build-environment.
 - [Qemu](https://www.qemu.org/) for emulating the operating system.

## Setup

Build an image for the build-environment:
 - `docker build buildenv -t myos-buildenv`

## Build

Enter build environment:
 - Linux or MacOS: `docker run --rm -it -v "$pwd":/root/env myos-buildenv`
 - Windows (CMD): `docker run --rm -it -v "%cd%":/root/env myos-buildenv`
 - Windows (PowerShell): `docker run --rm -it -v "${pwd}:/root/env" myos-buildenv`

Build for x86 (other architectures may come in the future):
 - `make build-x86_64`

To leave the build environment, enter `exit`.

## Emulate

Emulate the operating system using [Qemu](https://www.qemu.org/): (Don't forget to add qemu to your path!)

 - `qemu-system-x86_64 -cdrom dist/x86_64/kernel.iso`

## Cleanup

Remove the build-evironment image:
 - `docker rmi myos-buildenv -f`
