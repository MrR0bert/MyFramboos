# Setup of the Framboos
This page contains the documentation of the raspberry pi, including the commands used. Only the sensitive information is removed.

## Static IP
The raspberry has static private IP so it can be easily found on the network. This IP-address is configured with Linux's Network Manager.

First list all connections (because you need the name of the connection, not the interface):
```shell
nmcli connection show
```

After taking note of the value in the **NAME** column, use the following command to configure the IP-address:
```shell
sudo nmcli connection modify "[NAME from earlier]" \
ipv4.method "manual" \
ipv4.addresses "[STATIC-IP]/[NETMASK]" \
ipv4.gateway "[GATEWAY-IP]" \
ipv4.dns "[DNS-SERVER-1],[DNS-Server-2]"
```

Finally, restart the Network Manager:
```shell
sudo systemctl restart NetworkManager
```

Signout and reconnect using the new IP-address.