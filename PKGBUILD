# Maintainer: Echo J. <aidas957 at gmail dot com>
# Contributor: Dušan Simić <dusan.simic1810@gmail.com>
# shellcheck shell=bash disable=SC2034,SC2164

pkgname=cambalache
pkgver=0.94.0
pkgrel=1
pkgdesc="A new RAD tool for Gtk 4 and 3"
arch=('x86_64')
url="https://gitlab.gnome.org/jpu/cambalache"
license=('LGPL-2.1-only')
depends=('at-spi2-core' 'cairo' 'dconf' 'gdk-pixbuf2' 'glib2' 'gtk3' 'gtk4'
         'gtksourceview5' 'hicolor-icon-theme' 'libadwaita' 'libhandy'
         'libxkbcommon' 'pango' 'pixman' 'python' 'python-gobject' 'python-lxml'
         'wayland' 'webkit2gtk-4.1' 'webkitgtk-6.0' 'wlroots>=0.18.0')
makedepends=('git' 'gobject-introspection' 'meson' 'ninja' 'wayland-protocols')
source=("${url}/-/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha512sums=('019edd2cb38a6fd578007f90544ff8a76f35bff9cea7b8d5c585278306267088d3d6d221e6c4ea11a979b045a5c6d7c3ca4fdbb50604bb7d35b92f75cc52de28')

prepare() {
  # Use project's Casilda dependency
  # (This is likely the best solution until other programs start to use it)
  meson subprojects download casilda --sourcedir="${pkgname}-${pkgver}"
  meson subprojects update casilda --sourcedir="${pkgname}-${pkgver}"
}

build() {
  arch-meson "${pkgname}-${pkgver}" build --reconfigure

  meson compile -C build
}

package() {
  meson install -C build --destdir "${pkgdir}"
}
