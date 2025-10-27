pkgname=python-sphinx-theme-builder
pkgver=0.2.0b2
pkgrel=1
pkgdesc="Python build backend for Sphinx themes"
arch=('x86_64')
url="https://github.com/pradyunsg/sphinx-theme-builder"
license=('MIT')
depends=(
    'python'
    'python-nodeenv'
    'python-packaging'
    'python-pyproject-metadata'
    'python-rich'
    'python-setuptools'
)
makedepends=(
    'python-build'
    'python-flit-core'
    'python-installer'
)
source=(https://github.com/pradyunsg/sphinx-theme-builder/archive/${pkgver}/${pkgname#*-}-${pkgver}.tar.gz)
sha256sums=(e4cf8722ae40c133d79bd41a0398d2f96228cb79c891e77d6b9745da386360fa)

build() {
    cd ${pkgname#*-}-${pkgver}

    python3 -m build --wheel --skip-dependency-check --no-isolation
}

package() {
    cd ${pkgname#*-}-${pkgver}

    python3 -m installer -d ${pkgdir} dist/*.whl
}
