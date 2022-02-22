# Modificare fstab per montare un altro disco

Trova il nome della partizione con:
```
lsblk
```

Diciamo `/dev/sdb1`. Trova il *block id* con:
```
sudo blkid /dev/sdb1
```

Crea il punto di mount, per esempio:
```
sudo mkdir /media/hd2
```

Assegna i permessi `rwx` per owner e group:
```
sudo chmod 770 /media/hd2
```

Diciamo `436214af-1989-4b5e-b560-49754c137bc1`. Modifica `/etc/fstab` aggiungendo:
```
UUID=436214af-1989-4b5e-b560-49754c137bc1 /media/hd2 ext4 errors=remount-ro 0 1
```

Rimonta le partizioni:
```
sudo mount -a
```

Verifica che tutto vada bene con:
```
sudo dmesg | tail
```
