# Communication

## Modem

If a site has reasonable 4G/5G coverage, a modem can used for data transmission. In Australia, the recommended -and frequently only - phone network for remote locations is Telstra. TERN EP provides data-only Telstra SIM cards on request. Some towers might not require a 4G modem if there is an internet connection (WiFi, DSL, fibreoptics, fixed-wireless, satellite, ...) readily available. Then a router will suffice.

### 4G modem options

Selection criteria for modems:

-   Operating ranges (voltage, temperature) The modem must be able to operate using the available voltage(s) to avoid conversions. The modem must be able to operate within the anticipated temperature range of a research location. E.g. -20°C to 50°C.

-   Form factor Chose a modem that fits in the available space, especially if all loggers and network devices must fit an a single enclosure. Modems that can be mounted vertically on a DIN rail allow to save space and use the "height" of the enclosure. Many modems offer DIN rail mounts, but some have the rail mount in a location so that it can not be installed in space-saving way. Then adapters might be required.

Recommendations for industrial-grade modems:

-   [Maxon Quadmax MA-6060](https://rfi-sb.rfi.com.au/MA-6060) Slim-line modem, dual SIM slots, four ethernet ports, dual 4G antennas, two WiFi antennas, DIN rail on the thin side. Has built-in analog relay to devices like e.g. phenocam. Capable to connect to OpenVPN, and similar services.

-   [Maxon Dualmax MA-2055](https://rfi-sb.rfi.com.au/MA-2055) Flat, but slightly wide modem, dual SIM slots, two ethernet ports, dual 4G antennas, no WiFi (!), DIN rail on the wide side (not space-saving out of the box). Capable to connect to OpenVPN, and similar services.

-   [Robustel R1520](https://www.rfi.com.au/R1520) Wide modem, dual SIM slots, two ethernet ports, dual 4G antennas, no WiFi (!), DIN rail on the wide side (not space-saving out of the box). Capable to connect to OpenVPN, and similar services.

### Antennas

-   Omnidirectional (omni) antennas are "install and forget": they will connect to any phone network in the area, and can switch between multiple network towers depending on signal strength or if a phone tower goes offline.\

-   Directional (yagi) antennas must be pointing to a known, specific network tower. This will improve the signal. The downside is, that the antenna points to a specific tower. If that network tower goes down, this antenna will not connect to another tower.

In locations with marginal reception, it is recommended to use a modem that allows the use of two antennas, preferably yagi, in parallel (MiMo). Both antennas must be pointing to the same tower (!), and must be about 50 cm apart vertically for optimal boost of marginal signals.\

    -   [Directional antenna, Mimo capable](https://blackhawkantennas.com.au/product/blackhawk-lpda-antenna/)

-   Router Check if a modem provides sufficient ethernet ports (router functionality) for all devices on the local tower network. Consider

### Satellite communication

[Home](./Home.html)