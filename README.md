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
- Optional simplified timer for ON or OFF aftet a set period of time.
  - If the device is OFF the timer will switch the device ON
  - If the device is ON the timer will switch the device OFF
- Home Assistant Bluetooth Proxy

TODO:

- RF Controller
