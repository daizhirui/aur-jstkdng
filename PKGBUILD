# Maintainer: Alad Wenter <https://wiki.archlinux.org/index.php/Special:EmailUser/Alad>
# Contributor: Marcel Korpel <marcel[dot]korpel[at]gmail>
# Contributor: Thomas Dziedzic < gostrc [at] gmail >
# Contributor: breakdown <breakdown[at]archlinux[dot]us>
# Contributor: fs4000 <matthias_dienstbier[at]yahoo[dot]de>
# Contributor: William Heinbockel <wheinbockel[at]gmail[dot]com>
# Contributor: Adrian C. <anrxc..sysphere.org>

pkgname=xf86-video-intel-git
pkgver=2.99.917+560+gd167280
pkgrel=1

pkgdesc="X.org Intel i810/i830/i915/945G/G965+ video drivers"
url="http://intellinuxgraphics.org/"
arch=("i686" "x86_64")
license=("custom")

depends=("intel-dri" "libxvmc" "libpciaccess" "libdrm" "dri2proto" "xcb-util" "libxfixes" "udev")
makedepends=("git" "xorg-server-devel" "X-ABI-VIDEODRV_VERSION=20" "libx11"
             "xf86driproto" "glproto" "resourceproto" "scrnsaverproto" "mesa" "libxrender")
provides=("xf86-video-intel")
conflicts=("xf86-video-intel")
replaces=("xf86-video-intel")

options=("!libtool" "!strip")
source=($pkgname::git://anongit.freedesktop.org/git/xorg/driver/${pkgname%-git})
sha1sums=('SKIP')

pkgver() {
    cd "$pkgname"
    git describe --always | sed 's|-|.|g'
}


build() {
    cd "$pkgname"
    ./autogen.sh --prefix=/usr \
		 --enable-xvmc \
		 --enable-sna
    # --enable-glamor
    # --enable-kms-only
    make
}

check() {
    cd "$pkgname"
    make check
}

package () {
    cd "$pkgname"
    make DESTDIR="$pkgdir" install

    install -Dm644 COPYING "$pkgdir"/usr/share/licenses/$pkgname/COPYING
}
