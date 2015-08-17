# Maintainer: Erdbeerkaese <erdbeerkaese@gmx.net>
# Contributor: Michael Pfeuti
# edited by tmjdone 
pkgname=texworks-0.4.4-r1004
pkgver=0.4.4_r1004
pkgrel=1
pkgdesc="A TeX IDE inspired by TeXShop."
arch=('i686' 'x86_64')
url="http://tug.org/texworks"
license=('GPL2')
depends=('poppler-qt' 'hunspell')
makedepends=()
optdepends=('texlive-core')
provides=('texworks')
conflicts=('texworks-svn')
install=texworks.install
source=("http://texworks.googlecode.com/files/texworks-${pkgver//_/-}.tar.gz")
md5sums=('e5e70cd9671f7f8d6ff7978ebcbaa9b4')
 
build() {
  cd ${srcdir}/texworks-`echo ${pkgver} | sed 's/_.*//g'`
 
  qmake
  make || return 1
}
 
package() {
  cd ${srcdir}/texworks-`echo ${pkgver} | sed 's/_.*//g'`
 
  # binary
  install -D -m755 ${pkgname} ${pkgdir}/usr/bin/${pkgname}

  # documentation & manual
  install -d ${pkgdir}/usr/share/doc/${pkgname}
  install -D -m644 README ${pkgdir}/usr/share/doc/${pkgname}
  install -D -m644 NEWS ${pkgdir}/usr/share/doc/${pkgname}
  cp -r manual/en ${pkgdir}/usr/share/doc/${pkgname}

  # icon
  install -D -m644 res/images/TeXworks.png \
    ${pkgdir}/usr/share/pixmaps/TeXworks.png

  # manpage
  install -D -m644 man/${pkgname}.1 ${pkgdir}/usr/share/man/man1/${pkgname}.1

  # desktop
  install -D -m644 ${pkgname}.desktop \
    ${pkgdir}/usr/share/applications/${pkgname}.desktop
}
 
# vim: set ft=sh ts=2 sw=2 et:
