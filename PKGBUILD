# Maintainer: Mark Grimes <mgrimes at peculier.com>
# https://github.com/mvgrimes/aur-perl-nagios-plugin

pkgname=perl-nagios-plugin
pkgver=0.36
pkgrel=2
pkgdesc="A family of perl modules to streamline writing Nagios plugins"
_dist=Nagios-Plugin
arch=('any')
url="https://metacpan.org/release/$_dist"
license=('GPL' 'PerlArtistic')
depends=('perl>=5.10.0' 'perl-params-validate' 'perl-class-accessor' 'perl-config-tiny' 'perl-math-calc-units')
options=('!emptydirs' purge)
source=(http://search.cpan.org/CPAN/authors/id/T/TO/TONVOON/$_dist-$pkgver.tar.gz)
md5sums=('b897f6d5d66a655dde7caec579efcf2e')

# Setup environment to ensure installation in system perl and vender directory
clean_env() {
  unset PERL5LIB PERL_MM_OPT PERL_MB_OPT PERL_LOCAL_LIB_ROOT
  export PERL_MM_USE_DEFAULT=1 MODULEBUILDRC=/dev/null PERL_AUTOINSTALL=--skipdeps
}

build() (
  cd "$srcdir/$_dist-$pkgver"
  clean_env
  /usr/bin/perl Makefile.PL
  make
)

check() (
  cd "$srcdir/$_dist-$pkgver"
  clean_env
  make test
)

package() (
  cd "$srcdir/$_dist-$pkgver"
  clean_env
  make install INSTALLDIRS=vendor DESTDIR="$pkgdir"
)
