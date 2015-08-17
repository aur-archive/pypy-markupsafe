# $Id: PKGBUILD 211647 2014-04-22 10:43:11Z fyan $
# Maintainer : Felix Yan <felixonmars@gmail.com>
# Contributor: Ionut Biru <ibiru@archlinux.org>
# Contributor: Alex Anthony <alex.anthony28991@gmail.com>

pkgbase='pypy-markupsafe'
pkgname=('pypy3-markupsafe' 'pypy-markupsafe')
pkgver=0.23
pkgrel=3
pkgdesc="Implements a XML/HTML/XHTML Markup safe string for Python"
arch=('any')
url="http://pypi.python.org/pypi/MarkupSafe"
license=('custom')
makedepends=('pypy-setuptools' 'pypy3-setuptools')
source=("http://pypi.python.org/packages/source/M/MarkupSafe/MarkupSafe-${pkgver}.tar.gz")
sha512sums=('4f1fd91ced5e7119584b56cf7b69cfe6fdd9613bd77412368a38e9ef5d1011ba5c76d1d3a0da3d60f9f474627e6c8c8b613a80a668b32d212f09072f8b1f5b28')

build() {
  cp -r MarkupSafe-${pkgver} python2-MarkupSafe-${pkgver}
  cd "${srcdir}/MarkupSafe-${pkgver}"
  pypy3 setup.py build

  cd "${srcdir}/python2-MarkupSafe-${pkgver}"
  pypy setup.py build
}

package_pypy3-markupsafe() {
  depends=("pypy3>=2.3" "pypy3<=2.4")

  cd MarkupSafe-${pkgver}
  # pypy3 setup.py install --root="${pkgdir}" --optimize=1 \
  #   --install-lib=/opt/pypy3/lib/python3.2/site-packages
  pypy3 setup.py install --root="${pkgdir}" --optimize=1

  install -D -m644 LICENSE \
    "${pkgdir}/usr/share/licenses/pypy3-markupsafe/LICENSE"
}

package_pypy-markupsafe() {
  depends=('pypy')

  cd python2-MarkupSafe-${pkgver}
  pypy setup.py install --root="${pkgdir}" --optimize=1

  install -D -m644 LICENSE \
    "${pkgdir}/usr/share/licenses/pypy-markupsafe/LICENSE"
}
