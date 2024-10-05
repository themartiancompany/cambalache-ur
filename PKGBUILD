# Maintainer: Echo J. <aidas957 at gmail dot com>
# Contributor: Dušan Simić <dusan.simic1810@gmail.com>
# shellcheck shell=bash disable=SC2034,SC2164

pkgname=cambalache
pkgver=0.92.0
pkgrel=1
pkgdesc="A new RAD tool for Gtk 4 and 3"
arch=('x86_64')
url="https://gitlab.gnome.org/jpu/cambalache"
license=('LGPL-2.1-only')
depends=('cairo' 'dconf' 'gdk-pixbuf2' 'glib2' 'gtk3' 'gtk4' 'gtksourceview5'
         'hicolor-icon-theme' 'libadwaita' 'libhandy' 'libxkbcommon' 'pango'
         'pixman' 'python' 'python-gobject' 'python-lxml' 'wayland' 'webkit2gtk-4.1'
         'webkitgtk-6.0' 'wlroots>=0.18.0')
makedepends=('gobject-introspection' 'meson' 'ninja')
source=("${url}/-/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha512sums=('53b04211e61dcfb7070c1ed7ee39696c4f2f4b742fb68a172d48fed6a6a9dd7ecf1c887efba780c752e03e3b3d36c6c24a2fffdd36e0381412d5774eac8ef7e8')

prepare() {
  # Use project's Casilda dependency
  # (This is likely the best solution until other programs start to use it)
  meson subprojects download casilda --source="${pkgname}-${pkgver}"
}

build() {
  arch-meson "${pkgname}-${pkgver}" build --reconfigure

  meson compile -C build
}

package() {
  meson install -C build --destdir "${pkgdir}"
}
