pkgname=st-fuego
_pkgname=st
pkgver=0.8.2.r1092.9d152bb
pkgrel=1
epoch=1
pkgdesc="Fuego's simple (suckless) terminal"
arch=('i686' 'x86_64')
license=('MIT')
depends=('libxft')
makedepends=('git')
optdepends=('dmenu: feed urls to dmenu')
sha1sums=('SKIP')

provides=("${_pkgname}")
conflicts=("${_pkgname}")

pkgver() {
    cd ..
    printf "%s.r%s.%s" "$(awk '/^VERSION =/ {print $3}' config.mk)" \
        "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
    cd ..
    make X11INC=/usr/include/X11 X11LIB=/usr/lib/X11
}

package() {
    cd ..
    make PREFIX=/usr DESTDIR="${pkgdir}" install
    install -Dm644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
    install -Dm644 README.md "${pkgdir}/usr/share/doc/${pkgname}/README.md"
}
