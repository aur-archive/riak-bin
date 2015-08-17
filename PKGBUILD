# Maintainer: Thomas Jost <schnouki@schnouki.net>
# Contributor: lafka <lafa@hackeriet.no>
# Contributor: Albert Chang <albert.chang@gmx.com>
# Contributor: Thomas Mudrunka <harvie@@email..cz> You can also contact me on http://blog.harvie.cz/
# Contributor: zhehao
# Contributor: Tristan Rice <rice@outerearth.net>
# Contributor: Thiago Avelino <thiago@avelino.xxx>

pkgname=riak-bin
_pkgver_maj=2.0
pkgver=2.0.2
pkgrel=1
pkgdesc='NoSQL database engine providing decentralized key-value store, flexible map/reduce engine and HTTP/JSON query interface. Binary version from Debian.'
arch=('x86_64')
license=('APACHE')
url='http://riak.basho.com/'
depends=('erlang')
conflicts=('riak')
provides=('riak')
backup=('etc/riak/app.config' 'etc/riak/cert.pem' 'etc/riak/key.pem' 'etc/riak/vm.args')
options=('!emptydirs')
install='riak.install'
source=("http://s3.amazonaws.com/downloads.basho.com/riak/${_pkgver_maj}/${pkgver}/debian/7/riak_${pkgver}-1_amd64.deb"
        'riak.service')
md5sums=('e819ce01ae69079e27397e9821c5e2ed'
         'e6e26aa4cf5cae7b42c4ec0dd11e1db3')
sha256sums=('31ca5d472e992e3af267b440945239b110354a64fc197d2a3d73b93fc66483d4'
            '6f2240c6fb9b53c25d6c55f1aed3ebbd1c6e24acbb40bd4e6fa931073a1d2320')

prepare() {
  cd ${srcdir}

  msg2 'Extracting Debian package...'
  ar x riak_${pkgver}-1_amd64.deb
}

package() {
  cd ${pkgdir}
  bsdtar -xf ${srcdir}/data.tar.gz
  rm -rf etc/init.d var/run

  install -Dm644 ${srcdir}/riak.service ${pkgdir}/usr/lib/systemd/system/riak.service

  # Install Debian-named symlink to libncurses
  cd usr/lib
  ln -s libncurses.so.5 libtinfo.so.5
}
