# pmforms

Form API library for PocketMine-MP plugins

[![CI](https://github.com/AxolotlBucketLabs/pmforms/actions/workflows/ci.yml/badge.svg)](https://github.com/AxolotlBucketLabs/pmforms/actions/workflows/ci.yml)
[![License](https://img.shields.io/github/license/AxolotlBucketLabs/pmforms)](https://github.com/AxolotlBucketLabs/pmforms/blob/master/LICENSE)
[![Discord](https://img.shields.io/discord/1568295845374206052?label=Discord&logo=discord&logoColor=white&color=5865F2)](https://discord.gg/Pk4FrNvHnM)


## Compatibility

- PHP 8.1 or newer
- PocketMine-MP API 5.x
- Axolotl-PM 5.51.1 for development analysis and DevTools integration

## Include in a plugin

Use the repository as a local development virion with DevTools. Put the checkout in `virions/pmforms/` and declare it in the consuming plugin's `devtools.yml`:

```yaml
virions:
  - name: pmforms
    version: ^2.3.1
```

DevTools uses the shared source during development and injects the virion into the consumer PHAR during the build. The production server does not need DevTools installed for the resulting plugin.

## Demo plugin

[`examples/DevToolsConsumer/`](examples/DevToolsConsumer/) is a runnable demo plugin adapted from the upstream [pmforms-demo](https://github.com/dktapps-pm-pl/pmforms-demo). It demonstrates `MenuForm` with a URL image, `ModalForm`, `CustomForm`, form close callbacks, custom form elements, and reading typed values from `CustomFormResponse`.

Run one of these commands in game to open a form:

```text
/form menu
/form modal
/form custom
```

You can also target online players by name, for example `/form custom Steve`. The same example is built and analyzed with DevTools in CI, using the `devtools.yml` beside its `plugin.yml`.

## Develop with DevTools

The root `virion.yml` lets Axolotl-PM [DevTools](https://github.com/AxolotlBucketLabs/DevTools) load this checkout as a shared development virion. Put the repository at `virions/pmforms/`, then declare it in the consuming plugin's `devtools.yml`:

```yaml
virions:
  - name: pmforms
    version: ^2.3.1
```

DevTools uses the shared source during development and shades the library into a standalone plugin PHAR when building. The production plugin does not need DevTools installed. The demo plugin is also the [DevTools consumer example](examples/DevToolsConsumer/), built and analyzed in CI.

## Development checks

```sh
composer install
composer validate --strict
composer analyse
```

PHPStan runs at level `max` against Axolotl-PM 5.51.1.

## Attribution

The original author is `dktapps`. AxolotlBucketLabs maintains this fork for Axolotl-PM API 5.
