Build
#####

1. Setup Build Environment
**************************
1.1 Docker
==========


1.2 NFS
=======


2. Compile
*************
.. code:: console
    $ source ./settings.sh
    $ petalinux-build
    
2.1 Bootloader Compile
======================
.. code:: console

    $ petalinux-build -c u-boot -x clean
    $ petalinux-build -c u-boot -x cleansstate
    $ petalinux-build -c u-boot -x mrproper
    $ petalinux-config -c u-boot
    $ petalinux-build -c u-boot -x build
    
2.2 Kernel Compile
==================
.. code:: console

    $ petalinux-build -c kernel -x clean
    $ petalinux-build -c kernel -x cleansstate
    $ petalinux-build -c kernel -x mrproper
    $ petalinux-config -c kernel
    $ petalinux-build -c kernel -x build

3. Create Rootfs
****************
Small rootfs:

.. code:: console

    $ vim ./components/yocto/layers/meta-petalinux/recipes-core/images/petalinux-image-user.bb
    $ vim ./components/yocto/layers/meta-petalinux/recipes-core/images/petalinux-image-user.inc

    $ petalinux-build -c petalinux-image-user -x clean
    $ petalinux-build -c petalinux-image-user -x cleansstate
    $ petalinux-build -c petalinux-image-user -x mrproper
    $ petalinux-build -c petalinux-image-user -x build

Normal rootfs:

.. code:: console

    $ petalinux-build -c rootfs -x clean
    $ petalinux-build -c rootfs -x cleansstate
    $ petalinux-build -c rootfs -x mrproper
    $ petalinux-config -c rootfs
    $ petalinux-build -c rootfs -x build
    
Mount rootfs:

.. code:: console

    $ mkdir rootfs/
    $ sudo mount -t ext4 rootfs.ext4 rootfs/
    $ ls rootfs/
    $ sudo umount rootfs/

4. Create Boot Images
****************
.. code:: console

    $ cd ./petalinux_u96v2/bsp/images/linux
    $ petalinux-package --boot --fsbl zynqmp_fsbl.elf --fpga system.bit --pmufw pmufw.elf --u-boot --force

5. Flash Images
***************
.. code:: console

    $ cd ./petalinux_u96v2/bsp/images/linux

5.1 JTAG
========
.. code:: console

    $ petalinux-boot --jtag --kernel --fpga --bitstream system.bit

5.2 SD Card
===========
Partition:

.. code:: console

    $ sudo fdisk /dev/sdx
    $ sudo fdisk -l
    Device     Boot   Start      End  Sectors  Size Id Type
    /dev/sdx1          2048  2099199  2097152    1G  c W95 FAT32 (LBA)
    /dev/sdx2       2099200 31205375 29106176 13.9G 83 Linux

Format:

.. code:: console

    $ sudo mkfs -t ext4 /dev/sdx2

Specify mount directory:

.. code:: console

    $ sudo vim /etc/fstab
    UUID=5AA3-7D75 /media/louis/SD_BOOT vfat defaults 0 0
    UUID=2749244d-79ab-4493-87b1-2dace4105cbb /media/louis/SD_ROOTFS ext4 defaults 0 0

Insert SD Card and Check mount info:

.. code:: console

    $ dmesg | tail
    $ mount
    
Write boot images ``BOOT.BIN`` ``image.ub`` ``boot.scr`` to BOOT partition:

.. code:: console

    $ sudo cp BOOT.BIN image.ub boot.scr /media/louis/SD_BOOT

Write rootfs images to ROOTFS partition:

.. code:: console

    $ sudo dd if=rootfs.ext4 of=/dev/sdx2
    or
    $ make rootfs/
    $ mount -t ext4 rootfs.ext4 rootfs/
    $ sudo cp -rf rootfs/* /media/louis/SD_ROOTFS
    $ sync

4.3 NFS
=======
Host:

.. code:: console

    $ sudo cp BOOT.BIN boot.scr image.ub /mnt/shared/images/u96v2-v2021.2-images/linux/
    $ sudo cp rootfs.ext4 /mnt/shared/images/u96v2-v2021.2-images/linux/

Target Board:

.. code:: console

    $ ifconfig eth0 up x.x.x.x or ifup eth0 ( /etc/network/interface )
    $ cp /mnt/cifs/images/u96v2-v2021.2-images/linux/BOOT.BIN
    $ cp /mnt/cifs/images/u96v2-v2021.2-images/linux/image.ub
    $ reboot
