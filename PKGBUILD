# $Id: PKGBUILD 153589 2015-12-17 13:04:51Z fyan $
# Maintainer: judd <jvinet@zeroflux.org>

_pkgbasename=libgpg-error
pkgname=lib32-$_pkgbasename
pkgver=1.21
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
sha1sums=('ef1dfb2f8761f019091180596e9e638d8cc37513')

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
