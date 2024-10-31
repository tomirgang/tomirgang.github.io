+++
title = "QEMU User Emulation"
date = 2024-10-31
description = "QEMU User Emulation auf Vanilla OS verwenden ..."
[taxonomies]
tags = ["QEMU", "binfmt", "VanillaOS"]

[extra]
quick_navigation_buttons = true
+++

Quelle: https://wiki.debian.org/QemuUserEmulation

QEMU User Emulation erlaubt es Binaries fremder Architekturen transparent auszuführen.

##  QEMU User Emulation zum Immutable Root hinzufügen

```bash
abroot pkg add qemu-user-static
abroot pkg add binfmt-support
abroot pkg apply
```

Danach ist ein Neustart notwendig damit die Änderungen aktiv werden.

## Benutzung mit Ubuntu

- Architektur hinzufügen: `sudo dpkg --add-architecture arm64`
- Quellen aktualisieren:
```bash
Types: deb deb-src
URIs: http://archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Architectures: amd64

Types: deb deb-src
URIs: http://security.ubuntu.com/ubuntu/
Suites: noble-security
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Architectures: amd64

Types: deb deb-src
URIs: http://ports.ubuntu.com/ubuntu-ports/
Suites: noble noble-updates noble-backports
Components: main universe restricted multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Architectures: arm64
```
- arm64 Paket installieren: `sudo apt install busybox-static:arm64`
```bash
$ file $(which busybox)
/usr/bin/busybox: ELF 64-bit LSB executable, ARM aarch64, version 1 (GNU/Linux), statically linked, BuildID[sha1]=9a56c1160885424581261f8e1ef773bef3605199, for GNU/Linux 3.7.0, stripped
```
- Paket ausführen
```bash
$ busybox
BusyBox v1.36.1 (Ubuntu 1:1.36.1-6ubuntu3.1) multi-call binary.
BusyBox is copyrighted by many authors between 1998-2015.
Licensed under GPLv2. See source distribution for detailed
copyright notices.
...
```
