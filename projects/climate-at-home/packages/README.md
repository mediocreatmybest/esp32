# Climate at Home packages

This directory contains our ESPHome YAML packages to implement Climate at Home.

## Directories

| Directory Name | Why?                                                                                                                                           |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `hardware/`    | Used for the physical boards, pin configuration, buses, display drivers, touch drivers, and onboard components, basically...ahh, the hardware. |
| `features/`    | Optional capabilities we wish to use, e.g., Wi-Fi diagnostics, ESPHome's Bluetooth proxy, and similar                                          |
| `legacy/`      | Previous configurations that still need to be separated into packages, this will eventually be removed                                         |

The planned directories include `base/`, `climate/`, `display/`, and `projects/`.

New configurations will eventually import one file from `projects/`.
Until those are available and working, the maintained examples will use the files directly.

The root `climate_home_packages/` directory contains compatibility wrappers for my existing
remote installs. Once the new layout is functional, this too will be removed.

Remote packages do not read user secrets. So all Wi-Fi credentials and API encryption remain in the local ESPHome build configuration.
