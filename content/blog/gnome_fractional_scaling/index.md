+++
title = "Fractional Scaling mit Gnome"
date = 2024-05-11
updated = 2020-10-30
description = "Fractional Scaling in Gnome aktivieren ..."
[taxonomies]
tags = ["Gnome", "Linux","Debian", "VanillaOS"]

[extra]
quick_navigation_buttons = true
+++

Ich werde alt, und die Schrift auf meinem High DPI Screen mit 100% Darstellung zu lesen wird langsam schwierig. Zum Glück bin ich über einen [Blog-Post von Canox.net](https://canox.net/2021/08/kurztipp-fractional-scaling-unter-gnome-aktivieren/)  gestolpert, in dem erklärt wird wir man _Fractional Scaling_ aktivieren kann.

## Debian Bookworm

Auf Debian Bookworm muss mein ein Terminal öffnen und folgenden Befehl eingeben:

```bash
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

Nach dem nächsten Neustart hat man dann die Optionen 125%, 150% oder 175% Skalierung auszuwählen.

## Vanilla OS

Auf Vanilla OS hat obiges Kommando nicht funktioniert,
weil _gsettings_ erst nicht installiert ware,
und dann die Kategorie _org.gnome.mutter_ nicht existierte.

Die Lösung war direkt einen _dconf_ Editor zu verwenden.

- Editor installieren `sudo apt install dconf-editor gconf-cli`.
- Eintrag erstellen: `dconf write /org/gnome/mutter/experimental-features "['scale-monitor-framebuffer']"`.
- Ergebnis im UI-Editor betrachten: `dconf-editor`.
- Neustart, dann ist _Fractional Scaling_ aktiviert.

