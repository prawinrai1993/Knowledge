# VS Code Configuration and Debugging Setup

## VS Code Configurations

To enable remote debugging with VS Code, update the `program` and `miDebuggerPath` fields in the `launch.json` file. A sample configuration is provided below:

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "GDB Remote Debug",
            "type": "cppdbg",
            "request": "launch",
            "program": "/home/jarvis/development/poky/build/tmp/work/cortexa8hf-neon-poky-linux-gnueabi/example/0.1/image/usr/bin/example",
            "miDebuggerPath": "/opt/poky/5.0.4/sysroots/x86_64-pokysdk-linux/usr/bin/arm-poky-linux-gnueabi/arm-poky-linux-gnueabi-gdb",
            "args": [],
            "stopAtEntry": false,
            "cwd": "${workspaceFolder}",
            "environment": [],
            "externalConsole": false,
            "MIMode": "gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "miDebuggerServerAddress": "192.168.0.44:1234", // Replace with your target IP and gdbserver port
            "targetArchitecture": "arm" // Replace with your target architecture
        }
    ]
}
```

## Setup Target

### Add GDB to the Image
To include GDB in your Yocto image, add the following to your configuration:

```bash
EXTRA_IMAGE_FEATURES += "debug-tweaks tools-debug"
```

## Setup SDK

If the SDK is not already installed, follow these steps to generate and install it:

### Build the SDK
Run the following command in your Yocto environment:

```bash
bitbake <image-name> -c populate_sdk
```
Replace `<image-name>` with the name of the image you built (e.g., `core-image-minimal`).

### Install the SDK
Locate the SDK installer in the `tmp/deploy/sdk/` directory of your Yocto build. Run the installer with:

```bash
sh /path/to/yocto/build/tmp/deploy/sdk/poky-glibc-x86_64-core-image-minimal-arm-toolchain-<version>.sh
```

### Source the SDK Environment
Source the SDK environment setup script:

```bash
source /path/to/sdk/environment-setup-arm-poky-linux-gnueabi
```

### Locate GDB
Verify the GDB installation by running:

```bash
which arm-poky-linux-gnueabi-gdb
```

## Configure VS Code

### Create the `.vscode` Directory
If it doesn’t already exist, create a `.vscode` directory in your project root:

```bash
mkdir -p .vscode
```

### Create the `launch.json` File
Inside the `.vscode` directory, create a new file named `launch.json`:

```bash
touch .vscode/launch.json
```

Add the sample configuration provided above to this file.

## Start Debugging

### Launch `gdbserver` on the Target
Run the following command on the target device to start the GDB server:

```bash
nohup gdbserver :1234 /usr/bin/example > gdbserver.log 2>&1 &
```

### Start Debugging in VS Code
1. Open the Run and Debug panel in VS Code (Ctrl+Shift+D).
2. Select **GDB Remote Debug** from the dropdown menu.
3. Click the **Start Debugging** button (green play icon).

### Set Breakpoints
Set breakpoints in the VS Code editor and ensure they are hit when the application is running.




