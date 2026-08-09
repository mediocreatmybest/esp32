# ESP32 Projects

This is where I keep my miscellaneous ESP32 and ESPHome projects, including a few
unfinished thoughts and ideas. I still try to keep the configurations compiling and
validating.

Contributions, pull requests, and improvement suggestions are welcome.

## Projects

### Climate at Home

A local-first ESPHome climate controller and touch-remote project for infrared air
conditioners and heat pumps. It uses ESPHome's climate component and a few onboard
automations without relying on complicated Home Assistant automations.

- [Project Readme](projects/climate-at-home/README.md)
- [YAML Examples](projects/climate-at-home/examples/)

More ESP32 projects will eventually turn up under
`projects/secret-magical-project-name/` with _(hopefully)_ their own documentation,
packages, examples, tests, and maybe, if I get my act together, architecture notes.
I generally talk to myself in the comments. So yeah. There is that too.

## Development

Local testing uses the ESPHome version pinned in `compose.yaml`.
GitHub Actions should use the same version.

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
