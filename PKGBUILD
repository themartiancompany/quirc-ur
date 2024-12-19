# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Fabio Comuni <fabrix.xm@gmail.com>

_pkg=quirc
pkgname="${_pkg}"
_libver=1.2
pkgver=1.2
pkgrel=2
pkgdesc="QR decoder library."
arch=(
  'i686'
  'x86_64'
  'arm'
  'armv7l'
  'armv6l'
  'aarch64'
  'mips'
  'pentium4'
  'powerpc'
)
_http="https://github.com"
_ns="dlbeer"
url="${_http}/${_ns}/${_pkg}"
license=(
  'ISC'
)
depends=(
  'libjpeg-turbo'
)
makedepends=(
  'sdl'
)
provides=(
  "lib${_pkg}=${pkgver}"
)
checkdepends=()
_tarname="${_pkg}-${pkgver}"
source=(
  "${_tarname}::${url}/archive/v${pkgver}.tar.gz"
)
md5sums=(
  '9fdda44c5b12cc721c2ca85abddf48de'
)

build() {
  cd \
    "${_tarname}"
  CFLAGS="$CFLAGS -fPIC"
  make \
    "lib${_pkg}.so" \
    "${_pkg}-scanner"
}

package() {
  cd \
    "${_tarname}"
  install \
    -Dm644 \
    "lib/${_pkg}.h" \
    "${pkgdir}/usr//include/${_pkg}.h"
  install \
    -Dm0755 \
    "lib${_pkg}.so.${_libver}" \
    "${pkgdir}/usr/lib/lib${_pkg}.so.${_libver}"
  ln \
    -s \
    "lib${_pkg}.so.${_libver}" \
    "${pkgdir}/usr/lib/libquirc.so"
  install \
    -Dm0755 \
    "${_pkg}-scanner" \
    "${pkgdir}/usr/bin/${_pkg}-scanner"
  install \
    -Dm644 \
    "LICENSE" \
    -t \
    "${pkgdir}/usr/share/licenses/${pkgname}"
}
