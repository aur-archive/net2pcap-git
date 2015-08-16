# Maintainer: s1gma <s1gma@mindslicer.com>

pkgname=net2pcap-git
pkgver=20111214
pkgrel=1
pkgdesc="A simple network-to-pcap capture file for Linux. Its goal is to be as simple as possible to be used in hostile environments"
arch=('i686' 'x86_64')
url="https://github.com/nbareil/net2pcap"
license=('GPL')
depends=()
makedepends=('git')
provides=('net2pcap')
source=()

_gitroot=https://github.com/nbareil/net2pcap
_gitname=net2pcap

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"
  make

}

package() {
  cd "$srcdir/$_gitname-build"
  install -D -m 755 net2pcap $pkgdir/usr/bin/net2pcap
}

# vim:set ts=2 sw=2 et:
