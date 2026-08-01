# Climate at Home tests

The test layout separates shared device settings from the package paths being tested.

| Directory Name   | Why?                                                                                                  |
| ---------------- | ----------------------------------------------------------------------------------------------------- |
| `common/`        | Shared substitutions, credentials, external dependencies and device overrides                         |
| `local/`         | Project package paths used for current local build development                                        |
| `compatibility/` | Previous root package paths retained for my existing remote installs, this will eventually be removed |
| `remote/`        | Planned clean-cache tests of Git packages                                                             |

Files in `common/` are included by another test entry point and are not validated directly.

Both `local/` and `compatibility/` currently cover:

- Athom with Mitsubishi climate.
- Athom with Mitsubishi climate and Bluetooth proxy.
- Waveshare touch remote with the external modular LVGL interface.

Run ESPHome validation through Docker Compose from the repository root:

```bash
docker compose run --rm --no-deps esphome config projects/climate-at-home/tests/local/athom-mitsubishi.yaml
```

Replace the final path with each entry point under `local/` and `compatibility/` when changing shared packages or package composition.
GitHub Actions compiles the complete supported matrix.

## Output Warnings

The Waveshare configuration currently emits the standard GPIO3 strapping-pin warning and the external LVGL package's deprecation `transparency_key` warning.
