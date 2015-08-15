# Maintainer: Dylan Ferris <acerix at kanux dot com>

pkgname='catcoin-daemon'
pkgver=0.8.9
pkgrel=1
arch=('i686' 'x86_64')
url="http://catcoins.org/"
makedepends=('boost' 'automoc4' 'qrencode' 'miniupnpc')
license=('MIT')
source=("https://github.com/CatcoinOfficial/CatcoinRelease/archive/master.tar.gz"
        "catcoind@.service"
)

sha256sums=('SKIP'
            '9c0fb6c234dfe7482d34678f4648e706b49ba8c5dd836f43894b3041ea7955f8')

pkgdesc="Peer-to-peer network based digital currency (daemon)"
depends=(boost-libs miniupnpc openssl)
conflicts=(catcoin)

build() {
  cd "$srcdir/CatcoinRelease-master"
  make -f makefile.unix -C src CXXFLAGS="$CXXFLAGS" USE_UPNP=1
}

package() {
  install -Dm644 catcoind@.service "$pkgdir/usr/lib/systemd/system/catcoind@.service"
  cd "$srcdir/CatcoinRelease-master"
  install -Dm755 src/catcoind "$pkgdir"/usr/bin/catcoind
  install -Dm644 COPYING "$pkgdir/usr/share/licenses/$pkgname/COPYING"
}

