+++
title = "Docker on Vanilla OS"
date = 2024-10-30
updated = 2024-10-31
description = "Docker auf Vanilla OS installieren ..."
[taxonomies]
tags = ["Linux", "Docker", "VanillaOS"]

[extra]
quick_navigation_buttons = true
+++

Docker aus dem _docker.io_  auf _Vanilla OS 2.0 Orchid_ als zusätzliche
Container Runtime installieren.

## Docker zum Immutable Root hinzufügen

```bash
abroot pgk add docker.io  
abroot pkg apply
```

Die _docker_ Gruppe muss manuell angelegt werden, sonst startet der Docker Dienst nicht.

```bash
host-shell pkexec groupadd docker  
```

Danach ist ein Neustart notwendig damit die Änderungen aktiv werden.

## Docker Client installieren

Docker Client in einem Debian-basierten Subsystem installieren:

```bash
sudo apt install docker.io
```

Und den eigenen Benutzer zur _docker_ Gruppe hinzufügen:  

```bash 
sudo usermod -aG docker $USER
```

## Warum funktioniert das?  

Der lokale Unix Socket _/var/run/docker.sock_ ist im Container verfügbar,
wodurch der Client mit dem Docker Daemon im Root Dateisystem kommuniziert.

Vorsicht: Da Docker mit _root_ Rechten läuft kann der Benutzer im Subsystem
einen priviligierten Container starten und damit Änderungen am System vornehmen!
