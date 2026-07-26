# Climate at Home tests

The test layout separates shared device settings from the package paths being tested.

| Directory Name   | Why?                                                                                                  |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| `common/`        | Shared substitutions, credentials, external dependencies and device overrides                         |
| `local/`         | Project package paths used for current local build development                                        |
| `compatibility/` | Previous root package paths retained for my existing remote installs, this will eventually be removed |
| `remote/`        | Planned clean-cache tests of Git packages                                                             |

Files in `common/` are included by another test entry point and are not validated
directly.

Both `local/` and `compatibility/` currently cover:

- Athom with Mitsubishi climate.
- Athom with Mitsubishi climate and Bluetooth proxy.
- Waveshare touch remote with the external modular LVGL interface.

Run ESPHome validation through Docker from the repository root. For example:

```powershell
docker run --rm --mount "type=bind,source=C:\Extras\git\esp32,target=/config" esphome/esphome:latest config projects/climate-at-home/tests/local/athom-mitsubishi.yaml
```

The Waveshare configuration currently emits the documented GPIO3 strapping-pin warning
and the external LVGL package's legacy `transparency_key` redaction warning.
