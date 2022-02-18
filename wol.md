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

Riavvia per verficare che funzioni
