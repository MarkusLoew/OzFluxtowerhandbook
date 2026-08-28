# Tips and Tricks for Campbell Scientific data loggers

## CR6 and CR1000x Ethernet connectivity issues, no DHCP lease

In rare occasions, Campbell Scientific data loggers like the CR6 and the CR1000x do not connect to the ethernet network. The loggers does not even appear in the overview table of connected devices of the router. The lights of the ethernet port on the logger do not illuminate - except for a short blink right at connection and second blink about 30 to 60 seconds later and once per minute from then on.

While the logger will come online eventually, this can be very frustrating when working on a tight schedule or when working at heights.

This behaviour is most likely caused by the power saving settings for the ethernet port on the logger:

Connect to your data logger via the Campbell Scientific DevConfig tools. Select the tab "Deployment" -\> "Ethernet":

![Screenshof of the Campbell Scientific DevConfig tool. To change the ethernet power settings, select the tab "Deployment", then "Ethernet". Use the option "Always on" to minimise issues with delayed connection of the data logger to the etherner network. (Markus Loew)](images/tips+tricks/Ethernet_power_saving_setting_on_logger.png)

The default setting is "`1 minute`": `The Ethernet interface powers on for a few seconds every 1 minute to detect an active network link pulse. If a link is present, the interface will remain on until the cable is removed or the network is shut down. This setting allows the Ethernet interface to be available for periodic use without a significant contribution to power consumption when a link is not present` (Campbell Scientific, DevConfig).

From experience, this regular connection short reconnection of the logger to the ethernet netwrok every minute is not always sufficient to detect an active connection. Hence the data logger does not connect immediately. The reason for that is unknown.

To avoid that, select the setting "`Always on`" from the drop-down menu: `The Ethernet interface will always be powered and will contribute approximately 50 mA at 12 Vdc to the power budget regardless of the connectivity. Using this mode is recommended if using IPNetPower() to control Ethernet power under program control` (Campbell Scientific, DevConfig).

With this setting at "Always on" the activity lights on the ethernet port of the logger and router should illuminate immediately when the cable is plugged in. To confirm, check the DHCP client table on your router.