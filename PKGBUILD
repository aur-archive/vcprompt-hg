# Contributor: bender02 at archlinux dot us

pkgname=vcprompt-hg
pkgver=89
pkgrel=2
pkgdesc="Print a string with info about VCS suitable for inclusion into prompts"
url="http://vc.gerg.ca/hg/vcprompt/file/tip/README.txt"
license='GPLv2'
arch=('i686' 'x86_64')
makedepends=('mercurial')

_hgroot='http://vc.gerg.ca/hg/'
_hgrepo='vcprompt'

build() {
  cd $srcdir
  msg "Connecting to Mercurial server...."

  if [ -d $_hgrepo ]; then
    cd $_hgrepo
    hg pull -u || true
    msg "The local files are updated."
  else
    hg clone $_hgroot $_hgrepo
  fi

  msg "Mercurial checkout done or server timeout"
  msg "Starting make..."

  rm -rf "$srcdir/$_hgrepo-build"
  cp -r "$srcdir/$_hgrepo" "$srcdir/$_hgrepo-build"
  cd "$srcdir/$_hgrepo-build"

  #
  # BUILD HERE
  #

  make
}

package(){
  cd "$srcdir/$_hgrepo-build"
  install -Dm755 $_hgrepo "${pkgdir}/usr/bin/$_hgrepo"
}

# vim:set ts=2 sw=2 et:
