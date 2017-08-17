# Maintainer: Eric Vidal <eric@obarun.org>
# based on the original https://git.archlinux.org/svntogit/community.git/tree/trunk?h=packages/cgmanager
# 						Maintainer: Sergej Pupykin <pupykin.s+arch@gmail.com>
pkgname=cgmanager
pkgver=0.41
pkgrel=2
pkgdesc="Another daemon for managing control groups"
arch=(x86_64)
url="https://linuxcontainers.org/"
license=('GPL')
depends=('libnih')
makedepends=('help2man')
source=("https://linuxcontainers.org/downloads/cgmanager/cgmanager-$pkgver.tar.gz")
sha256sums=('29b155befb3ac233d5d29dbca7c791c8138bab01bfa78ea4757ebb88ce23b458')
validpgpkeys=('6DD4217456569BA711566AC7F06E8FDE7B45DAAC') # Eric Vidal

build() {
	cd "$srcdir/$pkgname-$pkgver"
#	./bootstrap.sh
	./configure --prefix=/usr \
	--sbindir=/usr/bin \
	--libdir=/usr/lib
	make
}

package() {
	cd "$srcdir/$pkgname-$pkgver"
	make DESTDIR="$pkgdir/" install
	mv "$pkgdir"/lib/* "$pkgdir"/usr/lib/
	rmdir "$pkgdir"/lib
}
