---
bibliography: ./references/References.bib # path and bibliography .bib file name
---

# Phenocams

## Phenocam models

### Campbell Scientific CCFC

Across the TERN OzFlux network, many sites are equipped with the Campbell Scientific [CCFC camera](https://www.campbellsci.com/ccfc).

NDVI images capture is possible.

This camera integrates well with the TERN network as it supports ssh-based sftp file upload via ssh-keys to the TERN data portal automatically. It is the preferred model for TERN-supported flux towers.

The CCFC uses a weatherproof ethernet cable (10 m) for communication and a separate power cable for 9 to 30 V. Settings and live images can be accessed via the built-in WiFi connection.

An external 12V relay (e.g. using the relay available in the Maxon Quadmax modem) to wake the camera from deep sleep. The camera is fully integrated into the Campbell Scientific sensor network and can interact with dataloggers and Loggernet via Pakbus.

To mount the camera the bracket [18549 ACC CC Camera or PWD22 Mounting Kit](https://www.campbellsci.com/order/p18549) is required. Alternatively, Nico provides a custom, versatile mount for it (or provides the CAD drawings to manufacture it yourself).

Ensure the camera has the latest firmware installed! E.g. Older configurations do not add a colour scale to the NDVI images - this makes it difficult to interpret NDVI images across the network.

### Stardot Netcam Live 2

A cheaper alternative to the Campbell Scientific CCFC is the Stardot [Netcam Live 2 camera](http://stardot.com/netcamlive) (StarDot Technologies, Buena Park, CA, USA).
For camera details and a performance review of the Netcam live 2 camera see @javadian_continuity_2025. 

However: **This camera does not capture NDVI images!**

Weatherproof housing and mounting arm must be ordered additionally: [Compact Outdoor Enclosure with Wall Mount Enc-Outd3](http://stardot.com/products/compact-outdoor-enclosure).

See the install scripts provided by ICOS (via bluegreenlabs) at [PhenoCam Installation Tool](https://github.com/icos-etc/phenocam_installation_tool_StardotLive2) for further details regarding configuration and ssh keys.

The Stardot [Knowledge base for the Netcam Live2 camera is available here](https://stardot-kb.netlify.app/kb/files/).

### General / manual upload of phenocam images to TERN

See the upload paths on UQ RDM and the TERN naming conventions at <https://ternaus.atlassian.net/wiki/spaces/TERNSup/pages/2629730756/Phenocam>

The camera above allow to change the filename of the photos to match the pattern expected by TERN.