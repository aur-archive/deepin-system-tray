# Maintainer: Xu Fasheng <fasheng.xu[AT]gmail.com>

pkgname=deepin-system-tray
pkgver=git20131114092503
pkgrel=1
pkgdesc='Icon theme from Linux Deepin'
arch=('i686' 'x86_64')
url="http://www.linuxdeepin.com/"
license=('GPL2')
depends=('deepin-system-settings')

_fileurl=http://packages.linuxdeepin.com/deepin/pool/main/d/deepin-system-tray/deepin-system-tray_0.1-1+git20131114092503~1dfbbf0f1a.tar.gz
source=("${_fileurl}")
md5sums=('ca8bf2de6c517d335e64fda512e3885c')

_filename="$(basename "${_fileurl}")"
_filename="${_filename%-*}"
_innerdir="${_filename/_/-}"

_install_copyright_and_changelog() {
    mkdir -p "${pkgdir}/usr/share/doc/${pkgname}"
    cp -f debian/copyright "${pkgdir}/usr/share/doc/${pkgname}/"
    gzip -c debian/changelog > "${pkgdir}/usr/share/doc/${pkgname}/changelog.gz"
}

# Usage: _easycp dest files...
_easycp () {
    local dest=$1; shift
    mkdir -p "${dest}"
    cp -R -t "${dest}" "$@"
}

package() {
    cd "${srcdir}/${_innerdir}"

    _easycp "${pkgdir}"/usr/share/deepin-system-tray/ src

    mkdir -p "${pkgdir}"/etc/xdg/autostart/
    install -m 0644 debian/deepin-system-tray.desktop "${pkgdir}"/etc/xdg/autostart/

    _install_copyright_and_changelog

    # fix python version
    find "${pkgdir}" -iname "*.py" | xargs sed -i 's=\(^#! */usr/bin.*\)python=\1python2='
}
