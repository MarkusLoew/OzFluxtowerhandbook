# Network settings within OzFlux

## Network level
Each flux tower has an assigned network IP range within the TERN OpenVPN network. IP addresses are provided and managed by TERN (contact Gerhard or Ian for access).
TERN OpenVPN provides a secure VPN connection for remote access to the flux tower network, each tower sites uses a unique private network mask in the 192.168.x.x range.

## Site level
Each flux tower site has its own local network, typically using a private IP range within the 192.168.x.x subnet. This local network connects all devices at the site, including data loggers, modems, and routers.
To make network management easier, it is recommended that all sites use similar device-to-IP address mappings:

* Modem: 192.168.x.1
* EC logger: 192.168.x.100
* Additional logger like e.g. soil sensor loggers: 192.168.x.101
* Profile system: 192.168.x.103
* Phenocam(s): 192.168.x.110 to 192.168.x.119
* network-enabled IRGAs (Li7500 RS): 192.168.x.120
* other items (associated loggers like Cosmoz system, surface temperature, radiation loggers, power system controllers, WiFi-extenders, ...): 192.168.x.130 or higher
