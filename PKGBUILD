pkgname=overbind
pkgver=1.5.1
pkgrel=1
pkgdesc="A Rust + Tauri-based input remapping tool"
arch=('x86_64')
url="https://github.com/Twig6943/OverBind"
license=('MIT')
depends=('gtk3' 'libayatana-appindicator' 'webkit2gtk' 'glibc')
makedepends=('rust' 'nodejs' 'npm' 'git' 'base-devel')

source=("git+https://github.com/Twig6943/OverBind.git")
sha256sums=('SKIP')

pkgver() {
  cd "$srcdir/OverBind"
  git describe --tags --always | sed -E 's/^v//; s/-/./g'
}

build() {
  cd "$srcdir/OverBind"
  export NODE_ENV=production

  #yarn add -D @tauri-apps/cli && yarn install
  npm install
  cargo build --release --bin cursor-overlay-x86_64-unknown-linux-gnu
  npm run tauri build
}

package() {
  cd "$srcdir/OverBind"
  install -Dm755 "src-tauri/target/release/overbind" "$pkgdir/usr/bin/overbind"
}
