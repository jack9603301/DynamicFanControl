# Server Dynamic Fan Control

This program implements temperature monitoring and forced fan overrides through continuous monitoring and IPMI control; it currently supports the following features:

- [x] Multi-curve control
- [x] Fan Device-Level Advanced Fan Speed ​​Mapping
- [x] Dual-threshold/Hysteresis control (dead-band control)
- [x] Support for unidirectional rising step input in the dead-zone (state machine lockout/hysteresis) state.

## Devices

- Dell(Currently only on the Dell R720)

## Contribution Guidelines

This program adheres to a fully C++23 style and must comply with the following specifications:
1. This program adheres to a fully C++23 style and must comply with the following specifications:
2. All class names follow the PascalCase naming convention.
3. All variable names within functions follow the SnakeCase naming convention.
4. One tab/code indentation equals 4 spaces.
5. Following the tree-like directory structure, all device actuators should be placed under the "Devices" directory, organized into subdirectories named after the server brands.

## Compiling from source

For a source-based installation, you should execute the following commands; this will fetch, compile, and install it on your system.

```
git clone https://github.com/jack9603301/DynamicFanControl
# or git clone git@github.com:jack9603301/DynamicFanControl.git
git checkout main
# or git checkout release-v{major}.{minor}
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_SYSCONFDIR=/etc -DCMAKE_INSTALL_LIBDIR=lib -DENABLE_SYSTEMD=ON ..
make
sudo make install
```

For a debug installation, we do not recommend installing it directly onto your system. Debug builds are typically larger than release versions,
and choosing a debug build—rather than installing from source—indicates that the build is intended specifically for debugging purposes, which implies that the control system may be unstable.
You should execute the following command; it will pull, compile, and install the software onto your system.

```
git clone https://github.com/jack9603301/DynamicFanControl
# or git clone git@github.com:jack9603301/DynamicFanControl.git
git checkout main
# or git checkout release-v{major}.{minor}
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=$PWD/dist/ -DCMAKE_BUILD_TYPE=Debug -DENABLE_CLANGD=ON -DENABLE_SYSTEMD=OFF ..
make
make install
```

For debug builds, we recommend enabling the `ENABLE_CLANGD` option; this generates a `compile_commands.json` file for LSP parsing, which helps your IDE (such as Neovim) locate code symbol definitions.
The explanations for the compilation options are as follows:

- CMAKE_INSTALL_PREFIX: The installation path for this program. for source-based installations, it is typically `/usr`.
- CMAKE_INSTALL_SYSCONFDIR: Provide the installation path for sysconfig. typically, this is `/etc`.
- CMAKE_INSTALL_LIBDIR: Specify the installation path for `libdir`; this can be relative to `CMAKE_INSTALL_PREFIX` (typically `lib`).
- CMAKE_BUILD_TYPE: The build type depends on your CMake configuration; we typically select the following value:
    - Debug
    - Release
- ENABLE_CLANGD: Generate compile_commands.json for IDEs
- ENABLE_SYSTEMD: Enable Systemd support

## Get help from the community

This is a personal hobby project, feel free to open issues or contact me directly for assistance. While I strive to respond as quickly as possible, please do not expect an immediate reply.
I may not be able to provide support for every scenario, as the software was created solely to handle server fan control and noise reduction. 
You are welcome to share any suggestions or submit a pull request (PR) to add features you find valuable.
You can also initiate community discussions and suggestions directly via GitHub issues or by starting a discussion topic.

email: jack9603301@qhjack.top

## Donate
This project was developed based on personal needs. If you would like to make a personal donation, please feel free to contact me.
You can use the GitHub donation button to contribute, or contact me directly for customized payment options and bank account details to send a tip or donation.

My email address is jack9603301@qhjack.top.

However, I only accept donations made in fiat currency. once the donation is complete, the funds are treated as personal income. 
If you would like to offer support, please feel free to contact me to make a donation—you could even just buy me a coffee.
