# $Id: PKGBUILD 112796 2014-06-07 12:09:07Z bluewind $
# Maintainer: judd <jvinet@zeroflux.org>

_pkgbasename=libgpg-error
pkgname=lib32-$_pkgbasename
pkgver=1.13
pkgrel=1
pkgdesc="Support library for libgcrypt (32-bit)"
arch=(x86_64)
url="http://www.gnupg.org"
license=('LGPL')
depends=('lib32-glibc' $_pkgbasename)
makedepends=(gcc-multilib)
options=(!libtool)
source=(ftp://ftp.gnupg.org/gcrypt/libgpg-error/${_pkgbasename}-${pkgver}.tar.bz2)
  #ftp://ftp.franken.de/pub/crypt/mirror/ftp.gnupg.org/gcrypt/libgpg-error/${pkgname}-${pkgver}.tar.bz2)
sha1sums=('50fbff11446a7b0decbf65a6e6b0eda17b5139fb')


build() {
  export CC="gcc -m32"
  export CXX="g++ -m32"
  export PKG_CONFIG_PATH="/usr/lib32/pkgconfig"

  cd "${srcdir}"/${_pkgbasename}-${pkgver}
  ./configure --prefix=/usr --libdir=/usr/lib32
  make
}
check() {
  cd "${srcdir}"/${_pkgbasename}-${pkgver}
  make check
}

package() {
  cd "${srcdir}"/${_pkgbasename}-${pkgver}
  make DESTDIR="${pkgdir}/" install

  rm -rf "${pkgdir}"/usr/{include,share,bin}
}
