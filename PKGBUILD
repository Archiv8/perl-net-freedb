#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# ToDo: Add files: User documentation
# ToDo: Add files: Tooling
# FixMe: Namcap warnings and errors

# Maintainer: Ross Clark <archiv8@artisteducator.com>
# Contributor: Ross Clark <archiv8@artisteducator.com>

pkgname=perl-net-freedb
pkgver=0.10
pkgrel=1
pkgdesc="Net::FreeDB is an oo-based module to interface with FreeDB servers"
_dist=Net-FreeDB
arch=("any")
url="https://metacpan.org/release/Net-FreeDB"
license=("GPL" "PerlArtistic")
depends=(
  # Arch Linux official packages
  "perl"
  "perl-http-message"
  "perl-io-socket-inet6"
  "perl-libwww"
  "perl-mailtools"
  "perl-moo"
  "perl-test-most"

  # Archiv8 / AUR packages
  "perl-cddb-file"
)
options=("!emptydirs" purge)
source=(
  "https://cpan.metacpan.org/authors/id/D/DS/DSHULTZ/$_dist-$pkgver.tar.gz"
)
sha512sums=("b1b249dfb81128645e6e3481f93d914fc11ecf931b91f6a21a065fa2fde8674f9c8b5466b3112be4f4f28556c0ec899cf8723e60adaaf26b5165e61d61445368")

build() {
  cd "$srcdir/$_dist-$pkgver"
  unset PERL5LIB PERL_MM_OPT PERL_LOCAL_LIB_ROOT
  export PERL_MM_USE_DEFAULT=1 PERL_AUTOINSTALL=--skipdeps
  /usr/bin/perl Makefile.PL
  make
}

check() {
  cd "$srcdir/$_dist-$pkgver"
  unset PERL5LIB PERL_MM_OPT PERL_LOCAL_LIB_ROOT
  export PERL_MM_USE_DEFAULT=1
  make test
}

package() {
  cd "$srcdir/$_dist-$pkgver"
  unset PERL5LIB PERL_MM_OPT PERL_LOCAL_LIB_ROOT
  make install INSTALLDIRS=vendor DESTDIR="$pkgdir"
}
