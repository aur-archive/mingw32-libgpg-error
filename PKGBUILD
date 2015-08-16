pkgname=mingw32-libgpg-error
pkgver=1.10
pkgrel=3
pkgdesc="Support library for libgcrypt (mingw32)"
arch=('any')
license=('GPL')
depends=(mingw32-runtime)
makedepends=(mingw32-gcc)
options=(!strip !buildflags !libtool)
url="http://ftp.gnupg.org"
source=("ftp://ftp.gnupg.org/gcrypt/libgpg-error/libgpg-error-${pkgver}.tar.bz2")
md5sums=('736a03daa9dc5873047d4eb4a9c22a16')

build() {
  cd "$srcdir/libgpg-error-$pkgver"
  unset LDFLAGS
  mkdir -p build && cd build
  ../configure \
    --prefix=/usr/i486-mingw32 \
    --host i486-mingw32 \
    --enable-static \
    --enable-shared
  make
}

package() {
  cd "$srcdir/libgpg-error-$pkgver/build"
  make install DESTDIR=$pkgdir
  i486-mingw32-strip $pkgdir/usr/i486-mingw32/bin/*.exe
  i486-mingw32-strip -x $pkgdir/usr/i486-mingw32/bin/*.dll
  i486-mingw32-strip -g $pkgdir/usr/i486-mingw32/lib/*.a
}

# vim:set ts=2 sw=2 et:
