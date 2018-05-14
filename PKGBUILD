# Maintainer: Maikel Wever <maikelwever@gmail.com>

_pkgname=prusacontrol
pkgname=$_pkgname-git
pkgver=r592.7c9877c
pkgrel=1
pkgdesc="Alternative user interface for Slic3r Prusa Edition"
arch=('any')
url="https://github.com/prusa3d/PrusaControl"
license=('GPL3')
depends=('python' 'python-pyqt4' 'python-numpy' 'python-numpy-stl' 'python-pyrr' 'slic3r-prusa3d' 'python-pillow' 'python-opengl' 'python-certifi' 'python-zeroconf')
conflicts=('prusacontrol')
options=('!strip' '!emptydirs' '!optipng')
source=(
    "git+https://github.com/prusa3d/PrusaControl.git"
    "prusacontrol.desktop"
)

md5sums=('SKIP'
         '78a4517dda5907234322df4b97a6334e')

pkgver() {
    cd PrusaControl
    printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

package() {
    mkdir -p "${pkgdir}/usr/share/applications"
    cp prusacontrol.desktop "${pkgdir}/usr/share/applications"

    mkdir -p "${pkgdir}/opt/prusacontrol"
    cd "${srcdir}/PrusaControl"
    cp -r "data" "${pkgdir}/opt/prusacontrol"
    cp -r "doc" "${pkgdir}/opt/prusacontrol"
    cp -r "translation" "${pkgdir}/opt/prusacontrol"
    cp -r "ts" "${pkgdir}/opt/prusacontrol"
    cp -r "README.md" "${pkgdir}/opt/prusacontrol"
    cp -r "version.txt" "${pkgdir}/opt/prusacontrol"
    cp -r *.py "${pkgdir}/opt/prusacontrol"

    # Fix for missing slic3r (runtime error)
    mkdir -p "${pkgdir}/opt/prusacontrol/tools/Slic3r-Lite/bin"
    ln -s /bin/slic3r-prusa3d "${pkgdir}/opt/prusacontrol/tools/Slic3r-Lite/bin/slic3r"
}

# vim:set ts=2 sw=2 et:
