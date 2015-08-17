# Maintainer: ruario 
# Contributor: RobertMe
# Contributor: BlackEagle
# Contributor: Skunnyk
# Contributor: totoloco
pkgname=opera-next # Set to opera if you want to replace your main/stable build
_bigrelease=12.15
_buildver=1745
_randomizer=emptsh
pkgver=${_bigrelease}_${_buildver}
pkgrel=2
pkgdesc="A fast and secure web browser and Internet suite. Alpha version."
url="http://my.opera.com/desktopteam/blog/"
depends=('gcc-libs' 'libxt' 'freetype2' 'libxext')
provides=('opera')
replaces=('opera-devel')
optdepends=('gstreamer0.10-base-plugins: HTML5 Video support' 'gstreamer0.10-good: HTML5 Video support')
install=opera-next.install
options=(!strip !zipman)
license=('custom:opera')
arch=('i686' 'x86_64')
_arch=i386
[ "$CARCH" = "x86_64" ] && _arch=x86_64
#source=(http://snapshot.opera.com/unix/${_randomizer}_${_bigrelease}-${_buildver}/opera-next-${_bigrelease}-${_buildver}.${_arch}.linux.tar.xz)
source=(http://www.herecura.be/files/opera-next-${_bigrelease}-${_buildver}.${_arch}.linux.tar.xz)
md5sums=('63979b24c0bc31d0724aba744fa1bbfc')
[ "$CARCH" = "x86_64" ] && md5sums=('d32ee78afabcce76a80a124c687a4752')

# Uncomment the following line, if you want your User Agent to include Arch Linux.
_opdistro="Arch Linux"

package() {

	# 'Install' Opera into $pkgdir
	opera-next-${_bigrelease}-${_buildver}.${_arch}.linux/install --prefix /usr --name ${pkgname} --repackage "${pkgdir}/usr"
	install -D -m 644 "${pkgdir}/usr/share/${pkgname}/defaults/license.txt" "${pkgdir}/usr/share/licenses/${pkgname}/license.txt"

	# Insert an Arch User Agent string if set
	if [ -n "${_opdistro}" ]
	then
		mkdir -p "${pkgdir}/usr/share/${pkgname}/custom/defaults"
		echo "[ISP]" > "${pkgdir}/usr/share/${pkgname}/custom/defaults/operaprefs.ini"
		echo "Id=${_opdistro}" >> "${pkgdir}/usr/share/${pkgname}/custom/defaults/operaprefs.ini"
		chmod 644 "${pkgdir}/usr/share/${pkgname}/custom/defaults/operaprefs.ini"
	fi
}
