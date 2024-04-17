# Maintainer: 7Ji <pugokughin@gmail.com>

_model_canonical='ARM Mali-G610'
_model='mali-valhall-g610'
_firmware="${_model}-firmware"
_repo='https://github.com/JeffyCN/mirrors'
_firmware_commit='e08ced3e0235b25a7ba2a3aeefd0e2fcbd434b68'
_eula_commit='8605a3c81b60ac5bd8e492cc02e84a2e0aa8e524'
_pkgver=g21p0-01eac0

pkgname="${_firmware}"
# The actual DDK version uses -, but it is forbidden in pkgver
pkgver="${_pkgver/-/.}"
pkgrel=1
pkgdesc="Firmware for ${_model_canonical} from rockchip"
url='https://developer.arm.com/Processors/Mali-G610'
license=('custom')
source=(
  "${_repo}/raw/${_eula_commit}/END_USER_LICENCE_AGREEMENT.txt"
  "mali_csffw_${_pkgver}.bin::${_repo}/raw/${_firmware_commit}/firmware/g610/mali_csffw.bin"
)
sha256sums=(
  'a78acc73de9909efb879800d4daa4640c4aaa55cd751238a133954aba15e4285'
  '8e7c821a55ca1c345cc79f61243616dd25fc35b81f090946f302886d67712df5'
)
arch=('any')
options=(!strip)

_package-firmware() {
  install -D --mode=644 mali_csffw_"${_pkgver}".bin "${pkgdir}"/usr/lib/firmware/mali_csffw.bin
  install -D --mode=644 END_USER_LICENCE_AGREEMENT.txt --target-directory="${pkgdir}/usr/share/licenses/${pkgbase}"
}

eval "package_${_firmware}() {
  pkgdesc='Firmware for ${_model_canonical}'
  _package-firmware
}"