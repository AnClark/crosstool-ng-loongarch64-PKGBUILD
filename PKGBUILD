# Maintainer: Xiaotian Wu <yetist@gmail.com>

pkgname=crossbuild-ng-loongarch64
pkgver=1.25.0
pkgrel=1
pkgdesc='Cross compiler builder, patched for LoongArch64'
arch=('x86_64')
url='https://crosstool-ng.github.io/'
license=('GPL' 'LGPL')
groups=('loongarch')
depends=('automake' 'autoconf' 'bison' 'flex' 'help2man' 'unzip' 'wget')
options=('!emptydirs' '!strip')
source=('git+https://github.com/jiegec/crosstool-ng.git#branch=loongarch'
        'git+https://github.com/jiegec/ct-ng-loongarch64')
sha256sums=('SKIP'
            'SKIP')
_prefix_dir=/opt/crosstools-ng-loongarch64/
install=crosstools-ng-loongarch64.install

build() {
  cd crosstool-ng
  ./bootstrap
  ./configure --prefix=$_prefix_dir
  make
}

package() {
  make -C crosstool-ng DESTDIR="$pkgdir" install

  # Create link in /usr/bin
  mkdir -p "$pkgdir"/usr/bin/
  ln -s $_prefix_dir/bin/ct-ng "$pkgdir"/usr/bin/ct-ng-loongarch64

  # Copy Jiege's config file to /opt/
  cp -r ct-ng-loongarch64 "$pkgdir"/$_prefix_dir
}

# vim: ts=2 sw=2 et:
