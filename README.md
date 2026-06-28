# ESP32 Projects

My miscellaneous ESP32 projects and other unfinished related ESP32 ideas.

## Climate At Home

Climate At Home is a simple, local-first alternative to cloud-based AC thermostats.
Built around the [Athom RF IR Remote](https://www.athom.tech/) hardware and [ESPHome Climate](https://esphome.io/components/climate/).
Designed around the assumption that the device IR Remote will be the primary controller.

### Features

- Local-first AC control through Home Assistant and ESPHome
- IR-based climate control currently using Athom RF IR Remote hardware
- Configurable AC platform/model settings (example, Mitsubishi)
- Optional mould-reduction dry-down cycle and timer after AC is turned off
- Optional OFF timer to automatically switch the AC off after a set duration
- Home Assistant Bluetooth Proxy

TODO:

- Optional ON timer with different modes
- RF Controller
