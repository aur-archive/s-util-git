
#Maintainer: Yichao Yu <yyc1992@gmail.com>
#Contributor: Yichao Yu <yyc1992@gmail.com>

pkgname=s-util-git
pkgver=20120318
pkgrel=2
pkgdesc="Simple utilities, git version"
arch=('any')
provides=('s-util')
conflicts=('s-util')
url="https://github.com/yuyichao/s-util"
license=('GPL')
depends=('bash' 'coreutils' 'findutils' 'grep' 'awk' 'sed')
optdepends=('xdg-utils: for using xopen to open any kind of files without annoy cli output'
  'openssl: for grub certificate from website'
  'nss: for add certificate in to database'
  'wget: for using recget to download recursively'
  'texlive-bin: for using texit to generate a tmp pdf'
  'curl: for netman and mitclass'
  'util-linux: mount')
makedepends=('git')

_gitroot='https://yuyichao@github.com/yuyichao/s-util.git'
_gitname='s-util'
build() {
  cd "$srcdir"

  msg "Connecting to github.com"

  if [ -d "$startdir/src/$_gitname" ] ;then
    cd "$startdir/src/$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot"
  fi
  msg "GIT checkout done or server timeout"

  cd "$srcdir/$_gitname"

  git checkout master

  mkdir build
  cd build

  cmake .. -DCMAKE_INSTALL_PREFIX=/usr
}

package() {
  cd "${srcdir}/$_gitname/build"
  make DESTDIR="${pkgdir}" install
}
