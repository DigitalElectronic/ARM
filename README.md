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





