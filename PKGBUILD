_gitname=rtl8822cs
pkgname=dkms-rtl8822cs
pkgver=2020.11.20
pkgrel=2
pkgdesc="DKMS driver for the Realtek RTL8822CS wifi chip"
arch=('any')
url="https://github.com/chewitt/$_gitname"
license=(‘GPL’)
install=dkms-rtl8822cs.install
#depends=('dkms' 'linux>=4.14' 'linux-headers>=4.14')
depends=('dkms')
makedepends=('git' 'bc')
options=(!strip)
source=("git+${url}.git" "dkms.conf")

md5sums=('SKIP' 'SKIP')

prepare() {
echo "Please be sure to install the kernel header files that match your kernel (e.g. linux-headers / linux-vim-headers / linux-aml-headers) before trying to install this driver!)"
_MAJOR_VERSION=$(uname -r | awk -F '.' '{print $1}')
_MINOR_VERSION=$(uname -r | awk -F '.' '{print $2}')
if [ $_MAJOR_VERSION -eq 5 ] && [ $_MINOR_VERSION -ge 12 ] || [ $_MAJOR_VERSION -ge 6 ] ; then
    echo "Patching source for kernel >= 5.12 ..."
    sed -i s/GRO_DROP/GRO_MERGED_FREE/ $(pwd)/rtl8822cs/os_dep/linux/recv_linux.c
    echo "Done patching!"
fi
}

pkgver() {
cd "$srcdir/$_gitname"
git log -1 --format="%cd" --date=short | sed 's|-|.|g'
}

package() {
cp dkms.conf "$srcdir/$_gitname/"
cd "$srcdir/$_gitname"
mkdir -p "$pkgdir/usr/src/rtl8822cs-$pkgver"
cp -r . "$pkgdir/usr/src/rtl8822cs-$pkgver"
}