# Gnome

## Fractional Scaling

Ich werde alt, und die Schrift uaf meinem High DPI Screen mit 100% Darstellung zu lesen wird langsam schwierig. Zum Glück bin ich über einen [Blog-Post](https://canox.net/2021/08/kurztipp-fractional-scaling-unter-gnome-aktivieren/) von Canox.net gestolpert, in dem erklärt wird wir man _Fractional Scaling_ aktivieren kann.

Auf Debian Bookworm muss mein ein Terminal öffnen und folgenden Befehl eingeben:

```bash
gsettings set org.gnome.mutter experimental-features "['scale-monitor-framebuffer']"
```

Nach dem nächsten Neustart hat man dann die Optionen 125%, 150% oder 175% Skalierung auszuwählen.

