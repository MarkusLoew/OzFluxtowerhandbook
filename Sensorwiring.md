# Sensors and wiring

This guide applies to tower using the OzFLux standard programs (available from github..., Ian McHugh). Detailed Sensor and wiring information for the Campbell EasyFux system is available here (EasyFlux manual).

## Wiring information

This wiring guide is for an all-in one flux tower system. This system consists of one logger with extension module handling all sensors at once, wired up in a single enclosure. Examples of towers using this wiring scheme and standard program are: Boolcoomatta, the three Dookie towers. Even if logger, extension module and soil system are separate from each other, the basic wiring still applies to some extent. Hardware used: - Campbell Scientific CR1000x(e) data logger - Campbell Scientific Volt116 extension module - Campbell Scientific Irgason - Kipp & Zonen CNR4 four-component radiometer - Vaisala HMP155 temperature and humidity sensor - Apogee PAR sensor - Hukseflux FG01 soil heat flux (two at Dookie towers, four for Boolcoomatta tower) - Campbell Scientific TCAV averaging soil temperature probe (two for Dookie towers, four for Boolcoomatta) - Campbell Scientific CS650 soil mositure probe (four for Dookie towers, and Boolcoomatta tower) - Campbell Scientific SoilVUE10 soil profile probe (Boolcoomatta only)

### User constants

Some parts of the standard program must be modified to unique settings for each tower.

Data logger constants:

`Const STATION_NAME = "Dookie2_EC" Const PAKBUS_ADDR = 1`

`'Server information for data upload`

`Const Server = "server.address.au"`

`Const User = "username" Const Pass = ""`

VOLT116 user constants

`Const CDMVOLT116_1_SN = 1234 ' CDM-VOLT116 serial number ser no 7008 in Dookie1`

`Const CDMVOLT116_1_ADDR = 1 ' CDM-VOLT116 CPI address (default is 1)`

`Const CDMVOLT116_1_DESC = "Mux_Tower" ' CDM-VOLT116 descriptor (name for instrument, even in case there is only one Volt116)`

### Irgason (Campbell Scientific) / 7500RS Irga (Licor) + CSat3b (Campbell Scientific)

The integrated irga and 3D anemometer (Irgason) and separate instruments Licor 7500RS irga plus 3D anemometer Cambell Scientific are wired in a similar way. All instruments communicate via the SDM bus when using the OzFlux standard program. The SDM cables for the two separate iga/anemometer get combined in a SDM hub, and only one cable connects both to the data logger. See section on SDM hub for details when using separate IRGA and CSat.

Wiring and constants.

`Const EC100_SDM_ADDR = 1 'Unique SDM address for EC100.`

`Const CO2_SIG_STRGTH_THRESHOLD = 0.7 'Remove gas analyzer CO2 data when CO2 signal strength is less than sig_str_CO2.`

`Const H2O_SIG_STRGTH_THRESHOLD = 0.7 'Remove gas analyzer H2O data when H2O signal strength is less than sig_str_H2O.`

| Logger port | Function      | Wire colour |
|-------------|---------------|-------------|
| C1          | SDM data      | green       |
| C2          | SDM data      | white       |
| C3          | SDM enable    | brown       |
| G           | SDM reference | black       |
| g           | SDM shield    | clear       |
| 12V         | Power         | red         |
| G           | Ground        | black       |
| G           | Powers shield | clear       |

### Soil heat flux

The unique calibration coefficients must be entered for each sensor. Calibration coefficients are printed on the cable and anre also available on the calibration sheet provided by the manufacturer.

`Const SHF_ANALOG_INPUT = 1 'Unique differential analog input channel.`

`Const NMBR_SHF = 2 'Unique number of HFP01 to measure.`

`Const SHF_FIELDS = "Fg_01,Fg_02" 'Field names, ie names in the data table`

`Const SHF_CAL_1 = 61.12 'Unique coefficient for HFP #1 (1000/sensitivity). Example for HFP01 #23316 61.12 uF/V`

`Const SHF_CAL_2 = 60.38 'Unique coefficient for HFP #2 (1000/sensitivity). HFP01 #23317`

`Data SHF_CAL_1 ' must be present for each unique heat flux sensor`

`Data SHF_CAL_2 ' must be present for each unique heat flux sensor`

| Logger port | Function               | Wire colour |
|-------------|------------------------|-------------|
| 1H          | HFP01 signal           | white       |
| 1L          | HFP01 signal reference | green       |
| gnd         | HFP01 shield           | clear       |
| 2H          | HFP02 signal           | white       |
| 2L          | HFP02 signal reference | green       |
| gnd         | HFP02 shield           | clear       |

If more than two soil heat flux plates are used, expand the program user constants and wiring accordingly.

### PAR sensor

Apogee CS310 PAR sensor program constants and wiring:

`Const PAR_ANALOG_INPUT = 9 ' specify unique SE analog input channel for the PAR sensor`

`Const PAR_MULT = 100 ' Multiplier provided by manufacturer and/or printed on cable, default is 100.0`

| Logger port | Function          | Wire colour |
|-------------|-------------------|-------------|
| 5H          | PAR signal        | white       |
| gnd         | PAR signal ground | black       |
| gnd         | PAR shield        | clear       |

' -\> Soil temperature user constants / wiring (CR1000X)

`Const TSOIL_ANALOG_INPUT = 3 'Unique differential analog input channel. Const NMBR_TSOIL = 2 'Unique number of TCAV to measure.`

### Averging soil temperature thermocouple (TCAV)

'TCAV #1 '3H Signal (purple) '3L Signal reference (red) 'gnd Shield (clear)

'TCAV #2 '4H Signal (purple) '4L Signal reference (red) 'gnd Shield (clear)

### Soil moisture user constants / wiring (CR1000X)

`Const CS65X_1_SDI12_PORT = C5 'Unique control port. Const CS65X_2_SDI12_PORT = C7 'Unique control port. Const NMBR_CS65X = 4 'Unique number of CS65X to measure.`

`C5 SDI-12 data #1 (SDI-12 address = 0) (green) 'C7 SDI-12 data #2 (SDI-12 address = 0) (green) 'G RS-232 Rx #1 (orange) ' RS-232 Rx #2 (orange)`

`12V SDI-12 power #1 (red) ' SDI-12 power #2 (red) 'G SDI-12 data/power reference #1 (black) ' Shield #1 (clear) ' SDI-12 data/power reference #2 (black) ' Shield #2 (clear)`

### Rain gauge user constants / wiring (CR1000X)

`Const RAIN_PULSE_INPUT = P1 'Unique pulse input channel for tipping bucket.`

`Const RAIN_CAL = 0.2 'Unique multiplier for tipping bucket.`

`'P1 Signal (black) 'G Signal reference (white) ' Shield (clear)`

### Air temperature and humidity (Vailsala HMP155 wired to Volt116)

`Const T_RH_ANALOG_INPUT = 1 'Unique differential input channel for temperature and humidity probe. Const T_RH_T_MULT = 0.14 'Unique multiplier for temperature; HC2S3 = 0.1, HMP155A = 0.14, or HMP45C = 0.1. Const T_RH_T_OFFSET = -80 'Unique offset for temperature; HC2S3 = -40, HMP155A = -80, or HMP45C = -40.`

`' Dookie2 HMP155 ser No V4720665 (2023) '1H Temperature signal (yellow) HMP155: yellow '1L Temperature signal reference HMP155: white(orange in loop with 11L, was purple, was white) --> Jumper to white 'gnd Shield '2H RH signal (blue) HMP155: blue '2L RH signal reference HMP155 only one signal reference for temp and rH: white 1L (orange, was purple, was white) '12V Power (red) 'G Power reference (black)`

### 4-component radiation user constants / wiring (Kipp & Zonen CNR4 wired to VOLT116)

`Const NR_ANALOG_INPUT = 3 'Unique differential analog input channel.`

`Const NR_TsENS_ANALOG_INPUT = 13 'Unique single-ended analog input channel for body T`

`Const NR_TsENS_VX = X2 'Unique voltage excitation channel for thermistor`

`Const NR_SW_INCOMING_CAL = 1000/12.82 'Unique multiplier for CNR 4 shortwave incoming radiation (1000/sensitivity). Kipp+Zonen CNR4 Ser No 234203 (Dec 2023) Const NR_SW_OUTGOING_CAL = 1000/12.63 'Unique multiplier for CNR 4 shortwave outgoing radiation (1000/sensitivity). Kipp+Zonen CNR4 Ser No 234203 (Dec 2023)`

`Const NR_LW_INCOMING_CAL = 1000/9.09 'Unique multiplier for CNR 4 longwave incoming radiation (1000/sensitivity). Kipp+Zonen CNR4 Ser No 2234203 (Dec 2023)`

`Const NR_LW_OUTGOING_CAL = 1000/9.41 'Unique multiplier for CNR 4 longwave outgoing radiation (1000/sensitivity). Kipp+Zonen CNR4 Ser No 234203 (Dec 2023)`

`'3H Incoming shortwave radiation signal (red) '3L Incoming shortwave radiation signal reference (blue) 'gnd Shield (clear) ' short jumper wire to 3L '4H Outgoing shortwave radiation signal (white) '4L Outgoing shortwave radiation signal reference (black) 'gnd short jumper wire to 4L '5H Incoming longwave radiation signal (gray) '5L Incoming longwave radiation signal reference (yellow) 'gnd short jumper wire to 5L '6H Outgoing longwave radiation signal (brown) '6L Outgoing longwave radiation signal reference (green) 'gnd short jumper wire to 6L '7H Thermistor signal (white) 'gnd Thermistor signal reference (black) ' Shield (clear) 'X2 Thermistor excitation (red)`

-   The Kipp and Zonen CNR sensor provided cables are different than the cable provided by Campbell Scientific! Campbell Scientfic adds a resistor to the cable!

Kipp and Zonen yellow Thermistor yellow cable has different colours and requires to add an additional resistor to the wiring panel as follows:

`'7H Thermistor signal (white)`

`'gnd thin black Thermistor signal reference (thin black)`

`' Shield (thick black)`

`'X2 Thermistor excitation (brown)`

`'1kOhm resistor between X2 (brown) and 7H (white)`