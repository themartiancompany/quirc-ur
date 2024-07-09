# Maintainer: Fabio Comuni <fabrix.xm@gmail.com>
pkgname=quirc
_libver=1.2
pkgver=1.2
pkgrel=2
pkgdesc="QR decoder library."
arch=('i686' 'x86_64')
url="https://github.com/dlbeer/quirc/"
license=('ISC')
depends=('libjpeg-turbo')
makedepends=('sdl')
checkdepends=()
source=("$pkgname-$pkgver"::"https://github.com/dlbeer/quirc/archive/v${pkgver}.tar.gz")
md5sums=('9fdda44c5b12cc721c2ca85abddf48de')

build() {
    cd "$pkgname-$pkgver"
    CFLAGS="$CFLAGS -fPIC"
    make libquirc.so quirc-scanner
}

package() {
    cd "$pkgname-$pkgver"
	   
    install -Dm644 "lib/quirc.h" "${pkgdir}/usr//include/quirc.h"
    install -Dm0755 "libquirc.so.${_libver}" "${pkgdir}/usr/lib/libquirc.so.${_libver}"
	ln -s "libquirc.so.${_libver}" "${pkgdir}/usr/lib/libquirc.so"
    install -Dm0755 quirc-scanner "${pkgdir}/usr//bin/quirc-scanner"
	install -D -m644 LICENSE -t "${pkgdir}/usr/share/licenses/${pkgname}"
}

