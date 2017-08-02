pkgname=hub
pkgver=2.3.0
_pkgver=pre10
pkgrel=1
pkgdesc="cli interface for Github"
url="https://hub.github.com"
arch=('x86_64')
license=('MIT')
conflicts=('hub')
provides=('hub')
depends=('git')
makedepends=('go' 'groff' 'ruby-bundler')
source=("https://github.com/github/hub/archive/v$pkgver-$_pkgver.tar.gz")
sha256sums=('SKIP')


build() {
  cd "$srcdir/$pkgname-$pkgver-$_pkgver"
  make all man-pages
}

package() {
  cd "$srcdir/$pkgname-$pkgver-$_pkgver"

  install -Dm755 bin/hub "$pkgdir/usr/bin/hub"
  install -Dm644 LICENSE "$pkgdir/usr/share/licenses/${pkgname/-git/}/LICENSE"
  install -Dm644 etc/hub.bash_completion.sh "$pkgdir/usr/share/bash-completion/completions/hub"
  install -Dm644 etc/hub.zsh_completion "$pkgdir/usr/share/zsh/site-functions/_hub"
  for manpage in share/man/man1/hub.1 share/man/man1/hub-*.1; do
    install -Dm644 $manpage "$pkgdir/usr/share/man/man1/$(basename $manpage)"
  done
}
