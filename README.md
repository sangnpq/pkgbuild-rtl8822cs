1. Install without makepkg(linux-vim kernel)
sudo pacman -S linux-vim-headers
sudo pacman -S git bc
git clone https://github.com/chewitt/rtl8822cs.git
cd RTL8822CS
make clean
make
sudo make install
reboot

2. Install with makepkg(linux-vim kernel)
sudo pacman -S linux-vim-headers
sudo pacman -S git bc dkms base-devel
git clone https://github.com/sangnpq/pkgbuild-rtl8822cs.git
cd pkgbuild-rtl8822cs
makepkg

3. Install manjaro with wifi to X96 Max+
    - Burn usb with image: Manjaro-ARM-xfce-vim3-21.03.img
    - Boot to manjaro
    - sudo pacman -Syyu # upgrade to newest linux
    - sudo pacman -S linux-vim-headers # upgrade headers the same to kernel, current 5.13.0-1-MANJARO-ARM
    - run step 2
    - modprobe 88x2cs
    - reboot
    - test: ping google.com

4. Boot in emmc
Note that the chances are these instructions won’t work for you and you’ll have to reflash Android but if they do work let us know and maybe we can at least work out which

    Install Manjaro onto an SD card and update it, get it booting with the correct dtb.
    Download install-aml59.sh
    copy install-aml59.sh to Manjaro sdcard /boot
    copy u-boot-gsking-x.bin to /boot/u-boot.emmc on SD card
    BOOT FROM SDCARD

cd /boot
sudo su
./install-aml59.sh # IGNORE ERORRS
Mount EMMC partitions

sudo mount LABEL=ROOT_EMMC /mnt
sudo mkdir /mnt/boot
sudo mount LABEL=BOOT_EMMC /mnt/boot
FIX BOOT

Edit /mnt/boot/extlinux/extlinux.conf and change the root disk label like so:

APPEND root=LABEL=ROOT_EMMC
FIX FSTAB

Edit or create /mnt/etc/fstab so it has a line like:

LABEL=BOOT_EMMC /boot vfat defaults 0 0

SHUTDOWN
REMOVE SDCARD
BOOT AND TEST

