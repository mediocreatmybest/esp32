# Climate at Home

Climate at Home is my local-first alternative to cloud-based IR climate controllers. It
uses [ESPHome Climate](https://esphome.io/components/climate/) and hardware such as the
[Athom RF IR Remote](https://www.athom.tech/).

The original IR remote is still assumed to be the main controller. ESPHome adds Home
Assistant control, state tracking, timers, and a few other useful bits around it.

## Project files

- [Athom Mitsubishi example](examples/athom-mitsubishi.yaml)
- [Waveshare touch remote example](examples/waveshare-touch-remote.yaml)
- [Packages](packages/)
- [Tests](tests/)

## Current features

- Local AC control through Home Assistant and ESPHome.
- IR climate control with whatever state tracking the selected climate platform supports.
- Mould-reduction and automatic ON/OFF timers.
- A touch interface using the external modular LVGL buttons interface.
- Optional Wi-Fi diagnostics and Bluetooth proxy packages.

## Current state

Hardware and optional connectivity now have their own packages. The climate core,
timers, and mould reduction now have their own packages as well.

The timer and mould-reduction packages can be left out of a build. Project manifests
compose the supported local builds; the old combined package remains for compatibility.
Public examples still compose packages directly until remote consumer tests are in
place.

Climate packages publish a shared `OFF`, `ON`, or `DRY_DOWN` status. A selected adapter
turns that into an Athom LED, a future display indicator, or nothing at all.

## Naming

- `climate_supports_*` describes additional capabilities supported by the AC or climate component.
- `enable_*` is being reserved for optional Climate at Home features.
- ESPHome component properties now keep their correct naming convention from ESPHome, such as `supports_heat:` and `supports_fan_only:`.

## Work in progress

- Test the hardware and tidy up the touch LCD interface.
- Split the display behaviour into smaller packages.
- Add clean-cache remote tests before using release tags.

## Planned

- Add an RF controller, or at least RF proxy options, for things such as fans.
- Add an optional maintenance switch to pause built-in automations while cleaning.
- Look at additional hardware options.
- Find additional examples of climate interfaces with LVGL, as I don't want to reinvent the wheel and others will no doubt do a better job than me.

## Possible improvements and issues

- **Advanced ESP32 compatibility settings**
  - The current Athom hardware _(Athom RF IR Remote)_ works with `minimum_chip_revision: "3.1"` and enables `sram1_as_iram`.
  - These settings may cause issues on previous ESP32 revisions or other ESP32 hardware.

- **Clean up climate capabilities: cool, heat, fan, etc.**
  - The timer and LCD currently list modes themselves. Can they use the climate component's capabilities instead?
  - Optional controls should eventually be removable instead of compiled in and disabled.
  - The timer and mould-reduction logic are now separate; the display interface still needs the same treatment.

- **Manufacturer-specific settings and examples**
  - `examples/athom-mitsubishi.yaml` is configured for Mitsubishi devices _(as that is what I have)_ and includes Mitsubishi-specific fan settings.
  - More useful device-specific examples would be handy.

- **Anything elsE?**
  - Feel free to make any suggestions, improvements, or pull requests, etc.
