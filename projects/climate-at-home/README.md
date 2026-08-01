# Climate at Home

Climate At Home is aimed at being a simple, local-first alternative to cloud-based infrared/IR smart climate control.
This is now a very easy replacement due to [Athom RF IR Remote](https://www.athom.tech/) (and other ESP32 hardware) and [ESPHome Climate](https://esphome.io/components/climate/).
These templates aim to make this as simplified as possible with additional timer based features and is designed around the assumption that an IR remote will be the primary controller for the AC or heat pump.

## Project files

- [Athom Mitsubishi example](examples/athom-mitsubishi.yaml)
- [Waveshare touch remote example](examples/waveshare-touch-remote.yaml)
- [Packages](packages/)
- [Tests](tests/)

## Current features

- Local-first AC control through Home Assistant and ESPHome.
- IR-based climate control with state tracking. _The available state depends on the selected ESPHome climate platform._
- Mould-reduction and automatic ON/OFF timer controls in the current combined climate package.
- A touch interface using the external modular LVGL buttons interface.
- Wi-Fi diagnostic sensors as an optional package.
- Bluetooth proxy as an optional package.

The timer and mould-reduction controls can be enabled or disabled by the user,
but are are currently still compiled together in `packages/legacy/climate-at-home-main.yaml`.

## Current architecture state

| Area                 | Current state                                                                      |
| -------------------- | ---------------------------------------------------------------------------------- |
| Hardware             | Athom, Waveshare, and eventually other hardware to live under `packages/hardware/` |
| Connectivity         | Wi-Fi diagnostics and Bluetooth proxy live under `packages/features/`              |
| Climate behaviour    | Climate core, timer and mould reduction remain in the combined legacy package      |
| Display behaviour    | Waveshare LVGL behaviour still needs separating from display hardware              |
| Project descriptions | Planned; maintained examples currently compose packages directly                   |
| Remote builds        | Compatibility paths are tested; clean remote-manifest tests are planned            |
| Development          | Local Docker testing and remote CI use the same pinned ESPHome version             |

## Configuration naming

- `climate_supports_*` describes additional capabilities supported by the AC or climate component.
- `enable_*` is being reserved for optional Climate at Home features.
- ESPHome component properties now keep their correct naming convention from ESPHome, such as `supports_heat:` and `supports_fan_only:`.

### Work in progress

- Hardware testing and interface refinement for the Touch LCD.
- Separating the shared device base, climate core, optional climate behaviour and display behaviour into smaller more manageable YAML packages.
- Adding project descriptions so each tested device can be imported through one remote package path.
- Adding clean-cache remote tests for potential release tags.

### Planned

- Add RF Controller or at a minimum enable RF proxy options to control other similar types of devices i.e., Fans.
- Add optional maintenance pause switch. Pause any inbuilt automations, e.g., cleaning, etc.
- Look at additional hardware options.
- Find additional examples of climate interfaces with LVGL, as I don't want to reinvent the wheel and others will no doubt do a better job than me.

### Possible improvements and issues

- **Eventually look into advanced ESP32 compatibility settings**
  - The current Athom hardware _(Athom RF IR Remote)_ works with `minimum_chip_revision: "3.1"` and enables `sram1_as_iram`.
  - These settings may cause issues on previous ESP32 revisions or other ESP32 hardware.

- **Cleanup climate capabilities, cool, heat, fan, etc.**
  - The timer and LCD interface currently offer modes such as heat, dry, auto and fan-only, can this be cleaned up and pull directly from the main capabilities of the climate component.
  - Should optional controls be compiled in and disabled, or able to be removed from the YAML.
  - How could we make this more modular to avoid one large sprawling logic YAML file, as the timer and mould-reduction features are currently included in the main climate package.

- **Look at manufacturer-specific settings inside the example or look at additional examples.**
  - The maintained example at `examples/athom-mitsubishi.yaml` is currently configured for Mitsubishi devices _(as that is what I have)_.
  - Options such as `set_fan_mode` and the ESPHome property `supports_fan_only:` are Mitsubishi-specific in this example. The property receives its value from the shared `climate_supports_fan_only` capability substitution.
  - We should add more useful device specific examples.

- **Anything elsE?.**
  - Feel free to make any suggestions, improvements, or pull requests, etc.
