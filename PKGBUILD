# Maintainer: Jan Houben <jan@nexttrex.de>
# Contributor: Jesus Alvarez <jeezusjr at gmail dot com>
#
# This PKGBUILD was generated by the archzfs build scripts located at
#
# http://github.com/archzfs/archzfs
#
pkgname="zfs-dkms"
pkgdesc="Kernel modules for the Zettabyte File System."

pkgver=2.0.2
pkgrel=1
makedepends=()
arch=("x86_64")
url="https://zfsonlinux.org/"
source=("https://github.com/zfsonlinux/zfs/releases/download/zfs-${pkgver}/zfs-${pkgver}.tar.gz")
sha256sums=("bde5067ce4577d26cc0f0313a09173ad40d590d01539b92c93f33f06ee150b24")
license=("CDDL")
depends=("zfs-utils=${pkgver}" "lsb-release" "dkms")
provides=("zfs" "zfs-headers" "spl" "spl-headers")
groups=("archzfs-dkms")
conflicts=("zfs" "zfs-headers" "spl" "spl-headers")
replaces=("spl-dkms")

build() {
    cd "${srcdir}/zfs-${pkgver}"
    ./autogen.sh || true
}

package() {
    dkmsdir="${pkgdir}/usr/src/zfs-${pkgver}"
    install -d "${dkmsdir}"
    cp -a ${srcdir}/zfs-${pkgver}/. ${dkmsdir}
    cd "${dkmsdir}"
    find . -name ".git*" -print0 | xargs -0 rm -fr --
    scripts/dkms.mkconf -v ${pkgver} -f dkms.conf -n zfs
    chmod g-w,o-w -R .
}
