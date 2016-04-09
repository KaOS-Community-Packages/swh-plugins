pkgname=swh-plugins
pkgver=0.4.15
pkgrel=1
pkgdesc="A collection of LADSPA plugins"
arch=('x86_64')
url="http://plugin.org.uk/ladspa-swh/docs/ladspa-swh.html"
license=('GPL')
depends=('fftw' 'ladspa')
makedepends=( 'libxml2' 'perl-xml-parser')
source=("http://plugin.org.uk/releases/$pkgver/$pkgname-$pkgver.tar.gz")
md5sums=('2fbdccef2462ea553901acd429fa3573')

prepare() {
  sed -i 's|for (i = 0; i < FFT_LENGTH/2; i++) {|comp[0] *= coefs[0];for (i = 1; i < FFT_LENGTH/2; i++) {|g'  $srcdir/$pkgname-$pkgver/mbeq_1197.c
}

build() {
  cd $srcdir/$pkgname-$pkgver
  export CFLAGS="$CFLAGS -fPIC"
  export CXXFLAGS="$CFLAGS"
  ./configure  --prefix=/usr
  make
}

package() {
  cd $srcdir/$pkgname-$pkgver
  make DESTDIR="$pkgdir/" install
}
