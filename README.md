jubilant-octo-train
-------------------

**NOTE**: Project is in pre-alpha phase.

Provides network bootable Debian Live OS that can seamlessly deploy
[Dasharo](https://docs.dasharo.com) open source firmware.

## Features

### Dasharo HCL Report

[Dasharo Hardware Compatibility List Report](config/includes.chroot/usr/bin/dasharo-hcl-report) dumps most important information about platform and backup SPI NOR flash.
Gathered information can be used for future analysis, debugging and recovery.
Optionally scripts upload dump to [Dasharo HCL Backup Server](https://backup.dasharo.com),
so Dasharo Team improve open source firmware product line and support customers
in case of issues.

Dasharo HCL Reports are also used during open source firmware port feasibilty
analysis, so if you are interested in Dasharo support for you hardware feel
free to [reach us](mailto:leads@3mdeb.com).

Please note Dasharo HCL Report may contain sensitive information like serial
numbers. Please do not make this information public. Dasharo Team treats
privacy as much as possible.

### Dasharo Blobs Transmission

Unfortunately, some hardware platforms cannot be fully functional without
binary blobs in the firmware. Some binary blobs have no EULA or any other
licesnse discussing redistributability. To avoid issues Dasharo Blobs
Transmission scripts extract blobs from SPI NOR flash backup and patch Dasharo
open source firmware before deployment.

### coreboot utils

Most distributions do not package [coreboot utils](https://review.coreboot.org/plugins/gitiles/coreboot/+/refs/heads/master/util/).
Those utils are crucial to obtain information about platform hardware and
firmware. jubilant-octo-train project includes following tools:
* superiotool
* inteltool
* ectool
* msrtool
* nvramtool
* intelp2m
* cbfstool

### UEFIExtract

jubilant-octo-train also contain UEFIExtract provided by [LongSoft/UEFITool](https://github.com/LongSoft/UEFITool).

# Demo

## Supported hardware

### Dell OptiPlex 7010/9010 SFF

## How it works

Project use set ofa`live-build` scripts to build custom Debian Live that can be
network booted using [iPXE](https://ipxe.org/). Build process produce
`vmlinuz`, `initrd` and `filesystem.squashfs`.

## Requirements

* Debian 11
* Packages
  ```shell
  sudo apt install live-build
  ```

## Usage

```shell
git clone https://github.com/Dasharo/jubilant-octo-train.git
cd jubilant-octo-train
lb config
sudo lb build
```

Build results will be available:
* `binary/live/filesystem.squashfs`
* `tftpboot/live/vmlinuz`
* `tftpboot/live/initrd.img`

### Booting over iPXE

## Roadmap

- [] Dasharo HCL Backup Server
- [] Dasharo HCL Backup Server Onion
- [] [Dasharo Openess Meter](https://github.com/Dasharo/dasharo-issues/issues/43)
