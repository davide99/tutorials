# Configurazione secondo schermo

Creare file in `/usr/share/multiple-monitors.sh`:

```bash
#!/usr/bin/env bash

xrandr --setprovideroutputsource 1 0
xrandr --output VGA-1 --auto --output VGA-1-1 --auto --left-of VGA-1
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
