# Maintainer: Your Name <email>
pkgname=atomic-pomodoro-timer
pkgver=1.0.0
pkgrel=1
pkgdesc="A focus timer with a productivity heatmap and sticky notes"
arch=('x86_64')
url="https://github.com/acetypeo/Atomic-Pomodoro-Timer"
license=('GPL3')
depends=('webkit2gtk' 'gtk3')
makedepends=('gcc' 'pkg-config' 'xxd')
source=("$pkgname::git+https://github.com/acetypeo/Atomic-Pomodoro-Timer.git")
sha256sums=('SKIP')

build() {
  cd "$srcdir/$pkgname"
  xxd -i index.html > html_embedded.h
  gcc webview.c -o atomic-pomodoro-timer $(pkg-config --cflags --libs gtk+-3.0 webkit2gtk-4.0)
}

package() {
  cd "$srcdir/$pkgname"
  
  # Binary
  install -Dm755 atomic-pomodoro-timer "$pkgdir/usr/bin/atomic-pomodoro-timer"
  
  # Desktop file
  install -Dm644 atomic-pomodoro-timer.desktop "$pkgdir/usr/share/applications/atomic-pomodoro-timer.desktop"
  
  # Icon (rename to match desktop file's Icon=atomic-pomodoro-timer)
  install -Dm644 icon.png "$pkgdir/usr/share/pixmaps/atomic-pomodoro-timer.png"
}