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
sudo pacman -S git bc
git clone https://github.com/sangnpq/pkgbuild-rtl8822cs.git
cd pkgbuild-rtl8822cs
makepkg

3. Unlink
rm <link>
ln -s file1 link1