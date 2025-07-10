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
  # Find the extracted directory dynamically (should be exactly one folder matching OverBind*)
  srcdir_folder=$(find "$srcdir" -maxdepth 1 -type d -name "OverBind*")
  cd "$srcdir_folder"

  export NODE_ENV=production
  npm install
  npm run tauri build
}

package() {
  srcdir_folder=$(find "$srcdir" -maxdepth 1 -type d -name "OverBind*")
  cd "$srcdir_folder"

  install -Dm755 "src-tauri/target/release/overbind" "$pkgdir/usr/bin/overbind"
}
