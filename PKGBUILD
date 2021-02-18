# Merged with official ABS kirigami2 PKGBUILD by João, 2021/02/05 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>

pkgname=kirigami2-git
pkgver=5.80.0_r2659.g5e079538
pkgrel=1
pkgdesc='A QtQuick based components set'
arch=($CARCH)
url='https://community.kde.org/Frameworks'
license=(LGPL)
groups=(kf5-git)
depends=(qt5-quickcontrols qt5-quickcontrols2 qt5-graphicaleffects)
makedepends=(git extra-cmake-modules-git qt5-tools qt5-doc qt5-svg kpackage-git doxygen)
conflicts=(${pkgname%-git} kirigami-git)
provides=(${pkgname%-git} kirigami-git)
source=("git+https://github.com/KDE/${pkgname%2-git}.git")
sha256sums=('SKIP')

pkgver() {
  cd ${pkgname%2-git}
  _ver="$(grep -m1 'set(KF5\?_VERSION' CMakeLists.txt | cut -d '"' -f2 | tr - .)"
  echo "${_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
  cmake -B build -S ${pkgname%2-git} \
    -DBUILD_TESTING=OFF \
    -DBUILD_QCH=ON
  cmake --build build
}

package() {
  DESTDIR="$pkgdir" cmake --install build
}

