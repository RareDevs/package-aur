# Maintainer: Dummerle

pkgname=rare
pkgver=1.11.2
pkgrel=1
pkgdesc="Open source alternative for Epic Games Launcher, using Legendary"
arch=('any')
url="https://github.com/RareDevs/Rare"
license=('GPL3')
depends=(
  pyside6
  python-requests
  python-qtawesome
  python-orjson
  python-vdf
  legendary
)
makedepends=(
  git
  python-{build,installer,wheel}
  python-setuptools{,-scm}
)
optdepends=(
  "wine: run Windows games"
  "proton: run Windows games"
  "python-pypresence: Discord RPC integration"
  "python-pywebview: embedded browser for logging in"
)
source=("git+https://github.com/RareDevs/Rare.git#tag=$pkgver")
sha256sums=('64d8f9c0f0c9291ca10a5d40bcd96c39f03b1e650f216edbe212d977de078edc')

build() {
  cd Rare
  python setup.py bdist_wheel
}

package() {
  cd Rare
  python -m installer -d "$pkgdir" dist/*.whl
  install -Dm644 "misc/${pkgname%-git}.desktop" "$pkgdir/usr/share/applications/${pkgname%-git}.desktop"
  install -Dm644 "rare/resources/images/Rare.png" "$pkgdir/usr/share/pixmaps/${pkgname%-git}.png"
}

