# Maintainer: Your Name <email>
pkgname=atomic-pomodoro-timer
pkgver=1.0.0
pkgrel=1
pkgdesc="A privacy-first focus timer with a productivity heatmap and sticky notes"
arch=('x86_64')
url="https://github.com/acetypeo/Atomic-Pomodoro-Timer"
license=('MIT')
depends=('webkit2gtk' 'gtk3')
makedepends=('gcc' 'pkg-config' 'xxd')
source=("$pkgname::git+https://github.com/acetypeo/Atomic-Pomodoro-Timer.git")
sha256sums=('SKIP')

build() {
  cd "$srcdir/$pkgname"
  # Embed index.html into a C header
  xxd -i index.html > html_embedded.h
  # Compile the app
  gcc webview.c -o atomic-pomodoro-timer `pkg-config --cflags --libs gtk+-3.0 webkit2gtk-4.0`
}

package() {
  cd "$srcdir/$pkgname"
  install -Dm755 atomic-pomodoro-timer "$pkgdir/usr/bin/atomic-pomodoro-timer"
}