OpenSwitch ONIE Installer
=========================

To create the OpenSwitch ONIE installer, you first need to create the OpenSwitch root filesystem image. To create the `rootfs` image, it is required to use the Docker container generated by `opx_setup` (see [opx-build](https://github.com/open-switch/opx-build) for more information).

The build process has been automated by the `build.sh` script.

You must have the following repos to build ONIE installer:
- [opx-build](https://github.com/open-switch/opx-build)
- [opx-onie-installer](https://github.com/open-switch/opx-onie-installer)

To clone the repos, run the following commands:

    $ git clone https://github.com/open-switch/opx-build.git
    $ git clone https://github.com/open-switch/opx-onie-installer.git

After you clone the above repos, run the following commands to generate the ONIE installer image:

    $ cd opx-onie-installer
    $ ./build.sh

OpenSwitch `rootfs` is based on Debian 8.7 Jessie.

OpenSwitch Linux kernel is based on:
- Debian Jessie (Linux kernel version : 3.16.39-1), amd64
- CONFIG_GPIO_SYSFS is enabled in kernel config

The build process pulls the Linux kernel image already built from
[linux-image](https://dell-networking.bintray.com/opx-apt/pool/jessie/linux-image/).

The root file system mainly incorporates:
- openssh-server
- sudo
- default user name and password: admin/admin
- "admin" user added to sudo group

After successful build, the ONIE installer will be generated at "opx-onie-installer" (for example, `opx-onie-installer-x86_64_generic.bin`).

(c) 2017 Dell
