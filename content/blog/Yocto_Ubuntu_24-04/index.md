+++
title = "Yocto builds auf Ubuntu 24.04"
date = 2025-05-08
description = "AppArmor Config für Yocto builds anpassen ..."
[taxonomies]
tags = ["Yocto", "Linux", "Ubuntu"]

[extra]
quick_navigation_buttons = true
+++

Ich bin inzwischen zurück zu Ubuntu gewechselt und verwende Ubuntu 24.04.
Als ich kürzlich mal wieder ein Yocto basiertes Projekt bauen wollte schlug der Build aufgrund der AppArmor Konfiguration fehl.
Die Lösung hat [ein Ubuntu Discourse Eintrag](https://discourse.ubuntu.com/t/ubuntu-24-04-lts-noble-numbat-release-notes/39890) geliefert,
die AppArmor Konfiguration musste angepasst werden um Bitbake das erstellen vun User Namespaces zu erlauben.

- Config-File anlegen: `sudo vi /etc/apparmor.d/bitbake`:

```bash
abi <abi/4.0>,

include <tunables/global>

/home/**/bitbake/bin/bitbake flags=(unconfined) {  
        userns,  
}
```

- Und anschließend die Konfiguration laden: `sudo apparmor_parser -r /etc/apparmor.d/bitbake`
