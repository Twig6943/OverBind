# Maintainer: Your Name <youremail@example.com>
pkgname=overbind
pkgver=1.5.1
pkgrel=1
pkgdesc="A Rust + Tauri-based input remapping tool"
arch=('x86_64')
url="https://github.com/yourusername/overbind" # Replace with actual URL
license=('MIT') # or as appropriate
depends=('gtk3' 'libayatana-appindicator' 'webkit2gtk' 'glibc')
makedepends=('rust' 'npm' 'nodejs' 'yarn')
source=("$pkgname-$pkgver.tar.gz") # or use git source
sha256sums=('SKIP') # Replace if using a tarball with checksum

build() {
  cd "$srcdir/${pkgname^}-$pkgver"

  export NODE_ENV=production

  # install JS dependencies
  npm install

  # compile with Tauri
  npm run tauri build
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  # Find the built binary (adjust if different)
  install -Dm755 "src-tauri/target/release/overbind" "$pkgdir/usr/bin/overbind"

  # Optional: install desktop entry and icon
  #install -Dm644 "resources/linux/overbind.desktop" "$pkgdir/usr/share/applications/overbind.desktop"
  #install -Dm644 "resources/icon.png" "$pkgdir/usr/share/pixmaps/overbind.png"
}
