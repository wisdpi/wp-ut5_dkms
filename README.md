# Realtek r8152 DKMS

![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/awesometic/realtek-r8152-dkms?sort=semver&style=for-the-badge)

This driver forked from [awesometic/realtek-r8152-dkms](https://github.com/awesometic/realtek-r8152-dkms)

This provides WP-UT5 driver in DKMS way so that you can keep the latest driver even after the kernel upgrade.

## Compatibility

This driver supports [WisdPi USB 3.2 to 5GbE adapter (WP-UT5)](https://www.wisdpi.com/products/wisdpi-usb-3-2-5g-ethernet-adapter-wp-ut5-wired-lan-network-connection-for-mac-os-linux-windows-backward-compatible-on-5g-2-5g-1g-100mbps-ideal-for-gaming) and some other USB Ethernet chipsets.

> Refers to the official websites, you can check it at the bottom of this document

Chipset          | Interface   | Performance
:----------------|:-----------:|:----------------:
RTL8157          | USB 3.0     | 5 GbE
RTL8156 /B       | USB 3.0     | 2.5 GbE
RTL8153 /B/C/D/E | USB 3.0     | 10/100/1000 MbE
RTL8154 /B       | USB 2.0     | 10/100/1000 MbE
RTL8152B         | USB 2.0     | 10/100M

## Installation

Installation using the Debian package is recommended for the sake of getting the newer driver.

### Debian package

#### Released package file

Download the latest Debian package from the Release tab on the Github repository.

Then enter the following command.

```bash
sudo dpkg -i realtek-r8152-dkms-2.19.2-1*.deb
```

> If multiple files selected by the wild card, you should type the specific version of the file.
>
> ```bash
> sudo dpkg -i realtek-r8152-dkms*.deb
> ```

If dependency error occurs, try to fix that with `apt` command.

```bash
sudo apt install --fix-broken
```

### autorun.sh

Using the `autorun.sh` script that Realtek provides on their original driver package. This is **not installed as a DKMS**, only efforts to the current kernel.

Download or clone this repository and move to the extracted directory, then run the script.

```bash
sudo ./autorun.sh
```

### dkms-install.sh

This script is from aircrack-ng team. You can install the DKMS module by a simple command.

Download or clone this repository and move to the extracted directory, then run the script.

```bash
sudo ./dkms-install.sh
```

## Debian package build

You can build yourself this after installing some dependencies including `dkms`.

```bash
sudo apt install devscripts debmake debhelper build-essential dkms dh-dkms
```

```bash
dpkg-buildpackage -b -rfakeroot -us -uc
```

## LICENSE

GPL-2 on Realtek driver and the debian packaing.

## References

- [Realtek r8152 driver downloads](https://www.realtek.com/Download/List?cate_id=585)
