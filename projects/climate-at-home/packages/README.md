# Climate at Home packages

This directory contains the ESPHome YAML packages used by Climate at Home.

## Directories

| Directory Name | Why?                                                                                                                                           |
| -------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| `base/`        | Shared device identity, project metadata and the usual ESPHome bits                                                                            |
| `hardware/`    | Used for the physical boards, pin configuration, buses, display drivers, touch drivers, and onboard components, basically...ahh, the hardware. |
| `climate/`     | The climate core, platform profiles, shared state, timer and mould-reduction behaviour                                                         |
| `features/`    | Optional capabilities we wish to use, e.g., Wi-Fi diagnostics, Bluetooth proxy, status indicators, and similar                                 |
| `projects/`    | Supported device compositions, so people do not have to assemble the internal bits themselves                                                  |
| `legacy/`      | Previous configurations that still need to be separated into packages, this will eventually be removed                                         |

The old combined climate configuration stays under `legacy/` for remote compatibility.
`display/` is still planned as that work is split up.

The supported local configurations import one manifest from `projects/`. Maintained
examples still compose packages directly until remote consumer tests are in place.

The root `climate_home_packages/` directory contains compatibility wrappers for my
existing remote installs. They will remain for at least one published release after the
replacement project manifests are introduced.

Remote packages do not read user secrets. Wi-Fi credentials and API encryption remain
in the local ESPHome configuration.
