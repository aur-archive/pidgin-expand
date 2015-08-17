# Maintainer: SpepS <dreamspepser at yahoo dot it>

_name=expand
pkgname=pidgin-$_name
pkgver=0.6.0
pkgrel=2
pkgdesc="A pidgin plugin to replace all shortened links with their full equivalents."
arch=(i686 x86_64)
url="https://code.google.com/p/expand/"
license=('GPL')
depends=('pidgin')
makedepends=('intltool')
options=('!libtool')
source=("https://expand.googlecode.com/files/$_name-$pkgver.tar.gz")
md5sums=('45ebb67837afc9e3ff9ac8ff8f1d9fee')

build() {
  cd "$srcdir/$_name-$pkgver"

  # missing stuff
  install -d po
  for _f in Makefile.in.in POTFILES.in es.po; do
    wget https://expand.googlecode.com/hg-history/0.6.0/po/$_f -O po/$_f
  done;

  # add open ur1.ca service
  sed -i '/tl.gd/p;s/tl.gd/ur1.ca/' expand.c

  ./configure --prefix=/usr
  make
}

package() {
  cd "$srcdir/$_name-$pkgver"
  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
