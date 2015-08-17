# Maintainer: jsteel <jsteel at vorx dot com>
# Contributor: Timur Antipin < mooxtim (at) yandex.ru >

pkgname=qgoogletranslate-svn
pkgver=26
pkgrel=2
pkgdesc="Translates text via Google Translate engine"
arch=('i686' 'x86_64')
url="http://code.google.com/p/qgoogletranslate"
license=('GPL2')
source=("qgoogletranslate.desktop")
md5sums=('3dc41f717e6d5e7e94014df42d12b1be')
conflicts=("qgoogletranslate")
provides=("qgoogletranslate")
depends=('qt')
makedepends=('subversion')

_svntrunk="http://qgoogletranslate.googlecode.com/svn/trunk"
_svnmod="qgoogletranslate"

build() {
  cd $srcdir
  if [ -d $_svnmod/.svn ]; then
    (cd $_svnmod && svn up -r $pkgver)
  else
    svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
  fi
  msg "SVN checkout done or server timeout"

  msg "Starting make..."
  cd $_svnmod
  qmake QGoogleTranslate.pro
  make
}

package() {
  install -Dm 755 $srcdir/$_svnmod/bin/QGoogleTranslate $pkgdir/usr/bin/qgoogletranslate
  install -Dm 644 $srcdir/$_svnmod/rc/icons/wicon.png $pkgdir/usr/share/pixmaps/qgoogletranslate_icon.png
  install -Dm 644 $srcdir/qgoogletranslate.desktop $pkgdir/usr/share/applications/qgoogletranslate.desktop
}
