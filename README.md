# Open Media Transport Plugin

omtplugin is a cross platform Open Media Transport plugin for OBS (https://obsproject.com)

## Download

https://github.com/openmediatransport/omtplugin/releases

## Features

Send and receive high quality audio/video between OBS and other OMT compatible devices over a local network!

For more information about Open Media Transport in general, see the README here:
https://github.com/openmediatransport/

### OMT Source

Receive audio/video from OMT sources on the network.

Supports HDR workflows using the Color Space dropdown in the OMT Source properties.

### OMT Output

Send audio/video from the main OBS output.

This can be enabled from the Tools - OMT Output Settings menu.

This supports HDR OBS workflows and will send 10bit+ when P010 or P216 is enabled in OBS settings.

## Requirements

OBS 31 or higher

## Installation

### Windows

1. Download the Windows binaries from Releases on GitHub
2. Copy omtplugin.dll and libvmx.dll into the following folder:

```
C:\ProgramData\obs-studio\plugins\omtplugin\bin\64bit
```

This folder will need to be created if it does not already exist.

**Note:** Replace C: if Windows has been installed to a different drive.

### MacOS

1. Download the MacOS pkg from Releases on GitHub
2. Open the package and follow the instructions to install


### Linux

The install instructions below are based on Linux Distributions using the **APT** package manager.

1. Update the package manager

```
sudo apt update
```

2. Install dotnet 8

```
curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin --channel 8.0

echo 'export DOTNET_ROOT=$HOME/.dotnet' >> ~/.bashrc
echo 'export PATH=$PATH:$HOME/.dotnet' >> ~/.bashrc
source ~/.bashrc
```

3. Install Clang and Git

```
sudo apt install clang
sudo apt install git
```

4. Download the required repositories from Github into the home directory.

```
cd ~/
git clone https://github.com/openmediatransport/libvmx
git clone https://github.com/openmediatransport/libomtnet
git clone https://github.com/openmediatransport/omtplugin
```
5. Build libvmx 

```
cd ~/libvmx/build
chmod 755 buildlinuxx64.sh
./buildlinuxx64.sh
```
6. Build libomtnet 

```
cd ~/libomtnet/build
chmod 755 buildall.sh
./buildall.sh
```

7. Build omtplugin

```
cd ~/omtplugin/build
chmod 755 buildlinuxx64.sh
./buildlinuxx64.sh
```

8. Copy libraries into OBS plugins directory

```
sudo cp ~/omtplugin/bin/Release/net8.0/linux-x64/native/omtplugin.so /usr/lib/x86_64-linux-gnu/obs-plugins/
sudo cp ~/libvmx/build/libvmx.so /usr/lib/x86_64-linux-gnu/obs-plugins/
```
