# Contributor: dninja <dninja@gmail.com>
pkgname=lorcon
pkgrel=1
makedepends=('subversion')
pkgver=163
pkgdesc="Create what libradiate could have been: A generic library for injecting 802.11 frames, capable of injection via multiple driver frameworks, without forcing modification of the application code."
url="http://802.11ninja.net/lorcon/"
license="GPL"
source=()
md5sums=()
arch=('i686' 'x86_64')

_svntrunk=http://802.11ninja.net/svn/lorcon/trunk
_svnmod=lorcon

build() {
	cd $startdir/src
	msg "Updating lorcon SVN..."

	if [ -d $_svnmod/.svn ]; then
		(cd $_svnmod && svn up -r $pkgver)
	else
		svn co $_svntrunk --config-dir ./ -r $pkgver $_svnmod
	fi

        msg "SVN checkout done or server timeout"
	msg "Starting make..."
        cd $startdir/src/$_svnmod

	./configure --prefix=/usr
	make || return 1
	make DESTDIR="$startdir/pkg/" install
}
