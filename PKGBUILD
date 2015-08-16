# Maintainer: skydrome <skydrome@i2pmail.org>
# Contributor: skydrome <skydrome@i2pmail.org>

pkgname=java-service-wrapper-src
pkgver=3.5.17
pkgrel=1
pkgdesc="Enables a Java Application to be run as a Windows Service or Unix Daemon"
url="http://wrapper.tanukisoftware.com"
arch=('i686' 'x86_64' 'armv6h')
license=('GPL2')
makedepends=('apache-ant')
conflicts=('java-service-wrapper')
provides=('java-service-wrapper')
source=("http://wrapper.tanukisoftware.com/download/3.5.17/wrapper_${pkgver}_src.tar.gz")
sha256sums=('e4432fdef6cfc1d19d8571429c8554748ec21ffa9fecabd464f5f12ec5160f9b')

build() {
    cd "${srcdir}/wrapper_${pkgver}_src"
    [[ "$CARCH" = "x86_64" ]] && _arch=64 || _arch=32
    ant -Dbits=${_arch} jar compile-c-unix
}

package() {
    cd "${srcdir}/wrapper_${pkgver}_src"
    install -Dm644 doc/wrapper-community-license-1.1.txt "${pkgdir}/usr/share/licenses/java-service-wrapper/LICENSE"
    install -Dm755 bin/wrapper       "${pkgdir}/usr/bin/java-service-wrapper"
    install -Dm644 lib/libwrapper.so "${pkgdir}/usr/lib/java-service-wrapper/libwrapper.so"
    install -Dm644 lib/wrapper.jar   "${pkgdir}/usr/share/java/wrapper-${pkgver}.jar"
    ln -s /usr/share/java/wrapper-${pkgver}.jar "${pkgdir}/usr/share/java/wrapper.jar"   
}
