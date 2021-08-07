# ARM
ARM-BOOT


Hi. In this web you can view how i boot ARM System from Windows for ARM32Chip.


The Image of ARM-Cpu.
------------------------
https://github.com/armbian/build.git


1º Steep in console Linux.
--------------------------------------------------------

apt-get -y -qq install git  
git clone --depth 1 https://github.com/armbian/build  
cd build 
./compile.sh    

--------------------------------------------------------


![stm32h747i-eval_1](https://user-images.githubusercontent.com/74788266/128599376-850917c3-2a7b-4482-8523-3efa1ee381d6.jpg)


1º  Parameters to select the options
--------------------------------------------------------

./compile.sh \
BOARD=orangepizero \
BRANCH=current \
RELEASE=focal \
BUILD_MINIMAL=yes \
BUILD_DESKTOP=no \
KERNEL_ONLY=no \
KERNEL_CONFIGURE=no \
CARD_DEVICE="/dev/sda"
__________________________________________________________

New configuration file config-example.conf and symlink config-default.conf will be created.

___________________________________________________________


KERNEL_CONFIGURE ( yes | no ):
yes: Automatically call kernel’s make menuconfig (add or remove modules or features).
no: Use provided kernel configuration provided by Armbian.
leave empty to display selection dialog each time.

REPOSITORY_INSTALL (comma-separated list): list of core packages which will be installed from repository.
Available options: u-boot, kernel, bsp, armbian-config, armbian-firmware.
Set to “” to use packages one from local output or build if not available.

BUILD_DESKTOP ( yes | no ):
yes: build image with minimal desktop environment.
no: build image with console interface only.

CARD_DEVICE ( /dev/sdX ): set to the device of your SD card. The image will be burned and verified using Etcher for CLI.

PROGRESS_DISPLAY ( none | plain | dialog ): way to display output of verbose processes - compilation, packaging, debootstrap.

________________________________________________________________________________________________________________________________________


What is FEL/NFS boot?

FEL/NFS boot mode is a possibility to test freshly created Armbian distribution without using SD card. It is implemented by loading u-boot, kernel, initrd, boot script and .bin/.dtb file via USB FEL mode and providing root filesystem via NFS share.

NOTE: this mode is designed only for testing. To use root on NFS permanently, use ROOTFS_TYPE=nfs option. NOTE: “hot” switching between kernel branches (default <-> dev/next) is not supported


Connect the UART console while it is off ;

./compile.sh 
KERNEL_ONLY=no
BOARD=cubietruck 
BRANCH=current P
ROGRESS_DISPLAY=plain 
RELEASE=jessie 
BUILD_DESKTOP=no 
ROOTFS_TYPE=fel


Go here if you get setting this.

( dir/userpatches/fel_post_prepare ) is executed once after setting up u-boot script and NFS share, you can use it to add extra stuff to boot.scr (like gpio set or setenv machid) based on device name.

___________________________________________________________________________________________________________________________


