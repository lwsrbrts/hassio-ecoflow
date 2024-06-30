# @lwsrbrts version - fixing 🐜🐜🐜

I've patched this fork of the Ecoflow integration to resolve all outstanding warnings raised by the integration in Home Assistant up to HA version 2024.6.3.

- The `await` patch - which was a blocking bug.
- The deprecation warnings about constants such as UnitOfEnergy that showed up around HA 2024.4.0.
- Fix the entity category for `...ac_custom_charge_speed` by changing from config (which caused the error) to diagnostic.
- Minor visual fix affecting how the AC frequency select displays entries (showed as `50Hz Hz`, now `50Hz`)
- 30/06/2024 - FIX: Detected that custom integration 'ecoflow' calls async_write_ha_state from a thread other than the event loop, which may cause Home Assistant to crash or data to corrupt.

*Obviously* this integration was originally written by @vwt12eh8 but it seems that he/she has abandoned the repo as it has had no updates or PRs accepted in 2 years. I have changed some bits of the code that point to his repo (such as the manifest.json) but I don't see this being a major issue given the MIT license.

What follows is from the original repo...

# EcoFlow Portable Power Station Integration for Home Assistant

This integration uses a local API.
Therefore, if the devices are not on the same network, they cannot synchronize their status.

This integration uses a private API.
Future device updates may prevent integration.

Requires Home Assistant Core 2022.7.0 or later for operation.

## Installation
This integration is not included by default and must be installed by yourself to use it.

Two methods are available, and you can choose one or the other.
- Install as a custom repository via HACS
- Manually download and extract to the custom_components directory

Once installed, after restarting Home Assistant, you can start integration as usual from Add Integration.

## Supported products
- ~~RIVER Mini~~ (Coming soon)
- RIVER Max
- RIVER Pro
  - Extra Battery
- DELTA Mini
- DELTA Max
  - with Extra Battery
- DELTA Pro (Wi-Fi only)
  - with Extra Battery

## How to register for the Energy Dashboard
- MPPT input energy : Solar Panels -> Solar production energy
- total input energy : Home Battery Storage -> Energy going in to the battery
- total output energy : Home Battery Storage -> Energy coming out of the battery

## About Remain Entities
The Remain entity is disabled by default because it is highly variable and generates a large number of writes to the database.

If enabled, it is recommended that these entities be included in the exclude in the recorder settings.
