# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>
# Maintainer: Philip Goto <philip.goto@gmail.com>
# Maintainer Erik Inkinen <erik.inkinen@gmail.com>
# Contributor: Sam Whited <sam@samwhited.com>

pkgname=feedbackd-hybris
_pkgname=feedbackd
pkgver='0.2.0+git20230508'
pkgrel=1
pkgdesc='A daemon to provide haptic feedback on events'
arch=(x86_64 aarch64)
url='https://github.com/droidian/feedbackd'
license=(GPL3)
provides=(feedbackd)
conflict=(feedbackd)
depends=('dconf' 'gsound' 'json-glib' 'libgudev')
makedepends=('gobject-introspection' 'meson' 'vala' 'gi-docgen' 'python-docutils')

source=("git+https://github.com/droidian/feedbackd.git")
sha256sums=('SKIP')

prepare() {
  cd ${srcdir}/${_pkgname}
  git checkout -b bookworm
  git checkout 76ab8710ce2d066254f5fdb9142dd43894fb0a58
}

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
