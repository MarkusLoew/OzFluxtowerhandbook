---
bibliography: ./references/References.bib # path and bibliography .bib file name
---

# Sensor calibration

Of major EC-related instruments

## Anemometer

Usually no DIY calibration possible. Can check the zero by covering the anemometer (plastic bag or similar) in a wind-still room. Regular cleaning required! The wicks can disintegrate and can sometimes block the pathway.

## IRGA

General:

-   ICOS protocol: From @sabbatini_icos_2017 : ICOS require an IRGA to be calibrated twice per year, four times per year if the instrument is new. It is preferred to calibrate the IRGA in the field to minimise downtime. Otherwise, a replacement IRGA must be installed to avoid gaps in the data while the actual IRGA is away for calibration. The zero of H<sub>2</sub>O and CO<sub>2</sub> signals must be checked regularly between the calibrations. The recommended frequency is every two months. In the field, the sensor is not cleaned initially before checking the zero. Thresholds of zero "drifts shall be based on CO2 concentration because more stable (drifts \>30 μmol mol-1 CO<sub>2</sub> are considered significant). As an indication, also H<sub>2</sub>O drifts \> 1.5 mmol mol-1 are considered significant." Factory calibrations of the IRGA is required every second year!

-   World Meteorological Organistation guidelines\
    See their strict guide on the Observations of CO<sub>2</sub>, CH<sub>4</sub> and N<sub>2</sub>O at Global Atmosphere Watch Stations: @world_meteorological_organization_wmo_measurement_2025

-   any Irga calibration papers?

### Licor 7500xxx

-   requires Li7500-specific shroud
-   chemicals get changed before each calibration. It takes 24 hours to flush the system once the chemicals are changed. Only then the actual calibration can take place.

### Campbell Scientific Irgason

-   requires Irgason-specific shroud
-   Chemicals need changing every two years or when drift occurs. Similar to the Licor IRGAs, the system needs to be flushed with the new chemicals for 24 hours before the calibration can happen.

### Checking CO<sub>2</sub> and H<sub>2</sub>O zero in the field

-   Campbell Scientific provide a handheld tool that allows to check the zeros of H<sub>2</sub>O and CO<sub>2</sub> in the field. The tools uses scrubber chemicals to produce "zero" air, ie air without CO<sub>2</sub> or H<sub>2</sub>O. It has a built-in, battery powered pump that circulates the "zero" air through the calibration shroud that is installed in the optical path of the irga (either Licor 7500xx or Campbell Scientific Irgason). A tube connects the "out" port of the Zero Air Generator with the shroud. Air is circulated through the shroud using the battery-powered pump of the device.\
    To check/set the zero, the temperature sensor of the shroud is connected to the control unit of the IRGA to estimate the dew point. The irga must be turned off before connecting / disconnecting the temperature sensor. The instrument-specific software by the manufacturer (*ECmon* or *Licor75xx*) is used to check and potentially set the zero once the system is flushed with "zero" air, and the values are stable (allow 10 min to 20 min). See their instruction manuals for details.

    [Campbell Scientific Zero Air generator](https://www.campbellsci.com.au/31022)

-   This allows a relatively fast, hassle free check of the zero that can be done on location on the tower. A laptop with the instrument control software and USB cable (default USB A to B n case of Campbell Scientific Irgason, or instrument-specific USB-cable in the case of Licor7500a/RS) or serial cable (with specific board adapter in case of Licor 7500) are required.

    ![Using the Campbell Scientific Zero Air Generator on location to check CO<sub>2</sub> and H<sub>2</sub>O zeros of the IRGA. Left: Licor 7500 RS. Right: Campbell Scientific IRGASon (Markus Loew)](images/calibration/zero_air_generator_on_location.jpg)

## Campbell Scientific logger calibration?

-   every few years at manufacturer - who does actually do that? What's the logger drift?