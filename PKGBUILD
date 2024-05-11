# Maintainer: Echo J. <aidas957 at gmail dot com>
# Contributor: Dušan Simić <dusan.simic1810@gmail.com>
# shellcheck shell=bash disable=SC2034,SC2164

pkgname=cambalache
pkgver=0.90.2
pkgrel=1
pkgdesc="A new RAD tool for Gtk 4 and 3"
arch=('x86_64')
url="https://gitlab.gnome.org/jpu/cambalache"
license=('LGPL-2.1-only')
depends=('glib2' 'gtk3' 'gtk4' 'gtksourceview5' 'libadwaita' 'libhandy' 'python-gobject'
         'python-lxml' 'webkit2gtk-4.1' 'webkitgtk-6.0')
makedepends=('git' 'meson' 'ninja')
source=("${url}/-/archive/${pkgver}/${pkgname}-${pkgver}.tar.gz")
sha512sums=('f962260b4be8f77f1036afe90e9489a3f9fda3d4a3c7786005c113fa434a4bc598094cfc799deefca2a8b935c7308aea995626e8e32089b7e06b256fe6098291')

build() {
  arch-meson "${pkgname}-${pkgver}" build

  meson compile -C build
}

package() {
  meson install -C build --destdir "${pkgdir}"
}
