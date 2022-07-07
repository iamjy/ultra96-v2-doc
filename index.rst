Welcome to Avnet-Ultra96-V2_ Documentation
##########################################

For this course on Xilinx Zynq UltraScale+ MPSoC development, we have selected the Avnet-Ultra96-V2_ platform as the reference development kit. There are several advantages in using this platform for an introductory course, enabling the potential reach to a wider audience:

- The Avnet Ultra96-V2 is powered by a Xilinx ZU3EG device that contains a fully featured processing system (PS) and a smaller programmable logic (PL) supported by free Xilinx development licenses.
- The Avnet Ultra96-V2 is one of the cheapest development kits based on the Xilinx Zynq UltraScale+ MPSoC devices, which makes it the ideal choice for both hobbyist and enterprise level courses.
- The Avnet Ultra96-V2 follows the 96 Boards standard promoted by Linaro for advanced ARM based platforms, so it supports a huge range of commercially available mezzanine and expansion cards.

.. _Avnet-Ultra96-V2: https://ohwr.org/project/soc-course/wikis/Avnet-Ultra96-V2

Bootloader ( U-boot )
*********************

* :doc:`configure </source/linux/u-boot/configure>`
    How to configure bootloader.
    
* :doc:`compile </source/linux/u-boot/compile>`
    How to compile bootloader.
    
* :doc:`development </source/linux/u-boot/development>`
    Guidelines and release planning and check dependencies.
    
* :doc:`changelog </source/linux/u-boot/changelog>`
    The bootloader development changelog.

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Bootloader

   /source/linux/u-boot/configure
   /source/linux/u-boot/compile
   /source/linux/u-boot/development
   /source/linux/u-boot/changelog

Kernel ( Linux )
****************

* :doc:`configure </source/linux/kernel/configure>`
    How to configure kernel.

* :doc:`compile </source/linux/kernel/compile>`
    How to configure kernel.

* :doc:`development </source/linux/kernel/development>`
    Guidelines and release planning and check dependencies.

* :doc:`changelog </source/linux/kernel/changelog>`
    The kernel development changelog.

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Kernel
   
   /source/linux/kernel/configure
   /source/linux/kernel/compile
   /source/linux/kernel/development
   /source/linux/kernel/changelog

RootFS ( Linux )
****************

* :doc:`build </source/linux/rootfs/build>`
    How to create a rootfs image
    
* :doc:`development </source/linux/rootfs/development>`
    Guidelines and release planning and check dependencies.
    
* :doc:`changelog </source/linux/rootfs/changelog>`
    The rootfs development changelog.

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: RootFS
   
   /source/linux/rootfs/build
   /source/linux/rootfs/development
   /source/linux/rootfs/changelog
   
Petalinux
*********

* :doc:`Build </source/xilinx/petalinux/build>`
    How to build in Petalinux
    
* :doc:`debug </source/xilinx/petalinux/debug>`
    Guidelines and release planning and check dependencies.
    
* :doc:`changelog </source/xilinx/petalinux/changelog>`
    The petalinux development environment changelog.
    
.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Petalinux

   /source/xilinx/petalinux/build
   /source/xilinx/petalinux/debug
   /source/xilinx/petalinux/changelog

Vitis IDE
*********

* :doc:`Build </source/xilinx/vitis_ide/build>`
    How to build using Vitis IDE tool

* :doc:`Debug </source/xilinx/vitis_ide/debug>`
    How to debug using Vitis IDE tool

.. toctree::
   :maxdepth: 2
   :hidden:
   :caption: Vitis IDE

   /source/xilinx/vitis_ide/build
   /source/xilinx/vitis_ide/debug
   
