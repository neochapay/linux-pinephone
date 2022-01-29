# AArch64 PinePhone/PineTab specific kernel
# Maintainer: Dan Johansen <strit@manjaro.org>
# Maintainer: Philip Müller <philm@manjaro.org>

pkgbase=linux-pinephone
_tag="orange-pi-5.16-20220128-1757"
_srcname=linux-${_tag}
_kernelname=${pkgbase#linux}
_desc="PinePhone Kernel (Megi)"
pkgver=5.16.4
pkgrel=1
arch=('aarch64')
url="https://github.com/megous/linux/releases/tag/$_tag"
license=('GPL2')
makedepends=('xmlto' 'docbook-xsl' 'kmod' 'inetutils' 'bc' 'git' 'uboot-tools' 'dtc' 'coreutils')
options=('!strip')
source=("linux-$_tag.tar.gz::https://github.com/megous/linux/archive/${_tag}.tar.gz"
        'config'
        'linux.preset'
        '60-linux.hook'
        '90-linux.hook'
        '5.16.3-4.patch'
        # Drop Megi's Modem-Power
        '0101-arm64-dts-pinephone-drop-modem-power-node.patch'
        '0102-arm64-dts-pinephone-pro-remove-modem-node.patch'
        # Implement Martijn's improvements for the cameras
        '0103-media-ov5640-Implement-autofocus.patch'
        # Reparent clocks to lower speed-occillator
        '0104-ccu-sun50i-a64-reparent-clocks-to-lower-speed-oscillator.patch'
        # Quirk for Kernel-Bug 210681         
        '0105-quirk-kernel-org-bug-210681-firmware_rome_error.patch'
        # LED patches
        '0106-leds-gpio-make-max_brightness-configurable.patch'
        '0107-panic-led.patch'
        # Bootsplash
        '0201-revert-garbage-collect-fbdev-scrolling-acceleration.patch'
        '0202-revert-fbcon-remove-now-unusued-softback_lines-cursor-argument.patch'
        '0203-revert-fbcon-remove-no-op-fbcon_set_origin.patch'
        '0204-revert-fbcon-remove-soft-scrollback-code.patch'
        '0301-bootsplash.patch'
        '0302-bootsplash.patch'
        '0303-bootsplash.patch'
        '0304-bootsplash.patch'
        '0305-bootsplash.patch'
        '0306-bootsplash.patch'
        '0307-bootsplash.patch'
        '0308-bootsplash.patch'
        '0309-bootsplash.patch'
        '0310-bootsplash.patch'
        '0311-bootsplash.patch'
        '0312-bootsplash.patch')
sha256sums=('2823712338432bc57b41bc0a13c17f1d7457b2f3c277306c570ca3a1d97435e5'
            'f2a6c9470cfe37e2ad3b784b44ec4e3d7411599f5820b7babe77bfdafcbe8f93'
            'f704a0e790a310f88b76bf5ae7200ef6f47fd6c68c0d2447de0f121cfc93c5ad'
            'ae2e95db94ef7176207c690224169594d49445e04249d2499e9d2fbc117a0b21'
            '71df1b18a3885b151a3b9d926a91936da2acc90d5e27f1ad326745779cd3759d'
            '6816eaa78c7a3a78b863c51d89147a0d66b3d5607faca1ed65d0b7d1d8e03133'
            '4438dbb4fc8dd2788da95615cc97394591a6f5dc54851860f912c62fcc934973'
            'ee0e1f7f9dc2f81aaa679664bf587760ce7225f494433af796b45e8500439576'
            'f88f9837ccbd76cae6d116f4dce40f9977e894241a668a7c0e3938021e9cc6f2'
            '91a43647c446c0792eec25efea265b14230b1bf1681be282b40862903ae98731'
            '5e804e1f241ce542f3f0e83d274ede6aa4b0539e510fb9376f8106e8732ce69b'
            'f34385a6e064583cfdf6fe660b2acf45828a009c047c933a8e7a6c5147ba9df7'
            '29ab48c207ccf90262596397026d3a20c7b7032833b17d6c77d7226db57e6914'
            '365d4225a7db60bd064ebbc34ce0ae582a0c378ad6c4cec7960a5ae4641a6757'
            'ddf1e7fc55cc6fe81ecfcac84112e573ca95713c027bc84d69cf880812fd6ff3'
            '94a8538251ad148f1025cc3de446ce64f73dc32b01815426fb159c722e8fa5bc'
            '1f18c5c10a3c63e41ecd05ad34cd9f6653ba96e9f1049ce2b7bb6da2578ae710'
            '59202940d4f12bad23c194a530edc900e066866c9945e39748484a6545af96de'
            'e096b127a5208f56d368d2cb938933454d7200d70c86b763aa22c38e0ddb8717'
            '8c1c880f2caa9c7ae43281a35410203887ea8eae750fe8d360d0c8bf80fcc6e0'
            '1144d51e5eb980fceeec16004f3645ed04a60fac9e0c7cf88a15c5c1e7a4b89e'
            'dd4b69def2efacf4a6c442202ad5cb93d492c03886d7c61de87696e5a83e2846'
            '028b07f0c954f70ca37237b62e04103e81f7c658bb8bd65d7d3c2ace301297dc'
            'a0c548c5703d25ae34b57931f1162de8b18937e676e5791a0f039922090881e7'
            '8dbb5ab3cb99e48d97d4e2f2e3df5d0de66f3721b4f7fd94a708089f53245c77'
            'a7aefeacf22c600fafd9e040a985a913643095db7272c296b77a0a651c6a140a'
            'e9f22cbb542591087d2d66dc6dc912b1434330ba3cd13d2df741d869a2c31e89'
            '27471eee564ca3149dd271b0817719b5565a9594dc4d884fe3dc51a5f03832bc'
            '60e295601e4fb33d9bf65f198c54c7eb07c0d1e91e2ad1e0dd6cd6e142cb266d')

prepare() {
  cd "${srcdir}/${_srcname}"

  local src
  for src in "${source[@]}"; do
      src="${src%%::*}"
      src="${src##*/}"
      [[ $src = *.patch ]] || continue
      msg2 "Applying patch: $src..."
      patch -Np1 < "../$src"
  done

  cat "${srcdir}/config" > ./.config

  # add pkgrel to extraversion
  sed -ri "s|^(EXTRAVERSION =)(.*)|\1 \2-${pkgrel}|" Makefile

  # don't run depmod on 'make install'. We'll do this ourselves in packaging
  sed -i '2iexit 0' scripts/depmod.sh
  
  cd "${srcdir}/${_srcname}"

  # get kernel version
  make prepare

  # load configuration
  # Configure the kernel. Replace the line below with one of your choice.
  #make menuconfig # CLI menu for configuration
  #make nconfig # new CLI menu for configuration
  #make xconfig # X-based configuration
  #make oldconfig # using old config from previous kernel version
  # ... or manually edit .config
  #make pine64_defconfig

  # Copy back our configuration (use with new kernel version)
  #cp ./.config /var/tmp/${pkgbase}.config

  ####################
  # stop here
  # this is useful to configure the kernel
  #msg "Stopping build"
  #return 1
  ####################

  #yes "" | make config  
}

build() {
  cd "${srcdir}/${_srcname}"

  # build!
  unset LDFLAGS
  make ${MAKEFLAGS} Image Image.gz modules
  make ${MAKEFLAGS} DTC_FLAGS="-@" dtbs
}

_package() {
  pkgdesc="The Linux Kernel and modules - ${_desc}"
  depends=('coreutils' 'kmod' 'mkinitcpio>=0.7'
           'rtl8723bt-firmware' 'anx7688-firmware' 'ov5640-firmware')
  optdepends=('crda: to set the correct wireless channels of your country'
              'rtl8723bt-firmware-megi: for Pinephone Bluetooth'
              'ov5640-firmware: for Pinephone Camera'
              'uboot-pinephone: Firmware for Pinephone')
  provides=('kernel26' "linux=${pkgver}")
  replaces=('linux-armv8-rc')
  conflicts=('linux')
  backup=("etc/mkinitcpio.d/${pkgbase}.preset")
  install=linux-pinephone.install

  cd "${srcdir}/${_srcname}"

  KARCH=arm64

  # get kernel version
  _kernver="$(make kernelrelease)"
  _basekernel=${_kernver%%-*}
  _basekernel=${_basekernel%.*}

  mkdir -p "${pkgdir}"/{boot,usr/lib/modules}
  make INSTALL_MOD_PATH="${pkgdir}/usr" modules_install
  make INSTALL_DTBS_PATH="${pkgdir}/boot/dtbs" dtbs_install
  cp arch/$KARCH/boot/Image{,.gz} "${pkgdir}/boot"

  # make room for external modules
  local _extramodules="extramodules-${_basekernel}${_kernelname}"
  ln -s "../${_extramodules}" "${pkgdir}/usr/lib/modules/${_kernver}/extramodules"

  # add real version for building modules and running depmod from hook
  echo "${_kernver}" |
    install -Dm644 /dev/stdin "${pkgdir}/usr/lib/modules/${_extramodules}/version"

  # remove build and source links
  rm "${pkgdir}"/usr/lib/modules/${_kernver}/{source,build}

  # now we call depmod...
  depmod -b "${pkgdir}/usr" -F System.map "${_kernver}"

  # sed expression for following substitutions
  local _subst="
    s|%PKGBASE%|${pkgbase}|g
    s|%KERNVER%|${_kernver}|g
    s|%EXTRAMODULES%|${_extramodules}|g
  "

  # install mkinitcpio preset file
  sed "${_subst}" ../linux.preset |
    install -Dm644 /dev/stdin "${pkgdir}/etc/mkinitcpio.d/${pkgbase}.preset"

  # install pacman hooks
  sed "${_subst}" ../60-linux.hook |
    install -Dm644 /dev/stdin "${pkgdir}/usr/share/libalpm/hooks/60-${pkgbase}.hook"
  sed "${_subst}" ../90-linux.hook |
    install -Dm644 /dev/stdin "${pkgdir}/usr/share/libalpm/hooks/90-${pkgbase}.hook"
}

_package-headers() {
  pkgdesc="Header files and scripts for building modules for linux kernel - ${_desc}"
  provides=("linux-headers=${pkgver}")
  conflicts=('linux-headers')

  cd "${srcdir}/${_srcname}"
  local _builddir="${pkgdir}/usr/lib/modules/${_kernver}/build"

  echo "Installing build files..."
  install -Dt "${_builddir}" -m644 Makefile .config Module.symvers System.map \
    vmlinux
  install -Dt "${_builddir}/kernel" -m644 kernel/Makefile

  mkdir "${_builddir}/.tmp_versions"

  echo "Installing headers..."
  cp -t "${_builddir}" -a include scripts

  install -Dt "${_builddir}/arch/${KARCH}" -m644 arch/${KARCH}/Makefile
  install -Dt "${_builddir}/arch/${KARCH}/kernel" -m644 arch/${KARCH}/kernel/asm-offsets.s

  cp -t "${_builddir}/arch/${KARCH}" -a arch/${KARCH}/include
  mkdir -p "${_builddir}/arch/arm"
  cp -t "${_builddir}/arch/arm" -a arch/arm/include

  install -Dt "${_builddir}/drivers/md" -m644 drivers/md/*.h
  install -Dt "${_builddir}/net/mac80211" -m644 net/mac80211/*.h

  # http://bugs.archlinux.org/task/13146
  install -Dt "${_builddir}/drivers/media/i2c" -m644 drivers/media/i2c/msp3400-driver.h

  # http://bugs.archlinux.org/task/20402
  install -Dt "${_builddir}/drivers/media/usb/dvb-usb" -m644 drivers/media/usb/dvb-usb/*.h
  install -Dt "${_builddir}/drivers/media/dvb-frontends" -m644 drivers/media/dvb-frontends/*.h
  install -Dt "${_builddir}/drivers/media/tuners" -m644 drivers/media/tuners/*.h

  # add xfs and shmem for aufs building
  mkdir -p "${_builddir}"/{fs/xfs,mm}

  echo "Installing KConfig files..."
  find . -name Kconfig\* -exec install -Dm644 {} "${_builddir}/{}" \;

  echo "Removing unneeded architectures..."
  local _arch
  for _arch in "${_builddir}"/arch/*/; do
    [[ ${_arch} == */${KARCH}/ || ${_arch} == */arm/ ]] && continue
    rm -r "${_arch}"
  done

  echo "Removing documentation..."
  rm -r "${_builddir}/Documentation"

  echo "Removing broken symlinks..."
  find -L "${_builddir}" -type l -printf 'Removing %P\n' -delete

  echo "Removing loose objects..."
  find "${_builddir}" -type f -name '*.o' -printf 'Removing %P\n' -delete
  
  echo "Remove unwanted files..."
  find ${_builddir} -name '*.orig' -printf 'Removing %P\n' -delete

  echo "Stripping build tools..."
  local _binary _strip
  while read -rd '' _binary; do
    case "$(file -bi "${_binary}")" in
      *application/x-sharedlib*)      _strip="${STRIP_SHARED}"   ;; # Libraries (.so)
      *application/x-archive*)        _strip="${STRIP_STATIC}"   ;; # Libraries (.a)
      *application/x-executable*)     _strip="${STRIP_BINARIES}" ;; # Binaries
      *application/x-pie-executable*) _strip="${STRIP_SHARED}"   ;; # Relocatable binaries
      *) continue ;;
    esac
    strip ${_strip} "${_binary}"
  done < <(find "${_builddir}/scripts" -type f -perm -u+w -print0 2>/dev/null)

  echo "Stripping vmlinux..."
  ${CROSS_COMPILE}strip -v ${STRIP_STATIC} "${_builddir}/vmlinux"
}

pkgname=("${pkgbase}" "${pkgbase}-headers")
for _p in ${pkgname[@]}; do
  eval "package_${_p}() {
    _package${_p#${pkgbase}}
  }"
done
