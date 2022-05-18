# Maintainer: Philip Goto <philip.goto@gmail.com>
# Maintainer Erik Inkinen <erik.inkinen@gmail.com>
# Contributor: Sam Whited <sam@samwhited.com>

pkgname=feedbackd-hybris
_pkgname=feedbackd-bookworm
pkgver=0.0.0+git20220208
pkgrel=1
pkgdesc='A daemon to provide haptic feedback on events'
arch=(x86_64 aarch64)
url='https://github.com/droidian/feedbackd'
license=(GPL3)
provides=(feedbackd)
conflict=(feedbackd)
depends=(
        dconf
        gsound
        json-glib
        libgudev
)
makedepends=(
        gobject-introspection
        meson
        vala
)
source=("${url}/archive/refs/heads/bookworm.tar.gz")
b2sums=('28e26aa447876119e95a643b43577570e86d8f4e629e46a49a1a3e5cb1bb68d773d9dcc2ff50c36733f66b535cedb61068181d52c1410daf3061b92ea7788ab9')

build() {
        cd ${srcdir}/${_pkgname}
        arch-meson . build -Dgtk_doc=true -Dman=true
        meson compile -C build
}

check() {
        cd ${srcdir}/${_pkgname}
        meson test -C build --print-errorlogs
}

package() {
        cd ${srcdir}/${_pkgname}
        DESTDIR="${pkgdir}" meson install -C build
}
