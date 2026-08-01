# ESP32 Projects

This repository contains my personal miscellaneous ESP32 or ESPHome projects that may or may not contain unfinished thoughts or ideas that I had.
I try to make sure that configuration and files will compile and validate.

Contributions, pull requests, and improvement suggestions are welcome.

## Projects

### Climate at Home

A local-first ESPHome climate controller and touch-remote project for infrared air conditioners and heat pumps.
This project is built around the ESPHome climate component, with some added automations built into ESPHome without relying on complex Home Assistant Automations.

- [Project Readme](projects/climate-at-home/README.md)
- [YAML Examples](projects/climate-at-home/examples/)

Additional ESP32 projects will be added under `projects/secret-magical-project-name/` with _(hopefully)_ their own documentation, packages, examples, tests,
and maybe if I get my act together architecture thoughts and decisions.
Please note that I generally talk to myself in the comments, so yeah. There is that too.

## Repository structure

- Project tests should be _(if required)_ located within each project under `projects/secret-magical-project-name/tests/`.

## Development

The repository uses a pinned ESPHome image in `compose.yaml` for local testing of ESPHome configuration files and validation. GitHub Actions should use the same version.

Starting the ESPHome dashboard:

```bash
docker compose up -d esphome
```

The dashboard is then available at <http://localhost:6052>.

Validate an ESPHome configuration from the repository root:

```bash
docker compose run --rm --no-deps esphome config projects/climate-at-home/tests/local/athom-mitsubishi.yaml
```

Stop the dashboard:

```bash
docker compose down
```
