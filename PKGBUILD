#Maintainer: Sebastien Duquette <ekse.0x@gmail.com>
pkgname=keimpx
pkgver=0.2
pkgrel=2
pkgdesc="tool to verify the usefulness of credentials across a network over SMB"
url="http://code.google.com/p/keimpx/"
license="APACHE"
depends=('impacket' 'pycrypto')
makedepends=('unzip')
arch=('i686' 'x86_64')
source=("http://keimpx.googlecode.com/files/keimpx-${pkgver}.zip"
        "setup.py-remove_py2exe.patch"
       )
md5sums=('f7451a4481e82f55d819437de9577f42'
         'bc2032ee6b40d21c15e151b4a487775a')

build() {
    cd $srcdir/$pkgname-$pkgver
    patch setup.py < $srcdir/setup.py-remove_py2exe.patch

}

package() {
cd $srcdir/$pkgname-$pkgver
python2 setup.py install --prefix=$pkgdir/usr
sed 's/\/usr\/bin\/env python/\/usr\/bin\/env python2/' -i keimpx.py
sed 's/keimpx_path =/keimpx_path = \"\/usr\/share\/keimpx\" #/' -i keimpx.py
install -D -m 755 keimpx.py $pkgdir/usr/bin/keimpx

mkdir -p $pkgdir/usr/share/keimpx
mv $pkgdir/usr/contrib $pkgdir/usr/share/keimpx
}
