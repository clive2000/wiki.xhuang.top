# Nmcli

## Enable NetowkrManger service

```bash
systemctl enable NetworkManager
systemctl start NetworkManager
```

## Connect to wifi

```bash
nmcli device wifi connect SSID password password
```

## Create a dhcp connection

```bash
nmcli con add con-name "static-ens32" ifname ens32 type ethernet ip4 xxx.xxx.120.44/24 gw4 xxx.xxx.120.1
nmcli con mod "static-ens32" ipv4.dns "1.1.1.1,1.0.0.1"
nmcli con up "static-ens32" ifce ens32
```

## Create a dhcp connection

```bash
nmcli connection add type ethernet con-name connection-name ifname interface-name
```

