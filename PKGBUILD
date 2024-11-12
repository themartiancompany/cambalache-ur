# Maintainer: Echo J. <aidas957 at gmail dot com>
# Contributor: Dušan Simić <dusan.simic1810@gmail.com>
# shellcheck shell=bash disable=SC2034,SC2164

pkgname=cambalache
pkgver=0.92.2
pkgrel=1
pkgdesc="A new RAD tool for Gtk 4 and 3"
arch=('x86_64')
url="https://gitlab.gnome.org/jpu/cambalache"
license=('LGPL-2.1-only')
depends=('cairo' 'dconf' 'gdk-pixbuf2' 'glib2' 'gtk3' 'gtk4' 'gtksourceview5'
         'hicolor-icon-theme' 'libadwaita' 'libhandy' 'libxkbcommon' 'pango'
         'pixman' 'python' 'python-gobject' 'python-lxml' 'wayland' 'webkit2gtk-4.1'
         'webkitgtk-6.0' 'wlroots>=0.18.0')
makedepends=('git' 'gobject-introspection' 'meson' 'ninja' 'wayland-protocols')
source=("${url}/-/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha512sums=('791594d9b3355ee45cd269594e5dc9353f9e3c832e203d07c09a6bd144b87acb922b5952beb62448ed253917daeb79b05523cef51c98489d1dd6eb596485932c')

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
