# How to build LisaEm on Windows

## Overview
The build instructions below have been tested on Windows 11, with the latest LisaEm code in the "master" branch, in Feb 2025.

The build process involves installing the latest Cygwin version with a set of required packages, checking out the LisaEm code from this repository, building the wxWidgets library from sources, building the LisaEm binary and tools, and installing them in in Windows.

Note: The generated binaries will run on 64-bit x86 Windows systems. Building for 32-bit x86 processors and 32-bit Windows OS is no-longer suported. If you wish to use LisaEm on such systems, please download an older 32-bit build from https://lisa.sunder.net/downloads.html.

## 1. Install Cygwin
Cygwin is a Linux-like command line enviringment for Windows.

Please download and install the latest version of Cygwin from  https://cygwin.com/install.html , along with the following packages: `wget,git,upx,netpbm,xz,zip,unzip,mingw64-x86_64-gcc-core,mingw64-x86_64-gcc-debug-info,mingw64-x86_64-gcc-g++,mingw64-x86_64-gcc-objc,gcc-core,gcc-g++,make`.

Alternatively, for Cygwin beginners, we have an automated unattended script wihich does that for you. Follow these steps:
  * Download file setup-x86_64.exe from https://cygwin.com/install.html into your "Downloads" folder.
  * Open a command prompt and run the following commands:
      ```
      cd Downloads
      powershell Invoke-WebRequest -Uri https://raw.githubusercontent.com/arcanebyte/lisaem/refs/heads/master/scripts/cygwin-install.bat -OutFile cygwin-install.bat
      cygwin-install.bat setup-x86_64.exe
      ```

      The Cygwin installer window should open and it should start downloading the required packages. Please wait for its completion; it should exit by itself. At the end, Cygwin will be installed into folder `C:\cygwin`, along with all packages necessary for building LisaEm. To customize your installation, see file [cygwin-install.bat](scripts/cygwin-install.bat).

## 2. Open a Cygwin command window
  * Start program "Cygwin64 Terminal", or
  * Open a new Command Promt and type: `C:\Cygwin\cygwin`.
  * You are in Cygwin now.
    
  Note: Your "home folder" (accessible via `cd ~`) is also accessible in Windows Explorer: you can find it in `C:\cygwin\home\<your-windows-username>`.

## 3. Download the LisaEm souces from GitHub

```
git clone https://github.com/arcanebyte/lisaem.git
```

This will download the LisaEm sources into new subfolder `LisaEm`.

## 4. Download and build the wxWidgets binaries
Run the following commands:

```
cd ~/LisaEm/scripts
./build-wx3.1.5-cygwin-windows.sh
```

This will download file `wxWidgets-3.1.5.tar.bz2` , expand it into subfolder `wxWidgets-3.1.5`, build it in subfolder `wxWidgets-3.1.5/build-msw`, install wxWidgets into folder `/usr/local/wx3.1.5-msw` and delete the temporary build folder above. Upon success, it should print e.g. `Default config is msw-unicode-static-3.1`.

## 5. Build the LisaEm binaries
Run the following commands:

```
cd ~/LisaEm
./build.sh build
```

This will compile and generate the LisaEm executable file `bin/lisaem.exe`, along with other tools in the same `bin` subfolder.

## 6. Installing the LisaEm binaries on Windows
UNFINISHED



