# Contributor: Fabio Ribeiro <fabiorphp@gmail.com>
# Maintainer: Fabio Ribeiro <fabiorphp@gmail.com>
pkgname=php81-pecl-zmq
_extname=zmq
pkgver=1.1.4
pkgrel=0
pkgdesc="PHP 8 extension for ZeroMQ - PECL"
url="https://pecl.php.net/package/zmq"
arch="all"
license="PHP-3.01"
depends="php81-common"
makedepends="php81-dev zeromq-dev"
_commit=ee5fbc693f07b2d6f0d9fd748f131be82310f386
source="php-pecl-$_extname-$_commit.tar.gz::https://github.com/zeromq/php-zmq/archive/$_commit.tar.gz"
builddir="$srcdir/php-$_extname-$_commit"
#source="php-pecl-$_extname-$pkgver.tgz::https://pecl.php.net/get/$_extname-$pkgver.tgz"
#builddir="$srcdir/$_extname-$pkgver"

build() {
	phpize81
	./configure --prefix=/usr --with-php-config=php-config81
	make
}

check() {
	php81 -dextension=modules/$_extname.so --ri $_extname
	make NO_INTERACTION=1 REPORT_EXIT_STATUS=1 test TESTS=--show-diff
}

package() {
	make INSTALL_ROOT="$pkgdir" install

	local _confdir="$pkgdir"/etc/php81/conf.d
	mkdir -p $_confdir
	echo "extension=$_extname" > $_confdir/50_$_extname.ini
}

sha512sums="ece4f52b6717749d56280e2e988a5d291fe967c40489f1e7b7ac0a17688a5a92b2a9fa720978dbad0969830034371ea54e937dd7cce7a6d983162977afd290c7  php-pecl-zmq-ee5fbc693f07b2d6f0d9fd748f131be82310f386.tar.gz"
