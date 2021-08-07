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
sudo pacman -S git bc dkms
git clone https://github.com/sangnpq/pkgbuild-rtl8822cs.git
cd pkgbuild-rtl8822cs
makepkg

3. Unlink
rm <link>
ln -s file1 link1

4. Install manjaro with wifi to X96 Max+
# Solution 1:
    - Burn usb with image: Manjaro-ARM-minimal-vim3-21.03.img
    - Boot to manjaro
    - sudo pacman -Syyu # upgrade to newest linux
    - sudo pacman -S linux-vim-headers # upgrade headers the same to kernel, current 5.13.0-1-MANJARO-ARM
    - run step 2
    - modprobe 88x2cs
    - reboot
    - sudo pacman -S NetworkManager
    - edit /etc/NetworkManager/conf.d/dhcpcd.conf:
        [main]
        dhcp=dhcpcd
    - sudo systemctl start NetworkManager
    - nmcli device wifi connect WIFI\ TANG\ 5 password 0981026177
    - test: ping google.com

# Solution 2:
    - Burn usb with image: Manjaro-ARM-xfce-vim3-21.03.img
    - Boot to manjaro
    - sudo pacman -S linux-vim-headers
    - edit /lib/modules to 5.11.4-1-MANJARO-ARM
    - unlink
    - link to 
    - edit version to 5.11.4-1-MANJARO-ARM

