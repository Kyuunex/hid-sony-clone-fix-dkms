# pkgbuild based on https://aur.archlinux.org/packages/hid-sony-ds3usb-dkms/

_pkgbase='hid-sony-clone-fix'
pkgname=${_pkgbase}-dkms
pkgver=6.1.12
pkgrel=1
pkgdesc="A quick hack to the hid-sony driver meant for the third party / clone DS4 controllers that do not support HID feature report 0x81."
_srctag=v${pkgver}
license=('GPL2')
arch=('x86_64')
depends=('dkms')
source=("hid-sony.c::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/plain/drivers/hid/hid-sony.c?h=${_srctag}"
        "hid-ids.h::https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux.git/plain/drivers/hid/hid-ids.h?h=${_srctag}"
        "Makefile"
        "hid-sony-clone-fix-dkms.dkms"
        "hid-sony-blacklist.modprobe")
sha256sums=('297b84f9fb1093511590bbaf57f89119cdbf998ca3650099b045b5fb0204b88d'
            '67d4d45bf65875569e8904cd750a5a2cd1a05fb1e9493558b09c2d4904a03117'
            '71e745ee26e7d57b4e8aec03616faea548443d13ace854d53d3ba981956f241a'
            '04a25acef8059630188ebbf398115c87bf27f97a8e37ce9a10d1d30387800610'
            'f4ab0b6941e353e861007a0bb6c468b4a7d027c56d530056fa686ad837616635')

prepare(){
    local workdir="${srcdir}/workdir"
    mkdir -p "${workdir}"
    cp "${srcdir}/hid-sony.c" "${workdir}"
    patch -d "${workdir}" -Np3 -i "${srcdir}/../hid-sony-clone-fix.patch"
}

package() {
    local dest="${pkgdir}/usr/src/${_pkgbase}-${pkgver}"
    install -d "${dest}"
    install -m 644 -T "${srcdir}/workdir/hid-sony.c" "${dest}/${_pkgbase}.c"
    install -m 644 -T "${srcdir}/hid-ids.h" "${dest}/hid-ids.h"
    install -m 644 -T "${srcdir}/Makefile" "${dest}/Makefile"
    install -m 644 -T "${srcdir}/hid-sony-clone-fix-dkms.dkms" "${dest}/dkms.conf"

    sed -e "s/@_PKGBASE@/${_pkgbase}/" \
        -e "s/@PKGVER@/${pkgver}/" \
        -i "${pkgdir}/usr/src/${_pkgbase}-${pkgver}/dkms.conf"

    # Blacklist the original hid_sony module
    install -dm755 "${pkgdir}/usr/lib/modprobe.d"
    install -Dm644 "${srcdir}/hid-sony-blacklist.modprobe" "${pkgdir}/usr/lib/modprobe.d/hid-sony-blacklist.conf"
}
