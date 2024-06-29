# Maintainer: Echo J. <aidas957 at gmail dot com>
# Contributor: Dušan Simić <dusan.simic1810@gmail.com>
# shellcheck shell=bash disable=SC2034,SC2164

pkgname=cambalache
pkgver=0.90.4
pkgrel=1
pkgdesc="A new RAD tool for Gtk 4 and 3"
arch=('x86_64')
url="https://gitlab.gnome.org/jpu/cambalache"
license=('LGPL-2.1-only')
depends=('dconf' 'gdk-pixbuf2' 'glib2' 'gtk3' 'gtk4' 'gtksourceview5' 'hicolor-icon-theme' 'libadwaita'
         'libhandy' 'pango' 'python-gobject' 'python-lxml' 'webkit2gtk-4.1' 'webkitgtk-6.0')
makedepends=('gobject-introspection' 'meson' 'ninja')
source=("${url}/-/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha512sums=('ac8b45b8ab45bb2ef9def2d9dbe75eb22bd2a2542af00c014934ef0ce9c54c98146b4a25b7066526de4fc772b40d97380e880b6d2f6cf16df76868e743e7d695')

build() {
  arch-meson "${pkgname}-${pkgver}" build

  meson compile -C build
}

package() {
  meson install -C build --destdir "${pkgdir}"
}
