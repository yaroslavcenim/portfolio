Netplan — это новая система настройки сети в Ubuntu (начиная с 18.04).

Конфиги лежат в: /etc/netplan
Обычно там один файл — 00-installer-config.yaml или 01-netcfg.yaml.
Формат — YAML (важны отступы, пробелы, не табы).

Применить конфиг: netplan apply
Проверить конфиг на ошибки: netplan try

Ethernet-интерфейс:
network:
  ethernets:
    ens33:
      addresses:
        - 192.168.1.100/24
      routes:
          - to: default
             via: 192.168.1.1
      nameservers:
        addresses: [8.8.8.8, 1.1.1.1]
  version: 2

DHCP:
network:
  ethernets:
    ens33:
        dhcp4: true
  version: 2

Включение маршрутизации (чтобы внутренние машины выходили в интернет)

В etc/sysctl.conf включить: net.ipv4.ip_forward=1

NAT через iptables (чтобы внутренние машины выходили в интернет)

sudo iptables -t nat -A POSTROUTING -o ens33 -j MASQUERADE (Где ens33 - интерфейс у которого есть выход в интернет)
Для сохранения правила: 
sudo apt install iptables-persistent
sudo netfilter-persistent save