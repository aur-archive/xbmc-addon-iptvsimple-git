#
# Maintainer: JT Wilkinson <jowilkin at tu dot archserver dot org>
#
# Note: Apache ant and java must be on the path for make to succeed.
#       If either was installed as a dependency during the build, you
#       will need to log out and then log back in for the changes to
#       your path and JAVA_HOME environment variable to take effect.
#
pkgname=xbmc-addon-iptvsimple-git
_gitname=xbmc-addon-iptvsimple
pkgver=0.1.3
pkgrel=3
pkgdesc="Add support for Live TV watching and EPG TV Guide through IPTV provided by the Internet providers in exUSSR countries"
arch=('i686' 'x86_64')
url="https://github.com/afedchin/xbmc-addon-iptvsimple"
license=('GPL2')
depends=('gcc-libs' 'zlib' 'xbmc>=12.2')
makedepends=('git')
source=('git://github.com/afedchin/xbmc-addon-iptvsimple.git')
md5sums=('SKIP')

conflicts=('xbmc-addon-iptvsimple')
replaces=('xbmc-addon-iptvsimple')

pkgver() {
  cd "$_gitname"
  git describe --abbrev=0 | sed 's|v||g'
}

build() {
  cd "$_gitname"
  sh autogen.sh
  ./configure
  make
}

package() {
  cd "$_gitname"
  make DESTDIR="$pkgdir" install
  rm $pkgdir/usr/share/xbmc/addons/pvr.iptvsimple/Makefile
  rm $pkgdir/usr/share/xbmc/addons/pvr.iptvsimple/Makefile.am
  rm $pkgdir/usr/share/xbmc/addons/pvr.iptvsimple/Makefile.in
  rm $pkgdir/usr/share/xbmc/addons/pvr.iptvsimple/XBMC_IPTV_Simple.pvr
}
 
