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
source=(https://github.com/pradyunsg/sphinx-theme-builder/archive/${pkgver}/${pkgname#*-}-${pkgver}.tar.gz
    https://github.com/pradyunsg/sphinx-theme-builder/commit/bb78c8c8.patch
    https://github.com/pradyunsg/sphinx-theme-builder/commit/adeb3750.patch)
sha256sums=(e4cf8722ae40c133d79bd41a0398d2f96228cb79c891e77d6b9745da386360fa
    4102608a1b241a7b2b3fa8ff6a9cceaa405cb09a15ca0560cb14d948b107aa0a
    fa9bb52eef8bfaf256a72ff6f2ca248a75e582e38fa124d2fc40dbfadef9f649)

prepare() {
    cd ${pkgname#*-}-${pkgver}

    patch -p1 -i ${srcdir}/bb78c8c8.patch # Python 3.14 support
    patch -p1 -i ${srcdir}/adeb3750.patch
}

build() {
    cd ${pkgname#*-}-${pkgver}

    python3 -m build --wheel --skip-dependency-check --no-isolation
}

package() {
    cd ${pkgname#*-}-${pkgver}

    python3 -m installer -d ${pkgdir} dist/*.whl
}
