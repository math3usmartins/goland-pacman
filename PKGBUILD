# Maintainer: Matheus Martins <matheus@gmail.com>

pkgbase=goland
pkgname=(goland goland-jre)
pkgver=2021.3.3
pkgrel=1
pkgdesc='Clever Go IDE by JetBrains'
arch=('x86_64' 'i686')
license=('custom:jetbrains')
url='https://www.jetbrains.com/go/'
depends=('glib2' 'python')
options=('!strip')
source=("https://download.jetbrains.com/go/goland-${pkgver%b*}.tar.gz"
        jetbrains-goland.desktop
        LICENSE)
b2sums=('8e92a7b426928168adf27f36858f4542d8fcc2e7f1632d6e70157293f07bc90e52c2dad0c903e5da39dd2c88a624a6f96075f9226c49ff747fb29f3dc6ac75cd'
        'a9e43cb1b2323a8f4661c160a5aa14637e8a740533d222fa8db4cc6a0ea663d952ba3ba8c624a0aaf3a6c0d6a43f0bcc26fa5de488036f2d161dde8f9ef61125'
        'dadaf0e67b598aa7a7a4bf8644943a7ee8ebf4412abb17cd307f5989e36caf9d0db529a0e717a9df5d9537b10c4b13e814b955ada6f0d445913c812b63804e77')

package_goland() {
  optdepends=('goland-jre: JetBrains custom Java Runtime (Recommended)'
              'java-runtime: JRE - Required if goland-jre is not installed'
              'gnome-keyring: save login/deployment credentials safely'
              'java-openjfx: rendering Markdown files')

  install -dm755 "${pkgdir}"/opt/
  install -dm755 "${pkgdir}"/usr/bin/
  install -dm755 "${pkgdir}"/usr/share/applications/
  install -dm755 "${pkgdir}"/usr/share/pixmaps/

  cp -a "${srcdir}"/GoLand-${pkgver#*b}/ "${pkgdir}"/opt/${pkgbase}
  rm -rf "${pkgdir}"/opt/${pkgbase}/jbr

  ln -s /opt/${pkgbase}/bin/${pkgbase}.sh "${pkgdir}"/usr/bin/${pkgbase}
  install -D -m 644 "${srcdir}"/jetbrains-${pkgbase}.desktop "${pkgdir}"/usr/share/applications/
  install -D -m 644 "${pkgdir}"/opt/${pkgbase}/bin/${pkgbase}.svg "${pkgdir}"/usr/share/pixmaps/${pkgbase}.svg
  install -Dm644 LICENSE "${pkgdir}"/usr/share/licenses/${pkgname}/LICENSE.txt
}

package_goland-jre() {
  pkgdesc='JBR (JetBrains Runtime) for GoLand - a patched JRE'
  url='https://confluence.jetbrains.com/display/JBR/JetBrains+Runtime'

  install -d -m 755 "${pkgdir}"/opt/${pkgbase}
  cp -a "${srcdir}"/GoLand-${pkgver#*b}/jbr "${pkgdir}"/opt/${pkgbase}
}
