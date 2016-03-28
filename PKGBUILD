# Maintainer: Hyacinthe Cartiaux <hyacinthe.cartiaux@free.fr>
# Contributor: Lev Lybin <lev.lybin@gmail.com>
# Contributor: Aaditya Bagga <aaditya_gnulinux@zoho.com>
# Contributor: Lukas Jirkovsky <l.jirkovsky@gmail.com>
# Contributor: Eric Bélanger <eric@archlinux.org>

pkgname=laptop-mode-tools
pkgver=1.69.2
pkgrel=1
pkgdesc='Power Savings tool for Linux'
arch=('any')
url='https://github.com/rickysarraf/laptop-mode-tools'
source=(${pkgname}-${pkgver}-${pkgrel}.tar.gz::https://github.com/rickysarraf/laptop-mode-tools/archive/${pkgver}.tar.gz)
sha256sums=('af4422f632d3dd3073c8aaf02333ca5f508952392299b39e9b6b0ac79fe0c292')
license=('GPL2')
depends=('bash')
optdepends=('acpid: ACPI support'
    'bluez-utils: Bluetooth support'
    'hdparm: hard disk power management'
    'sdparm: SCSI disk power management'
    'ethtool: Ethernet support'
    'wireless_tools: Wi-Fi support'
    'xorg-xset: DPMS standby support'
    'python2-pyside: LMT GUI')
backup=('etc/laptop-mode/conf.d/ac97-powersave.conf'
    'etc/laptop-mode/conf.d/auto-hibernate.conf'
    'etc/laptop-mode/conf.d/battery-level-polling.conf'
    'etc/laptop-mode/conf.d/bluetooth.conf'
    'etc/laptop-mode/conf.d/configuration-file-control.conf'
    'etc/laptop-mode/conf.d/cpufreq.conf'
    'etc/laptop-mode/conf.d/dpms-standby.conf'
    'etc/laptop-mode/conf.d/eee-superhe.conf'
    'etc/laptop-mode/conf.d/ethernet.conf'
    'etc/laptop-mode/conf.d/exec-commands.conf'
    'etc/laptop-mode/conf.d/hal-polling.conf'
    'etc/laptop-mode/conf.d/intel-hda-powersave.conf'
    'etc/laptop-mode/conf.d/intel-sata-powermgmt.conf'
    'etc/laptop-mode/conf.d/lcd-brightness.conf'
    'etc/laptop-mode/conf.d/nmi-watchdog.conf'
    'etc/laptop-mode/conf.d/pcie-aspm.conf'
    'etc/laptop-mode/conf.d/runtime-pm.conf'
    'etc/laptop-mode/conf.d/sched-mc-power-savings.conf'
    'etc/laptop-mode/conf.d/sched-smt-power-savings.conf'
    'etc/laptop-mode/conf.d/start-stop-programs.conf'
    'etc/laptop-mode/conf.d/terminal-blanking.conf'
    'etc/laptop-mode/conf.d/video-out.conf'
    'etc/laptop-mode/conf.d/wireless-ipw-power.conf'
    'etc/laptop-mode/conf.d/wireless-iwl-power.conf'
    'etc/laptop-mode/conf.d/wireless-power.conf'
    'etc/laptop-mode/laptop-mode.conf'
    'etc/laptop-mode/lm-profiler.conf')

package() {
    cd "laptop-mode-tools-${pkgver}"

    make DESTDIR="${pkgdir}" MAN_D=/usr/share/man LIB_D=/usr/lib PREFIX=/usr INIT_D=false install
    # use /bin instead of /sbin
    mv "${pkgdir}/usr/sbin" "${pkgdir}/usr/bin"
    find "${pkgdir}" -type f -exec sed -i 's|sbin/laptop_mode|bin/laptop_mode|g' '{}' ';'

    install -Dm755 gui/LMT.py "${pkgdir}/usr/bin/lmt-gui"
}
