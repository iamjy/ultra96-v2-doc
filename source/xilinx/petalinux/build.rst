Build
#####

0. Setup Build Environment
**************************
.. code:: console

    $ source ./settings.sh
    $ petalinux-build


1. Full Build
*************
.. code:: console

    $ petalinux-build
    
1.1 Bootloader Compile
======================
.. code:: console

    $ petalinux-build -c u-boot -x clean
    $ petalinux-build -c u-boot -x cleansstate
    $ petalinux-build -c u-boot -x mrproper
    $ petalinux-config -c u-boot
    $ petalinux-build -c u-boot -x build
    
1.2 Kernel Compile
==================
.. code:: console

    $ petalinux-build -c kernel -x clean
    $ petalinux-build -c kernel -x cleansstate
    $ petalinux-build -c kernel -x mrproper
    $ petalinux-config -c kernel
    $ petalinux-build -c kernel -x build

1.3 Make Rootfs
================
.. code:: console

    $ vim ./components/yocto/layers/meta-petalinux/recipes-core/images/petalinux-image-user.bb
    $ vim ./components/yocto/layers/meta-petalinux/recipes-core/images/petalinux-image-user.inc
    $ petalinux-build -c petalinux-image-user -x clean
    $ petalinux-build -c petalinux-image-user -x cleansstate
    $ petalinux-build -c petalinux-image-user -x mrproper
    $ petalinux-build -c petalinux-image-user -x build
    or
    $ petalinux-build -c rootfs -x clean
    $ petalinux-build -c rootfs -x cleansstate
    $ petalinux-build -c rootfs -x mrproper
    $ petalinux-config -c rootfs
    $ petalinux-build -c rootfs -x build

2. Create Images
****************
.. code:: console

    $ cd ./petalinux_u96v2/bsp/images/linux
    $ petalinux-package --boot --fsbl zynqmp_fsbl.elf --fpga system.bit --pmufw pmufw.elf --u-boot --forc

3. Flash Images
***************
.. code:: console

    $ cd ./petalinux_u96v2/bsp/images/linux

3.1 JTAG
========
.. code:: console

    $ petalinux-boot --jtag --kernel --fpga --bitstream system.bit

3.2 SD Card
===========
