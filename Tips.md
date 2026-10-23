# Tips and Tricks

## Campbell Scientific data loggers

### CR6 and CR1000x Ethernet connectivity issues, no DHCP lease

In rare occasions, Campbell Scientific data loggers like the CR6 and the CR1000x do not connect to the ethernet network when the ethernet cable gets plugged in. The loggers does not even appear in the overview table of connected devices of the router. The lights of the ethernet port on the logger do not illuminate either - except for a short blink right at connection and second blink about 30 to 60 seconds later and once per minute from then on.

While the logger will come online eventually, waiting for the connection can be very frustrating when working on a tight schedule or when working at height.

This behaviour is most likely caused by the power saving settings for the ethernet port on the logger:

Connect to your data logger via the Campbell Scientific DevConfig tools. Select the tab "Deployment" -\> "Ethernet":

![Screenshot of the Campbell Scientific DevConfig tool. To change the ethernet power settings, select the tab "Deployment", then "Ethernet". Use the option "Always on" to minimise issues with delayed connection of the data logger to the ethernet network. (Markus Loew)](images/tips+tricks/Ethernet_power_saving_setting_on_logger.png)

The default setting is "`1 minute`": From Campbell Scientific, DevConfig help:

`The Ethernet interface powers on for a few seconds every 1 minute to detect an active network link pulse. If a link is present, the interface will remain on until the cable is removed or the network is shut down. This setting allows the Ethernet interface to be available for periodic use without a significant contribution to power consumption when a link is not present`.

From experience, this regular, but short reconnection of the logger to the ethernet network every minute is not always sufficient to detect an active connection. Hence the data logger does not connect immediately. The reason for that is unknown.

To avoid that, select the setting "`Always on`" from the "Ethernet power" drop-down menu:

`The Ethernet interface will always be powered and will contribute approximately 50 mA at 12 Vdc to the power budget regardless of the connectivity. Using this mode is recommended if using IPNetPower() to control Ethernet power under program control` (from Campbell Scientific, DevConfig).

With this setting at "Always on" the activity lights on the ethernet port of the logger and router should illuminate immediately when the cable is plugged in. The logger should connect. To confirm, check the DHCP client table on your router.

## Critters

### Critters and conduit

Stuff some steel wool into the end of any open conduit, cable ducts, or open cable glands. That will keep animals, including larger insects, out of the cable ducts. Ants will still get through, though! Replace the steel wool regularly, as it rusts and deteriorates quickly.

## Birds

Birds like to nibble on cables. Use rigid or split conduit or even metal conduit to protect cables from getting eaten.

Use bird spikes to keep them away from sensitive instruments.

[Home](./Home.html)