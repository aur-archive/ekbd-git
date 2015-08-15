pkgname=ekbd-git
_pkgname=ekbd
pkgver=0.r30
pkgrel=3
pkgdesc="A vkbd (virtual keyboard) library using EFL"
arch=('i686' 'x86_64')
url="http://www.enlightenment.org"
license=('LGPL2.1')
depends=('efl' 'elementary' 'libx11')
makedepends=('git')
provides=('ekbd-svn')
conflicts=('ekbd-svn')
options=('!libtool')
source=('git://git.enlightenment.org/libs/ekbd.git')
md5sums=('SKIP')

pkgver() {
  cd ${srcdir}/${_pkgname}
  printf "0.r%s" "$(git rev-list --count HEAD)"
}

build() {
  cd ${srcdir}/${_pkgname}

  ./autogen.sh --prefix=/usr
  make
}

package() {
  cd ${srcdir}/${_pkgname}

  make DESTDIR=${pkgdir} install
  
  # install license files
  install -Dm644 ${srcdir}/${_pkgname}/COPYING \
  	${pkgdir}/usr/share/licenses/${pkgname}/COPYING
}
