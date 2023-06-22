# mk-mach2-lvm

A simple script for generating the commands creating volumes on Seagate [Exos 2X14](https://www.seagate.com/files/www-content/datasheets/pdfs/exos-2x14-DS2015-2-1912US-en_US.pdf)
and [Exos 2X18](https://www.seagate.com/content/dam/seagate/migrated-assets/www-content/datasheets/pdfs/exos-2x18-DS2093-1-2202US-en_US.pdf) (Mach2) dual actuator drives

## Requirements

- Python 3
- [plumbum (pip)](https://plumbum.readthedocs.io/en/latest/)
- [gum](https://github.com/charmbracelet/gum)
- [lsblk](https://linux.die.net/man/8/lsblk)
- [jq](https://github.com/jqlang/jq)

## Usage

`./mk-mach2-lvm`

1. Choose your drive (picks the first listed LUN from `lsblk` for the given pair of drives)
2. Copy the resulting commands :)

This script currently follows a naming convention of `sgt_{lv,vg}_[LAST 6 digits of serial number]` for logical volume and volume group naming, and uses a fixed stripe size of 128k

It will also output a json dump from lsblk of all the matching Mach2 disks before choosing your disks for some extended information if needed.
