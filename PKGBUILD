# Maintainer: knul <dtor-dev[at]protonmail[dot]com>

pkgname=dtor-git
pkgver=0.1.0.0
pkgrel=1
pkgdesc="Dtor: a fairly launched privacy-centric coin with no premine and a finite supply"
license=('BSD')
arch=('x86_64')
url="https://dtor.org/"
depends=('boost-libs' 'libunwind' 'openssl' 'readline' 'zeromq' 'pcsclite' 'hidapi' 'protobuf')
makedepends=('git' 'cmake' 'boost')
source=(
    "${pkgname}"::"git+https://github.com/Dtor-Project/dtor#tag=v${pkgver}"
    "git+https://github.com/Dtor-Project/unbound.git"
    "git+https://github.com/Dtor-Project/miniupnp.git"
    "git+https://github.com/Dtor-Project/rapidjson.git"
    "git+https://github.com/Dtor-Project/RandomX.git"
    "dtor.sysusers"
    "dtor.tmpfiles")
sha512sums=('SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP'
            'SKIP')

prepare() {
  cd "${pkgname}"
  git submodule init
  git config submodule.external/unbound.url "$srcdir/unbound"
  git config submodule.external/miniupnp.url "$srcdir/miniupnp"
  git config submodule.external/rapidjson.url "$srcdir/rapidjson"
  git config submodule.external/RandomX.url "$srcdir/RandomX"
  git submodule update
}

build() {
  cd "${pkgname}"
  mkdir -p build && cd build
  cmake -D BUILD_TESTS=OFF -D CMAKE_BUILD_TYPE=release -D ARCH=default ../
  make
}

package() {
  backup=('etc/dtord.conf')

  cd "${pkgname}"
  install -Dm644 "LICENSE" -t "${pkgdir}/usr/share/licenses/${pkgname}"

  install -Dm644 "utils/conf/dtord.conf" "${pkgdir}/etc/dtord.conf"
  install -Dm644 "utils/systemd/dtord.service" "${pkgdir}/usr/lib/systemd/system/dtord.service"
  install -Dm644 "../dtor.sysusers" "${pkgdir}/usr/lib/sysusers.d/dtor.conf"
  install -Dm644 "../dtor.tmpfiles" "${pkgdir}/usr/lib/tmpfiles.d/dtor.conf"

  install -Dm755 "build/bin/dtor-wallet-cli" \
                 "build/bin/dtor-wallet-rpc" \
                 "build/bin/dtord" \
                 -t "${pkgdir}/usr/bin"
}

# vim: ts=2 sw=2 et:
