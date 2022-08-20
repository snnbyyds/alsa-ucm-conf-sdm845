# Maintainer: David Runge <dvzrv@archlinux.org>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>

pkgname=alsa-ucm-conf
pkgver=845.spec
pkgrel=4
pkgdesc="ALSA Use Case Manager configuration (and topologies)"
arch=(any)
url="https://alsa-project.org/"
license=(BSD)
source=("git+https://gitlab.com/sdm845-mainline/alsa-ucm-conf.git")
sha512sums=('SKIP')

prepare(){
  cd ${srcdir}/$pkgname
  wget https://gitlab.com/sdm845-mainline/alsa-ucm-conf/-/commit/9cb4b283515ffc11e33ce7aa04b357d48b741e1b.patch -O ../../9cb4b283515ffc11e33ce7aa04b357d48b741e1b.patch
  msg2 "Apply Patches"
  git apply ../.././9cb4b283515ffc11e33ce7aa04b357d48b741e1b.patch
#  git am  ../../0004-ucm2-add-profiles-for-OnePlus-6-6T-Pocophone-F1.patch

}
_pick() {
  local p="$1" f d; shift
  for f; do
    d="$srcdir/$p/${f#$pkgdir/}"
    mkdir -p "$(dirname "$d")"
    mv "$f" "$d"
    rmdir -p --ignore-fail-on-non-empty "$(dirname "$f")"
  done
}

package() {
  cd $pkgname
  install -vdm 755 "$pkgdir/usr/share/alsa/"
  cp -av ucm2 "$pkgdir/usr/share/alsa/"
  install -vDm 644 LICENSE -t "$pkgdir/usr/share/licenses/$pkgname"
  install -vDm 644 README.md -t "$pkgdir/usr/share/doc/$pkgname"
  install -vDm 644 ucm2/README.md -t "$pkgdir/usr/share/doc/$pkgname/ucm2"
}
