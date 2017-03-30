OpenSwitch ONIE Installer
=========================

To create the OpenSwitch ONIE installer, you first need to
create the OpenSwitch root file system image. 
To create the `rootfs` image, it is required to use the Docker container 
generated by `opx_setup`. See `opx_setup` at [opx-build](https://github.com/open-switch/opx-build) for more information.

The build process has been automated by the `build.sh` script.

The following repos are required to build the ONIE installer:
- `opx-build`
- `opx-onie-installer`

After you clone the repos, run the following commands to generate
the ONIE installer image:

    $ cd opx-onie-installer
    $ ./build.sh

OpenSwitch `rootfs` is based on Debian 8.7 Jessie.

OpenSwitch Linux kernel is based on:
- Debian Jessie (Linux kernel version : 3.16.39-1), amd64
- CONFIG_GPIO_SYSFS is enabled in the kernel config

The build process pulls the Linux kernel image already built from
[linux-image](https://dell-networking.bintray.com/opx-apt/pool/jessie/linux-image/).

The root file system mainly incorporates:
- openssh-server
- sudo
- default user name and password : admin/admin
- "admin" user added to sudo group

After a successful build, the ONIE installer is generated as `opx-onie-installer`.
(`opx-onie-installer-x86_64_generic.bin`)

(c) Dell 2017
