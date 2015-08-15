# Maintainer: Graham Edgecombe <graham@grahamedgecombe.com>
pkgname=gnome-shell-extension-dash-click-fix-git
pkgver=20121101
pkgrel=1
pkgdesc="A GNOME shell extension that launches a new instance of a program when the dash is clicked."
arch=('any')
url="https://github.com/grossetti/gnome-shell-extension_DashClickFix"
license=('unknown')
depends=('gnome-shell')
makedepends=('git')

_gitroot="https://github.com/grossetti/gnome-shell-extension_DashClickFix.git"
_gitname="gnome-shell-extension-dash-click-fix"

build() {
  cd ${srcdir}
  msg "Connecting to the GIT server..."
  if [[ -d ${srcdir}/${_gitname} ]] ; then
    cd ${_gitname}
    git pull origin
    msg "The local files are updated..."
  else
    git clone ${_gitroot} ${_gitname}
    cd ${_gitname}
  fi
  msg "GIT checkout done."

  # patch extension.js for gnome 3.6 support
  sed -i 's/\["3.2", "3.4"\]/["3.2", "3.4", "3.6"]/g' metadata.json
}

package() {
  cd "$srcdir/${_gitname}"
  install -Dm644 extension.js "${pkgdir}/usr/share/gnome-shell/extensions/DashClickFix@evotex.ch/extension.js"
  install -Dm644 metadata.json "${pkgdir}/usr/share/gnome-shell/extensions/DashClickFix@evotex.ch/metadata.json"
}

