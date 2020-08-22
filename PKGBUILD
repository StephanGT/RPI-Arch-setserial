# Maintainer: Brian Bidulock <bidulock@openss7.org>
# Contributor: Giovanni Scafora <giovanni@archlinux.org>
# Contributor: Aurelien Foret <orelien@chez.com>

pkgname=setserial
pkgver=2.17
pkgrel=5
pkgdesc="Allows to change various attributes of a serial device on RPI's."
arch=('armv6h' 'armv7h')
url="http://setserial.sourceforge.net/"
license=('GPL')
depends=('glibc')
source=("http://downloads.sourceforge.net/sourceforge/${pkgname}/${pkgname}-${pkgver}.tar.gz"
        'setserial.patch'
        'ioctls.patch'
        'includes.patch')
sha256sums=('7e4487d320ac31558563424189435d396ddf77953bb23111a17a3d1487b5794a'   # setserial-2.17.tar.gz
            'a9f693059ad7d48a668fee762785f407755eea027ec4eb4c548fe0c6b72d623a'   # setserial.patch
            'f78fad248c72378d7451dbe5dc40b06ca1c645ab6ea0bf52e35100197dfc1d49'   # ioctls.patch
            '5cfc9eab1831f90a0b98d0f3b07254148b4097e08a2938f23bc83c03ac6167e8')  # includes.patch

prepare(){
  cd "${srcdir}/${pkgname}-${pkgver}"
  
  patch -Np1 -i "${srcdir}/setserial.patch"
  patch -Np1 -i "${srcdir}/ioctls.patch"
  patch -Np1 -i "${srcdir}/includes.patch"
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"

  ./configure --prefix=/usr \
              --mandir=/usr/share/man
  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  
  install -d ${pkgdir}/usr/{bin,share/man/man8}
  make DESTDIR="${pkgdir}" install
}
