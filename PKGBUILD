# Maintainer: Your Name <youremail@example.com>
pkgname=overbind
pkgver=1.5.1
pkgrel=1
pkgdesc="A Rust + Tauri-based input remapping tool"
arch=('x86_64')
url="https://github.com/Twig6943/OverBind"
license=('MIT')
depends=('gtk3' 'libayatana-appindicator' 'webkit2gtk' 'glibc')
makedepends=('rust' 'npm' 'nodejs' 'yarn' 'git')

source=("git+https://github.com/Twig6943/OverBind.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/OverBind"
  # Get latest tag or short commit hash as version
  git describe --tags --always | sed 's/^v//; s/-/./g'
}

build() {
  cd "$srcdir/OverBind"

  export NODE_ENV=production

  npm install
  npm run tauri build
}

package() {
  cd "$srcdir/OverBind"

  install -Dm755 "src-tauri/target/release/overbind" "$pkgdir/usr/bin/overbind"
}
