# Network settings within OzFlux

## Network level
Each flux tower has an assigned IP range within the TERN OpenVPN network. IP addresses are provided and managed by TERN (contact Gerhard or Ian for access).
TERN OpenVPN provides a secure VPN connection for remote access to the flux tower network, each tower site uses a unique private network mask in the 192.168.x.x range.

## Site level
Each flux tower site has its own local network, typically using a private IP range within the 192.168.x.x subnet. This local network connects all devices at the site, including data loggers, modems, and routers.
All network-connected devices at the site should have a fixed IP address within this range. Check your modem settings on how to assign IP addresses to devices ie MAC-address mapping. See e.g. DHCP settings [Modem network setup](./TERNOpenVPN.html#configure-dhcp-server) or similar for your modem. 


Once a device connected to the modem, it takes time to change its IP address (`IP lease time`). Therefore, it is best to set up the desired device MAC-to-IP mapping before the first connection. Then the device uses the designated address from the start. Otherwise, it can take several hours or even days for the device to accept the new IP address (depending on the lease time configured in the DHCP server). Some modems /devices are stubborn to change the IP address of a DHCP client, but it usually resolves itself after some time.


You can discover the MAC address of a specific device in your [modem management interface](./TERNOpenVPN.html#configure-dhcp-server). Or you can check if the MAC address is printed on the device or provided in the configuration software of the device. For Campbell Scientific systems, the MAC address is usually available through `Loggernet Connect`, `PC 400`, `ECMon`, `Devconfig`, etc. For Licor instruments, use device specific software e.g. `LI-7500 3.0.2`, `Li-7x00 A RS DS` or `Li-COR Li-8x0`.


To make network management and troubleshooting easier across OzFlux, it is recommended that all sites use similar device-to-IP address mappings:

* Modem: 192.168.x.1
* EC logger: 192.168.x.100
* Additional flux-related logger(s) like e.g. soil sensor loggers: 192.168.x.101
* Profile system: 192.168.x.102 or .103
* Phenocam(s): 192.168.x.110 to 192.168.x.119
* network-enabled IRGAs (Li7500 RS): 192.168.x.120
* other, non-flux systems (associated loggers like Cosmoz system, surface temperature, radiation, power system control interfaces, managed routers, network-enabled relays, WiFi-extenders, ...): 192.168.x.130 or higher (where possible).

Centralised data download and processing via TERN EPCN requires that IP-addresses for all flux-related devices are known and stable!

`To be debated if loggers (like Cosmoz and surface temperature / radiation loggers) should share adjacent IP-ranges and only non-logger systems use the IP range > .130`

[Home](./Home.html)