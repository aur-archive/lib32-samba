# Maintainer: josephgbr <rafael.f.f1@gmail.com>

# How to update?
# 'pkgver' and 'pkgrel' has to be same as in 'smbclient'
# Run 'pacman -Si smbclient' to verify the version
# e.g.: smbclient 4.1.8-1 means pkgver=4.1.8 and pkgrel=1

pkgbase=lib32-samba
pkgname=(lib32-libwbclient lib32-smbclient)
pkgver=4.2.1
pkgrel=1
arch=('x86_64')
url="http://www.samba.org"
license=('GPL3')
_urlprefix=http://mirrors.kernel.org/archlinux/extra/os/i686
source=("$_urlprefix/smbclient-$pkgver-$pkgrel-i686.pkg.tar.xz"
        "$_urlprefix/libwbclient-$pkgver-$pkgrel-i686.pkg.tar.xz")
noextract=(smbclient-$pkgver-$pkgrel-i686.pkg.tar.xz
           libwbclient-$pkgver-$pkgrel-i686.pkg.tar.xz)
md5sums=('3931e7e6e6aaa19093ced35afb55c4f6'
         '9d656c88b4ac4c709c65536623b322a7')

package_lib32-libwbclient() {
  pkgdesc="Samba winbind client library (32 bits)"
  depends=('lib32-libbsd' 'lib32-glibc' "libwbclient>=$pkgver")
  
  rm -rf libwbclient && mkdir libwbclient
  cd libwbclient  
  tar xf ../libwbclient-$pkgver-$pkgrel-i686.pkg.tar.xz usr/lib
  
  mkdir -p "$pkgdir"/usr/lib32
  cp -rPf usr/lib/* "$pkgdir"/usr/lib32
  sed -i 's#/lib#/lib32#' "$pkgdir"/usr/lib32/pkgconfig/wbclient.pc
}


package_lib32-smbclient() {
  pkgdesc="Tools to access a server's filespace and printers via SMB (32 bits)"
  depends=('lib32-tdb' 'lib32-gnutls' 'lib32-talloc' 'lib32-libcap'
           'lib32-libwbclient' 'lib32-libgcrypt' 'lib32-libcups'
           'lib32-pam' 'lib32-avahi' 'lib32-systemd' 'lib32-acl'
           "smbclient>=$pkgver")
         
  rm -rf smbclient && mkdir smbclient
  cd smbclient  
  tar xf ../smbclient-$pkgver-$pkgrel-i686.pkg.tar.xz usr/lib
  
  mkdir -p "$pkgdir"/usr/lib32
  cp -rPf usr/lib/* "$pkgdir"/usr/lib32
  sed -i 's#/lib#/lib32#'\
    "$pkgdir"/usr/lib32/pkgconfig/netapi.pc \
    "$pkgdir"/usr/lib32/pkgconfig/smbclient.pc \
    "$pkgdir"/usr/lib32/pkgconfig/smbclient-raw.pc
                           
  rm -rf "$pkgdir"/usr/lib32/cups # not a lib
}

