# PetaLinux Installation and Usage Guide

PetaLinux is used for ATF and U-Boot compilation. Follow the steps below to download, install, and use PetaLinux.

## Download PetaLinux

Download the PetaLinux installer from the following link:

[PetaLinux v2023.2 Installer](https://www.xilinx.com/member/forms/download/xef.html?filename=petalinux-v2023.2-10121855-installer.run)

## Installation Steps

1. Set the correct permissions for the installer:
   ```bash
   chmod +wrx petalinux-v2023.2-10121855-installer.run
   ```

2. Run the installer and specify the installation directory:
   ```bash
   ./petalinux-v2023.2-10121855-installer.run --dir $PATH_TO_INSTALL
   ```

   If the installer prompts for dependency packages, install them first and then restart the installation process.

## Compiling U-Boot or ATF

1. Navigate to the U-Boot directory:
   ```bash
   cd u-boot
   ```

2. Source the PetaLinux environment:
   ```bash
   source $PETA_LINUX_PATH/settings.sh
   ```

3. Set up the environment variables for the build:
   ```bash
   export ARCH=arm
   export CROSS_COMPILE=$cross_compilername
   ```

4. Configure the build using the appropriate defconfig file:
   ```bash
   make defconfigfile
   ```

5. Build the project:
   ```bash
   make
   ```

For more details, refer to the documentation linked below:

- [Compilation Steps](http://192.168.0.80:6875/link/6#bkmrk-%C2%A0-5)

