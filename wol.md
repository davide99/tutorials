# Abilitare il Wake on LAN

Installa ethtool:
```bash
sudo apt install ethtool
```

Trova il nome dell'interfaccia con:
```bash
ip a
```

Abilita il Wake on LAN:
```bash
sudo ethtool -s eno1 wol g
```

Spegni per verificare che funzioni.

Abilita il Wake on LAN permanentemente creando un file sotto `/etc/network/interfaces.d/eno1` con:
```
auto eno1
iface eno1 inet dhcp
	ethernet-wol g
```
