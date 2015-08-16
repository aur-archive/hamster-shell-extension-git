# Maintainer: Juan Manuel Hernandez <juanmah@gmail.com>

_real_pkgname=hamster-shell-extension
pkgname="${_real_pkgname}-git"
pkgver=20140308
pkgrel=1
pkgdesc="Shell extension for project hamster - the GNOME time tracker"
arch=('any')
url="https://github.com/projecthamster/shell-extension"
license=('GPL')
depends=('hamster-applet' 'glib2' 'dbus-glib' 'libxslt' 'gettext' 'docbook2x' 'intltool' 'gnome-doc-utils')
optdepends=('gnome-tweak-tool: A tool to customize advanced GNOME 3 options.')
makedepends=('git')
conflicts=("$_real_pkgname")
provides=("$_real_pkgname")
groups=('gnome-extra')
install="hamster-shell-extension.install"
source=()
md5sums=()

_gitroot="git://github.com/projecthamster/shell-extension.git"
_gitname="shell-extension"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server ..."

  if [ -d "$srcdir/$_gitname" ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
} 

package() {
  _extpath="$pkgdir/usr/share/gnome-shell/extensions"
  _extname="hamster@projecthamster.wordpress.com"
  mkdir -p "$_extpath/$_extname"
  cd "$srcdir/$_gitname"
  cp -r * "$_extpath/$_extname"
}

