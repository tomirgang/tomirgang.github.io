+++
title = "Libvirt/Virt-Manager on Vanilla OS"
date = 2024-10-31
description = "Virt-Manager auf Vanilla OS benutzen ..."
[taxonomies]
tags = ["Linux", "libvirt", "VanillaOS", "virt-manager"]

[extra]
quick_navigation_buttons = true
+++

Libvirt und QEMU auf _Vanilla OS 2.0 Orchid_ installieren.

## Packete zum Immutable Root hinzufügen

```bash
abroot pkg add qemu-system
abroot pkg add libvirt-daemon-system
abroot pkg apply
```

Die _libvirt-qemu_ Gruppe und der _libvirt-qemu_ Benutzer muss manuell angelegt werden,
sonst startet der libvirtd Dienst nicht.

```bash
addgroup libvirt-qemu
useradd -r -s /bin/false -g kvm libvirt-qemu -G kvm
```

Danach ist ein Neustart notwendig damit die Änderungen aktiv werden.

Jetzt kann man Virt-Manager in einem Subsystem installieren
und damit virtuelle Maschinen anlegen.
