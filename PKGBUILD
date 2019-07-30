# Maintainer: Florian Mayer <florian[dot]andrefranc[dot]mayer[at]fau[dot]de>
# at https://faui22m.cs.fau.de/orka/PKGBUILDs/libtapasco

pkgname=('libtapasco')
pkgdesc='Tapasco C API libraries'
pkgver=1.0
pkgrel=1
url='https://github.com/esa-tu-darmstadt/tapasco.git'
arch=('x86_64')
license=('BSD')
makedepends=('cmake' 'gcc' 'binutils')
depends=()

source=('git+https://github.com/esa-tu-darmstadt/tapasco.git')
sha256sums=('SKIP')
OPTIONS=(!strip)

_PREFIX=/opt/tapasco

build() {
   cd "${srcdir}"/tapasco

   local builddir="${srcdir}"/build-tapasco

   . setup.sh
   cd ..
   mkdir -p "${builddir}"
   cd "${builddir}"

   cmake -DCMAKE_C_COMPILER=gcc \
         -DCMAKE_CXX_COMPILER=g++ \
         -DCMAKE_INSTALL_PREFIX:PATH="${pkgdir}"/opt/tapasco \
         "${srcdir}/tapasco" .
   make CFLAGS=-fno-lto -j16
}

package_libtapasco() {
   local builddir="${srcdir}"/build-tapasco
   cd "${builddir}"
   make install -j4
}
