# Maintainer: And Bryson <agbryson@gmail.com>
pkgname=srmio-git
pkgver=20130317
pkgrel=1
pkgdesc="Library to access the most important functions of a Schoberer Radmesstechnik (SRM) PowerControl V, VI and 7"
url="http://www.zuto.de/project/srmio/"
arch=('x86_64' 'i686')
license=('MIT')
depends=()
install=""
source=() 

_gitroot="git://github.com/rclasen/srmio.git"
_gitname="master"
 
build() {
    cd "$srcdir"
 
    msg "Connecting to GIT server...."
    if [[ -d $_gitname ]]; then
        cd "$_gitname"
        git checkout "$_gitname"
        git pull origin "$_gitname"
        msg "The local files are updated."
    else
        git clone --depth 1 "$_gitroot" "$_gitname"
        cd "$_gitname"
        git checkout "$_gitname"
    fi
    msg "GIT checkout done or server timeout"
    sh genautomake.sh
    ./configure
    make
}
 
package() {
    cd $srcdir/$_gitname
    make DESTDIR=$pkgdir install
}

