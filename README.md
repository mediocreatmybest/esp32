# ESP32 Projects

My miscellaneous ESP32 projects and other unfinished related ESP32 ideas.  
I would love to see any pull requests or improvement suggestions.

## Climate at Home

Climate At Home is a simple, local-first alternative to cloud-based infrared/IR smart climate control.
This is now a very easy replacement due to [Athom RF IR Remote](https://www.athom.tech/) (and other hardware) and [ESPHome Climate](https://esphome.io/components/climate/).
These templates aim to make this as simplified as possible and is designed around the assumption that an IR remote will be the primary controller for the AC or heat pump.

### Features

- Local-first AC control through Home Assistant and ESPHome
- IR-based climate control with state tracking (This does depend on the climate platform being used)
- Configurable AC platform/model settings (for example; Mitsubishi, Daikin)
- Optional mould-reduction or dry-down cycle with timer after an AC is turned off
- Optional simplified timer for ON or OFF after a set period of time (disabled by default).
  - If the device is OFF the auto timer will switch the device ON
  - If the device is ON the auto timer will switch the device OFF
- Enable or disable features with YAML packages in main configuration.
  - Home Assistant Bluetooth Proxy (enabled by default)

TODO:

- Look into RF Controller or RF proxy options for control of other similar types of devices i.e., Fans.
- Add optional maintenance pause switch. Pause any inbuilt automations, e.g., cleaning, etc.
- Look at other hardware, such as Waveshare ESP32 S3 Touch LCD 3.5c.
- Create more modular YAML configurations
  - To allow adding in touch display without touching main climate configurations. e.g., using LVGL with ESPHome with Climate interface.
  - Allow additional connectivity options, e.g., Thread, Wi-Fi.
