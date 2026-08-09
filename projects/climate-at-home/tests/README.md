# Climate at Home tests

The test layout separates shared device settings from the package paths being tested.

| Directory Name   | Why?                                                                                                  |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| `common/`        | Shared substitutions, credentials, external dependencies and device overrides                         |
| `local/`         | Supported project manifests used for current local build development                                  |
| `compatibility/` | Previous root package paths retained for my existing remote installs, this will eventually be removed |
| `remote/`        | Planned clean-cache tests of Git packages                                                             |

Files in `common/` are included by another test entry point and are not validated directly.

Both `local/` and `compatibility/` cover:

- Athom with Mitsubishi climate.
- Athom with Mitsubishi climate and Bluetooth proxy.
- Waveshare touch remote with the external modular LVGL interface.

`local/` also validates Athom's climate core with physical and no-op status indicators,
plus the timer and mould-reduction packages on their own.

Run ESPHome validation through Docker Compose from the repository root:

```bash
docker compose run --rm --no-deps esphome config projects/climate-at-home/tests/local/athom-mitsubishi.yaml
```

When changing shared packages or package composition, repeat that command for each entry
point under `local/` and `compatibility/`. GitHub Actions compiles the complete supported
matrix.

## Known warnings

The Waveshare configuration currently emits the standard GPIO3 strapping-pin warning
and the external LVGL package's deprecated `transparency_key` warning.
