# Climate at Home packages

This directory contains the ESPHome YAML packages to implement Climate at Home.

## Directories

| Directory Name | Why?                                                                                                                                           |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `hardware/`    | Used for the physical boards, pin configuration, buses, display drivers, touch drivers, and onboard components, basically...ahh, the hardware. |
| `features/`    | Optional capabilities we wish to use, e.g., Wi-Fi diagnostics, ESPHome's Bluetooth proxy, and similar                                          |
| `legacy/`      | Previous configurations that still need to be separated into packages, this will eventually be removed                                         |

The planned directories include `base/`, `climate/`, `display/`, and `projects/`.

The hardware and optional connectivity packages have been moved into this directory.
The climate core, timer, mould-reduction behaviour and common services are still
combined under `legacy/`.

New configurations will eventually import one supported manifest from `projects/`.
Until those manifests are available and working, the maintained examples compose the
current packages directly.

The root `climate_home_packages/` directory contains compatibility wrappers for my existing
remote installs. These wrappers will remain for at least one published release after the
replacement project manifests are introduced.

Remote packages do not read user secrets. So all Wi-Fi credentials and API encryption remain in the local ESPHome build configuration.
