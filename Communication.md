# Communication

## Direct download from data logger

In the simplest case, communication with a logger can be done by directly, by connecting a computer to the logger and downloading the data manually. This method is straightforward but requires physical access to the logger.

### Serial communication

Many modern computers don't have a serial port, so a USB-to-serial adapter may be required. Recommended serial-to-usb adapters:

[FTDI Chip model US232R-10 usb to RS232](https://ftdichip.com/products/us232r-10-bulk/)


Available via e.g. [RS-online](https://au.rs-online.com/web/p/interface-adapters-converters/0429274)


Check your computer settings what serial port the adapter is using. Windows: check "`Device manager`", section "ports". Linux: check `ls /dev/tty*` for new devices.

Latest generation Campbell Scientific and other manufacturer's loggers have built in USB-to-serial converters, no dedicated serial cable and plug are required. The communication protocol is still RS232 and it is still required what serial port is used for communication.

## Modem

If a site has reasonable 4G/5G coverage, a modem can used for data transmission. In Australia, the recommended -and frequently only - phone network for remote locations is Telstra. TERN EP provides data-only Telstra SIM cards on request. Some towers might not require a 4G modem if there is an internet connection (WiFi, DSL, fibreoptics, fixed-wireless, satellite, ...) readily available. Then a router will suffice.

### 4G modem options

Selection criteria for modems:

-   Operating ranges (voltage, temperature): The modem must be able to operate using the available voltage(s) to avoid conversions. The modem must be able to operate within the anticipated temperature range of a research location. E.g. -20°C to 50°C.

-   Form factor: Chose a modem that fits in the available space, especially if all loggers and network devices must fit an a single enclosure. Modems that can be mounted vertically on a DIN rail allow to save space and use the "height" of the enclosure. Many modems offer DIN rail mounts, but some have the rail mount in a location so that it can not be installed in space-saving way. Then adapters might be required.

Recommendations for industrial-grade modems:

-   [Maxon Quadmax MA-6060](https://rfi-sb.rfi.com.au/MA-6060) Slim-line modem, dual SIM slots, four ethernet ports, dual 4G antennas, two WiFi antennas, DIN rail on the thin side. Has built-in analog relay to devices like e.g. phenocam. Capable to connect to OpenVPN, and similar services.

-   [Maxon Dualmax MA-2055](https://rfi-sb.rfi.com.au/MA-2055) Flat, but slightly wide modem, dual SIM slots, two ethernet ports, dual 4G antennas, no WiFi (!), DIN rail on the wide side (not space-saving out of the box). Capable to connect to OpenVPN, and similar services.

-   [Robustel R1520](https://www.rfi.com.au/R1520) Wide modem, dual SIM slots, two ethernet ports, dual 4G antennas, WiFi, DIN rail on the wide side (not space-saving out of the box). Capable to connect to OpenVPN, and similar services.

-   [Belden Netmodule 1601](https://www.belden.com/products/industrial-networking-cybersecurity/wireless/iiot-and-industrial-routers/nb1601-lsc) Slim-line modem, dual SIM slots, four ethernet ports, dual 4G antennas, two WiFI antennas, DIN rail on the thin side. Has built-in analog relay to devices like e.g. phenocam. Capable to connect to OpenVPN, and similar services.

-   [Campbell Scientific Cell220](https://www.campbellsci.com.au/cell220) Serial modem well integrated the the Campbell Scientifc logger ecosystem. The Modem is conveniently configured via the logger program (CRBasic). This modem can interact directly with logger, and data and provides diagnostic output (like signal strength, uptime) to data tables on the logger. Modem actions can be triggered depending on logger or measurement status. No WiFi, no ethernet ports, dual antenna, single SIM card. Small form factor, highly configurable. Similar serial modems are available elsewhere too, as long as they support he full range of AT modem commands (ie Netmodule NB1600).

### Antennas

-   Omnidirectional (omni) antennas are "install and forget": they will connect to any phone network in the area, and can switch between multiple network towers depending on signal strength or if a phone tower goes offline.\

-   Directional (yagi) antennas must be pointing to a known, specific network tower. This will improve the signal. The downside is, that the antenna points to a specific tower. If that network tower goes down, this antenna will not connect to another tower.

In locations with marginal reception, it is recommended to use a modem that allows the use of two antennas, preferably yagi, in parallel (MiMo). Both antennas must be pointing to the same tower (!), and must be about 50 cm apart vertically for optimal boost of marginal signals.\

-   [Directional antenna, Mimo capable](https://blackhawkantennas.com.au/product/blackhawk-lpda-antenna/)

## Satellite communication

to do


## Router

Check if a modem provides sufficient ethernet ports (router functionality) for all devices on the local tower network. Consider a modem with sufficient built-in ethernet ports. Avoid office-grade network routers. They are susceptible to power surges, lightning strikes and do not operate well at high or low temperatures. Check if what data transmission rates are required at a research tower. Chose a GBit capable-router if required (ie for high-frequency spectral data). Many industrial MBit-routers offer sufficient performance for most flux-related data transfer and are more robust.

### Router recommendations

-   [Industrial 5-port 100 MBit router](https://www.brainboxes.com/product/industrial-ethernet-switches/fast-ethernet/sw-505) (5 to 30V, DIN rail mount)

-   [Industrial 8-port 100 MBit router](https://www.brainboxes.com/product/industrial-ethernet-switches/fast-ethernet/sw-508) (5 to 30V, DIN rail mount)

General network routers like office-grade, indoor routers (e.g. Netgear) are known to be more susceptible to electrical interference (lightning, power surges) and do not operate well at extreme temperatures compared to these "industrial" routers.


[Home](./Home.html)