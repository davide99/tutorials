# Configurazione secondo schermo

## Script per xrandr

Creare file in `/usr/share/multiple-monitors.sh`:

```bash
#!/usr/bin/env bash

xrandr --setprovideroutputsource 1 0
xrandr --output VGA1 --auto --output VGA-1-1 --auto --left-of VGA1

#nomi ottenuti con xrandr --listproviders
xrandr --setprovideroffloadsink "CAICOS @ pci:0000:01:00.0" Intel
```

Rendere il file eseguibile:

```bash
sudo chmod +x /usr/share/multiple-monitors.sh
```

Far eseguire il file all'avvio (su XFCE):
1. Applicazioni > Impostazioni > Gestore delle impostazioni
1. Sessione e avvio (razzo)
1. Avvio automatico
1. Click su +
1. Come comando inserire il percorso dello script
1. Come attivazione scegliere "on logon"

## Far funzionare la scheda radeon con X11

Spostarsi in `xorg.conf.d` e creare il file `20-radeon.conf` con:

```
Section "Device"
	Identifier "Radeon"
	Driver "radeon"
	Option "AccelMethod" "exa"
	Option "DRI" "2"
EndSection
```

Creare anche il file `20-intel.conf` (altrimenti X11 fa partire solo la scheda radeon) con:
```
Section "Device"
	Identifier "Intel Graphics"
	Driver "Intel"
EndSection
```
