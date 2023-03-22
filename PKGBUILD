# Maintainer: Atom Long <atom.long@hotmail.com>

pkgname=nssm
pkgver=2.24
pkgrel=1
pkgdesc="The Non-Sucking Service Manager"
arch=(i686 x86_64)
url="https://nssm.cc/"
license=('MIT')
options=('!strip')
source=("${pkgname}"::"git+https://git.nssm.cc/nssm/nssm.git")
sha256sums=('SKIP')

case "$CARCH" in
i686) WARCH=win32; OUTDIR=out/Release/win32;;
x86_64) WARCH=win64; OUTDIR=out/Release/win64;;
*) echo "Unsupported architecture: $CARCH"; exit 1;;
esac

build() {
  cd "${srcdir}/${pkgname}"
  cmd //c '..\..\msbuild\hMSBuild.bat -notamd64 -vsw-version local /p:Configuration=Release /p:Platform='"$WARCH"
}

package () {
  cd "${srcdir}/${pkgname}"

  install -d "${pkgdir}/${MSYSTEM_PREFIX}/bin"
  install -m755 ${OUTDIR}/${pkgname}.exe "${pkgdir}/${MSYSTEM_PREFIX}/bin"
}
