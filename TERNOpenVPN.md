# Virtual provate networks

-   OpenVPN (TERN)
-   Kinect (Campbell Scientific)
-   DynDNS

## TERN OpenVPN setup

(Ian McHugh)

### General description

We use openVPN for connection and upload / download of data to and from the loggers and other IP-capable devices. This gives us a secure, network-wide solution that offers access to both the modem router and the devices connected to its local area network. This is invaluable for allowing remote configuration. The initial configuration consists of 5 main steps (steps 1-3 are device-specific, and are covered in further detail based on device subsequently):

1.  Establish openVPN connection

This consists of configuring the modem / router as an openVPN client with settings that allow secure connection to the openVPN server via specific encryption protocols, in combination with a key file or files the user uploads to the device. The file(s) can be acquired from TERN EP central.

2)  Configure LAN IP

This consists of applying subnetwork settings for the modem itself, and for the IP range covered by the DHCP server (from within which specific IP addresses will be assigned to client hardware). Note that site VPN IP and subnet IP addresses are specifically tied to individual sites.

3)  Configure DHCP server

This consists of assigning fixed local IP addresses to different hardware components (loggers, IP cameras, IRGAs etc) based on their unique MAC addresses.

4)  Configure hardware to use DHCP

This is generally only required / relevant for loggers, but ensures that they request IP leases via DHCP - and thus have a predictable IP address assigned, as per (3) above - instead of assigning the IP address within the hardware itself, which increases both the complexity of the configuration (multiple pieces of hardware must be configured correctly for the system to work) and the potential for IP collisions.

5)  Configure remote PC and communications software

To enable communications between the modem / router and a remote machine, openVPN client software must also be running on the remote machine. You may need to check your IT departmental policy on the use of openVPN, as some universities may stop openVPN traffic by default. In most cases, hardware devices are accessed via support software. The main software package of most relevance to most researchers is Campbell Scientific’s Loggernet package, to which instructions herein are confined. Please contact TERN EP central node to discuss connection / configuration / communication needs for other hardware.

DEVICE-SPECIFIC SETTINGS

MAXON Datamax MA100-1010/1020-4G applicable to Quadmax MA-6060 as well.

Connect to the modem (usually via ethernet – username and password on a unit fresh out of the box are ‘admin’ and ‘admin’, and the default IP address is 192.168.0.1), and check that you have web connectivity. On the front panel of the device, the ‘Online’ LED will be lit if all is well. Check that you have the most recent firmware version (listed at top right in Figure 1 below). Many of the requisite openVPN settings may not be available if your firmware version is not current. Maxon firmware updates can be accessed here:

[https://www.rfi.com.au/MA100-1010-4G](http://support.maxon.com.au/download/Datamax+%20-%20MA100-1010/)

<http://support.maxon.com.au/download/MA-6060/>

0)  Update firmware to enable TLS cipher options for OpenVPN

See status website of router, Firmware version should be: v3.0.2-100-1020(Aug 23 2021 11:03:31) std - build 5656M

To update the firmware, get the file from here:

<http://support.maxon.com.au/download/Datamax%20LoRa/Firmware/>

File: uimage-MA100-1020-V3.0.2-20210823.flash

Use network connection to Maxon datamax to write the new firmware to device

1)  Establish openVPN connection

Under ‘Advanced Features’ → ‘OPENVPN’, ensure settings match those in Figure 1. Further down the same admin page, we can upload the requisite certificates / keys for secure connection (Figure 2). In the case of the Maxon modems, the text in the single file issued to the site user must be split into four sections (to minimise editing – and potential introduction of unwanted edits/characters in the originally-issued file - it is best to create local subfiles for each of the below), which are uploaded by cutting and pasting the relevant sections of text into the appropriate text boxes, as follows (Maxon text box headings in quotations):

-   `‘TLS Auth Key’: the section of text between <tls-auth> and </tls-auth>, including only the text between (and INCLUSIVE OF) “-----BEGIN OpenVPN Static key V1-----” and “-----END OpenVPN Static key V1-----”`

-   ‘`CA Cert’ (Root certificate): the section of text between <ca> and </ca>, including only the text between (and INCLUSIVE OF) “-----BEGIN CERTIFICATE-----” and “-----END CERTIFICATE-----”`

-   `‘Public Client Cert’ (Public certificate): the section of text between <cert> and </cert>, including only the text between (and INCLUSIVE OF) “-----BEGIN CERTIFICATE-----” and “-----END CERTIFICATE-----”`

-   `‘Private Client Key’ (Private key): the section of text between <key> and </key>, including only the text between (and INCLUSIVE OF) “-----BEGIN PRIVATE KEY-----” and “-----END PRIVATE KEY-----”`

If this has been configured successfully, you should now be able to access the VPN. To confirm successful connection, select ‘Status’ → ‘OpenVPN’. A successful connection should appear as shown in Figure 3 (‘CONNECTED SUCCESS’ reported under ‘State’). If the text boxes on this page are blank, then you do not have a working openVPN connection.

![](ovpn_modem_setup_instructions_ML_html_7bcd34e0.png)

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_7bcd34e0.png)

*Figure 1: Maxon openVPN settings.*

![Shape2](ovpn_modem_setup_instructions_ML_html_1adc9aae.gif)

![](ovpn_modem_setup_instructions_ML_html_db8592fa.png)

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_db8592fa.png)

*Figure 2: Maxon openVPN settings (continued).*

![Shape3](ovpn_modem_setup_instructions_ML_html_1adc9aae.gif)

![](ovpn_modem_setup_instructions_ML_html_21c86555.png)

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_21c86555.png)

*Figure 3: Maxon openVPN connection confirmation.*

2)  Configure LAN IP

Under ‘LAN and WAN Setup’ → ‘LAN’, set the local IP address of the device to the assigned subnet IP for the site (Figure 4; note that the IP assignment has already been altered for the router in the figure – a new router will have default device IP as noted above; see Appendix A for a list of site-assigned IP addresses). Change the ‘Network Address Server Settings (DHCP)’ start IP address to be compatible with (but not collide with) the device IP address (in Figure 4, start IP address is 192.168.2.100).

Once these settings are applied, you may lose access to the modem, as your connection is to an IP address that is no longer applicable. Reconnect via ethernet using the newly configured IP address.

![Shape4](ovpn_modem_setup_instructions_ML_html_1adc9aae.gif)

![](ovpn_modem_setup_instructions_ML_html_e48a7d67.png)

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_e48a7d67.png)

*Figure 4: Maxon LAN settings.*

3)  Configure DHCP server

This step requires that the MAC addresses of the devices be known (see section 5 for information about obtaining MAC addresses for loggers and other devices). Under ‘LAN and WAN Setup’ → ‘Services’, in the ‘DHCP server’ panel (Figure 5), click ‘Add’, and enter MAC address, Host Name (the name the device will appear as in the DHCP client table) and desired IP address (note this must be in the IP range set in ‘LAN and WAN Setup’ → ‘LAN’). Client Lease Time can be left at the default 1440 minutes (meaning lease is renewed daily, but the same client hardware – as identified by MAC address - will always get the same IP lease).

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_bf34a289.png)

*Figure 5: Maxon DHCP IP reservation.*

SIERRA WIRELESS RV50X[1](#sdfootnote1sym)

Connect to the modem (usually via ethernet – username and password on a unit fresh out of the box are ‘user’ and ‘12345’, and the default IP address is 192.168.13.31 [2](#sdfootnote2sym)), and check that you have web connectivity. On the front panel of the device, the network LED will be lit if all is well (see url for manual in footnote below – LED descriptions in Table 8-1, p37). Check that you have the most recent firmware version (under ‘Software and Firmware’ button at top of screen). Many of the requisite openVPN settings may not be available if your firmware version is not current. Sierra firmware (radio and carrier) updates can be accessed here:

<https://source.sierrawireless.com/resources/airlink/software_downloads/rv50/rv50-firmware-list/>

1)  Establish openVPN connection

In the top menu under ‘VPN’, select ‘VPN1’ from the side menu and ensure settings match those in Figure 6. On the same page, we can upload the requisite certificates / keys for secure connection. In the case of the RV50X, the text in the single file issued to the site user must be split into four separate files and saved locally, then uploaded separately (RV50X text box headings in quotations):

-   `‘Load Root Certificate’ (Root certificate): saved file encapsulating section of text between <ca> and </ca>, including only the text between (and INCLUSIVE OF) “-----BEGIN CERTIFICATE-----” and “-----END CERTIFICATE-----”`

-   `‘Load Client Certificate’ (Public certificate): saved file encapsulating section of text between <cert> and </cert>, including only the text between (and INCLUSIVE OF) “-----BEGIN CERTIFICATE-----” and “-----END CERTIFICATE-----”`

-   `‘Load Client Certificate Key’ (Private key): the section of text between <key> and </key>, including only the text between (and INCLUSIVE OF) “-----BEGIN PRIVATE KEY-----” and “-----END PRIVATE KEY-----”`

-   `‘Load Client TLS Key’ (TLS Authentication Key): saved file encapsulating section of text between <tls-auth> and </tls-auth>, including only the text between (and INCLUSIVE OF) “-----BEGIN OpenVPN Static key V1-----” and “-----END OpenVPN Static key V1-----”`

If this has been configured successfully, you should now be able to access the VPN. To confirm successful connection, ‘VPN1 Status’ at the top of the page should show ‘Connected’ (Figure 6).

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_fb59a2d7.png)

*Figure 6: Sierra RV50X openVPN settings.*

2)  Configure LAN IP

On the tab menu, select ‘LAN’, then from the left hand menu select ‘Ethernet’. Set the device IP address to the assigned subnet IP address for the site (Figure 7; note in the image the IP assignment is for Wombat State Forest site – a new router will have the default IP as above; see Appendix A for a list of assigned site IP addresses). Change ‘Starting IP’ and ‘Ending IP’ to be compatible with (but not collide with) the device IP address (in Figure 7, IP range is 192.168.12.100 → 192.168.12.150).

Once these settings are applied, you may lose access to the modem, as your connection is to an IP address that is no longer applicable. Reconnect via ethernet using the newly configured IP address.

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_93dbaff4.png)

*Figure 7: Sierra RV50X LAN settings.*

3)  Configure DHCP server

This step requires that the MAC addresses of the devices be known (see section 5 for information about obtaining MAC addresses for loggers and other devices). On the tab menu, select ‘LAN’, then from the left hand menu select ‘DHCP/Addressing’. In the ‘Reservation List’ box, select ‘Add More’, then enter MAC address and corresponding IP address for each IP-capable device to be deployed (Figure 8).

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_621cb8a.png)

*Figure 8: Sierra RV50X DHCP IP reservation.*

4)  Configure hardware to use DHCP

Loggers and other IP-capable hardware (e.g. Campbell Scientific CCFC and other field cameras) must be connected to the modem via Ethernet. If the modem has only a single Ethernet port (e.g. RV50X), then a multi-port Ethernet switch (such as Brainboxes SW504 12V 4-port switch) must be used to expand the number of devices that can be connected.

In Loggernet’s Device Configuration Utility, ‘Deployment’ tab, ensure the IP address in the ‘Ethernet’ sub-tab is set to ‘0.0.0.0’ (default; Figure 9 below). This ensures that the logger is assigned the IP address registered to the logger’s MAC address in the DHCP server settings. Note here that the MAC address of the logger is also visible on this page.

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_5dcdc6e1.jpg)

*Figure 9: Logger IP setup.*

While configuring the logger, the TCP Port should also be set / noted (Figure 10; default is 6785 - this can be left as is for most configurations); this is required for subsequent connection.

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_13c33a20.jpg)

*Figure 10: Logger Pakbus/TCP setup.*

5)  Configure remote PC and communications software

Finally, in Loggernet’s ‘Setup’ utility, configure the IP and port numbers for the logger (Figure 11).

![](images/ovpn_images/ovpn_modem_setup_instructions_ML_html_96095c48.jpg)

*Figure 11: Loggernet Setup configuration.*

[1](#sdfootnote1anc) Campbell Scientific is a reseller of these modems; the Campbell manual for their use can be found here: <https://s.campbellsci.com/documents/au/manuals/rv50.pdf>

[2](#sdfootnote2anc) RV50(X)s running OS version 4.13 and older had both HTTP port 9191 and HTTPS port 9443 enabled by default. When using HTTP (not HTTPS) with these older OS versions, enter the IP address using port number 9191, for example, http://192.168.13.31:9191. You may be warned that the connection is not secure – allow an exception for this address and continue.