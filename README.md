# ESP32 Projects

Some of my miscellaneous ESP32 projects that may contain other unfinished related ESP32 thoughts or ideas that I had.  
I would love to see any pull requests or improvement suggestions.

## Climate at Home

Climate At Home is a simple, local-first alternative to cloud-based infrared/IR smart climate control.
This is now a very easy replacement due to [Athom RF IR Remote](https://www.athom.tech/) (and other ESP32 hardware) and [ESPHome Climate](https://esphome.io/components/climate/).
These templates aim to make this as simplified as possible with additional timer based features and is designed around the assumption that an IR remote will be the primary controller for the AC or heat pump.

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

### Configuration naming

- `climate_supports_*` describes additional capabilities supported by the AC or climate component.
- `enable_*` is being reserved for optional Climate at Home features.
- ESPHome component properties keep their correct naming convention from ESPHome, such as `supports_heat:` and `supports_fan_only:`.

#### WIP

- Waveshare with Touch LCD
- Creating a more modular YAML configuration.
  - Enabling touch display without modifying main climate configurations. e.g., using LVGL with ESPHome with Climate interface.
  - Enabling additional connectivity options, e.g., Thread, Wi-Fi.

#### TODO

- Add RF Controller or at a minimum enable RF proxy options to control other similar types of devices i.e., Fans.
- Add optional maintenance pause switch. Pause any inbuilt automations, e.g., cleaning, etc.
- Look at additional hardware options.
- Find additional examples of climate interfaces with LVGL

##### Possible Improvements and/or Issues

- **Eventually look into advanced ESP32 compatibility settings**
  - The current Athom hardware *(Athom RF IR Remote)* works with `minimum_chip_revision: "3.1"` and enables `sram1_as_iram`.
  - These settings may cause issues on previous ESP32 revisions or other ESP32 hardware.

- **Cleanup climate capabilities, cool, heat, fan, etc.**
  - The timer and LCD interface currently offer modes such as heat, dry, auto and fan-only, can this be cleaned up and pull directly from the main capabilities of the climate component.
  - Should optional controls be compiled in and disabled, or able to be removed from the YAML.
  - How could we make this more modular to avoid one large sprawling logic YAML file, as the timer and mould-reduction features are currently included in the main climate package.
  
- **Look at manufacturer-specific settings inside the example or look at additional examples.**
  - The main example that is in the root directory `climate-at-home.yaml` is the main example YAML, currently configured on Mitsubishi *(As that is what I have...)* devices as an example.
  - Options such as `set_fan_mode` and the ESPHome property `supports_fan_only:` are Mitsubishi-specific in this example. The property receives its value from the shared `climate_supports_fan_only` capability substitution.
  - We should add device specific examples.

- **Add automated ESPHome validation** [x] - Partially done.
  - Could we add GitHub Actions checks or compilation of the base package, as this would highlight any merge issues between YAML files.
  - Suggested configurations include Athom with Mitsubishi, Athom with Bluetooth proxy, a non-Mitsubishi example, and Waveshare with the LCD package.
  - As we need to catch YAML merge errors, obvious typos, or simple unsupported platform options mixing that might break ESPHome from compiling.
