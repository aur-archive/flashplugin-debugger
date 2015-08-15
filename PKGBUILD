# Maintainer: Hyperfang8 <hyperfang8@gmail.com>

pkgname=flashplugin-debugger
_licensefile='PlatformClients_PC_WWEULA-Combined-20100108_1657.pdf'
pkgver=11.2.202.394
pkgrel=1
pkgdesc='Adobe Flash Player'
url='http://www.adobe.com/support/flashplayer/downloads.html'
arch=('i686' 'x86_64')
case "$CARCH" in
  'i686')
    depends=('mozilla-common' 'libxt' 'gtk2' 'nss' 'curl' 'alsa-lib')
    optdepends=('libvdpau: GPU acceleration on Nvidia card')
      ;;
  'x86_64')
    depends=('mozilla-common' 'lib32-libxt' 'lib32-gtk2' 'lib32-nss' 'lib32-curl' 'lib32-alsa-lib' 'nspluginwrapper')
    optdepends=('lib32-libvdpau: GPU acceleration on Nvidia card')
    ;;
esac
provides=('flashplayer', 'flashplugin')
conflicts=('flashplugin')
license=('custom')
install=flashplugin.install
backup=(etc/adobe/mms.cfg)
source=('http://fpdownload.macromedia.com/pub/flashplayer/updaters/11/flashplayer_11_plugin_debug.i386.tar.gz'
        "http://www.adobe.com/products/eulas/pdfs/${_licensefile}"
        mms.cfg)
md5sums=('4d85e382cbac5c139bad4dbbeca10d64'
         '53146e096d2e4ec3dd26828b69704d2d'
         'ad99cdab9b6d2d9943394a438b569495')
options=(!strip)

package() {
  install -d -m755 "${pkgdir}"/usr/lib/mozilla/plugins/
  case "$CARCH" in
    'i686')
      install -m755 "${srcdir}"/libflashplayer.so "${pkgdir}"/usr/lib/mozilla/plugins/
      ;;
    'x86_64')
      install -d -m755 "${pkgdir}"/usr/lib32/mozilla/plugins/
      install -m755 "${srcdir}"/libflashplayer.so "${pkgdir}"/usr/lib32/mozilla/plugins/
      touch "${pkgdir}"/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
      chmod 755 "${pkgdir}"/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
      ;;
  esac

  install -d -m755 "${pkgdir}"/usr/share/licenses/${pkgname}/
  install -m644 "${_licensefile}" "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE.pdf
  install -d -m755 "${pkgdir}"/etc/adobe
  install -m644 "${srcdir}"/mms.cfg "${pkgdir}"/etc/adobe/mms.cfg
}

# vim:set ts=2 sw=2 et:
