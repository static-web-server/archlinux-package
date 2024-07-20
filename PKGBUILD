# Maintainer: Jose Quintana <joseluisquintana20[at]gmail[dot]com>

pkgname=static-web-server-bin
_pkgname=static-web-server
pkgver=2.32.1
pkgrel=1
pkgdesc="Static Web Server (sws): A cross-platform, high-performance and asynchronous web server for static files-serving (official binary version)"
arch=('x86_64' 'i686' 'armv6h' 'armv7h' 'aarch64')
url="https://static-web-server.net"
license=('Apache' 'MIT')
provides=('static-web-server' 'sws')
conflicts=('sws')
depends=()
optdepends=()
source_x86_64=(static_web_server_x86_64_${pkgver}.tar.gz::https://github.com/${_pkgname}/${_pkgname}/releases/download/v${pkgver}/${_pkgname}-v${pkgver}-x86_64-unknown-linux-gnu.tar.gz)
source_i686=(static_web_server_i686_${pkgver}.tar.gz::https://github.com/${_pkgname}/${_pkgname}/releases/download/v${pkgver}/${_pkgname}-v${pkgver}-i686-unknown-linux-gnu.tar.gz)
source_armv6h=(static_web_server_armv6h_${pkgver}.tar.gz::https://github.com/${_pkgname}/${_pkgname}/releases/download/v${pkgver}/${_pkgname}-v${pkgver}-arm-unknown-linux-musleabihf.tar.gz)
source_armv7h=(static_web_server_armv7h_${pkgver}.tar.gz::https://github.com/${_pkgname}/${_pkgname}/releases/download/v${pkgver}/${_pkgname}-v${pkgver}-armv7-unknown-linux-musleabihf.tar.gz)
source_aarch64=(static_web_server_aarch64_${pkgver}.tar.gz::https://github.com/${_pkgname}/${_pkgname}/releases/download/v${pkgver}/${_pkgname}-v${pkgver}-aarch64-unknown-linux-gnu.tar.gz)

sha256sums_x86_64=('7f10a4601c82f2eda5227abf79edc2df5ba61a221c35a6e45878878c96875cee')
sha256sums_i686=('571ceaf2a20f786ba10ef81198b5bbbe4a9c8b4db2a02e54e6a6e39ab35f3170')
sha256sums_armv6h=('d42fdedd0bf638b0d2a8ac847e67aba06b6d7686ad2eea0517aeee6e028135e5')
sha256sums_armv7h=('0eabc77293d2beba1e26b847fa7935adcfa7c9a68ef481ea7ba629772a6034d6')
sha256sums_aarch64=('34571e9390fdcdf7b327870e7d3974b5a61a8d80f565c249487f08db1c81bdf0')

package() {
    case "$CARCH" in
        'x86_64') target='x86_64-unknown-linux-gnu';;
        'i686') target='i686-unknown-linux-gnu';;
        'armv6h') target='arm-unknown-linux-musleabihf';;
        'armv7h') target='armv7-unknown-linux-musleabihf';;
        'aarch64') target='aarch64-unknown-linux-gnu';;
    esac

    cd "${srcdir}/${_pkgname}-v${pkgver}-${target}/"

    # Install docs
    install -d "${pkgdir}/usr/share/licenses/${_pkgname}"

    cp -R LICENSE-APACHE \
        "${pkgdir}/usr/share/licenses/${_pkgname}/"
    cp -R LICENSE-MIT \
        "${pkgdir}/usr/share/licenses/${_pkgname}/"

    # Install binary
    install -D -m755 ${_pkgname} \
        "${pkgdir}/usr/bin/${_pkgname}"

    # Symlink binary
    ln -s "/usr/bin/${_pkgname}" "${pkgdir}/usr/bin/sws"
}
