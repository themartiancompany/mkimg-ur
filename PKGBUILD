# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_offline="false"
_git="false"
pkgname=mkimg
pkgver=0.0.0.0.0.0.0.0.0.0.0.0.0.1
_commit="0a66419696f3191ea9b1523c46d2d2072aa59060"
pkgrel=1
_pkgdesc=(
  "Generate image files in various formats."
)
pkgdesc="${_pkgdesc[*]}"
arch=(
  any
)
_http="https://github.com"
_ns="themartiancompany"
url="${_http}/${_ns}/${pkgname}"
license=(
  AGPL3
)
depends=(
  "e2fsprogs"
  "libcrash-bash"
)
_os="$( \
  uname \
    -o)"
[[ "${_os}" != "GNU/Linux" ]] && \
[[ "${_os}" == "Android" ]] && \
  depends+=(
  )
optdepends=(
  'blk-utils: swap volume support'
  "erofs-utils: 'enhanced read only file system' support"
  'luks-tools: LUKS volumes support'
  'mdadm: RAID images support'
  'mtools: FAT file system support'
  'squashfs-tools-ng: Squash file system support'
)
[[ "${_os}" == "GNU/Linux" ]] && \
[[ "${_os}" != "Android" ]] && \
  optdepends+=(
    "btrfs-progs: 'better file system' support"
  )
makedepends=(
  make
)
checkdepends=(
  "shellcheck"
)
source=()
sha256sums=()
_url="${url}"
_tag="${_commit}"
_tag_name="commit"
_tarname="${pkgname}-${_tag}"
[[ "${_offline}" == "true" ]] && \
  url="file://${HOME}/${pkgname}"
[[ "${_git}" == true ]] && \
  makedepends+=(
    "git"
  ) && \
  source+=(
    "${_tarname}::git+${_url}#${_tag_name}=${_tag}?signed"
  ) && \
  sha256sums+=(
    SKIP
  )
[[ "${_git}" == false ]] && \
  if [[ "${_tag_name}" == 'pkgver' ]]; then
    _tar="${_tarname}.tar.gz::${_url}/archive/refs/tags/${_tag}.tar.gz"
    _sum="3b035f4755a007867c0bc0d3a0bfd9628a2b6c0feb93fa30a791ae804f636a46"
  elif [[ "${_tag_name}" == "commit" ]]; then
    _tar="${_tarname}.zip::${_url}/archive/${_commit}.zip"
    _sum="3b035f4755a007867c0bc0d3a0bfd9628a2b6c0feb93fa30a791ae804f636a46"
  fi && \
    source+=(
      "${_tar}"
    ) && \
    sha256sums+=(
      "${_sum}"
    )
validpgpkeys=(
  # Truocolo <truocolo@aol.com>
  '97E989E6CF1D2C7F7A41FF9F95684DBE23D6A3E9'
)

check() {
  cd \
    "${_tarname}"
  make \
    -k \
    check
}

package() {
  cd \
    "${_tarname}"
  make \
    PREFIX="/usr" \
    DESTDIR="${pkgdir}" \
    install
}

# vim: ft=sh syn=sh et
