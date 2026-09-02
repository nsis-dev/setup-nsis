# setup-nsis

![License](https://img.shields.io/github/license/nsis-dev/setup-nsis?color=blue&style=for-the-badge)
![Release](https://img.shields.io/github/v/release/nsis-dev/setup-nsis?style=for-the-badge)
![CI](https://img.shields.io/github/actions/workflow/status/nsis-dev/setup-nsis/ci.yml?style=for-the-badge)

Set up [NSIS](https://nsis.sourceforge.io/) in your GitHub workflow.

## Usage

```yaml
- uses: nsis-dev/setup-nsis@v1
- run: makensis installer.nsi
```

With build options:

```yaml
- uses: nsis-dev/setup-nsis@v1
  with:
    version: "latest"
    large-strings: false
    advanced-logging: false
```

## Inputs

| Name               | Default  | Description                                                   |
| ------------------ | -------- | ------------------------------------------------------------- |
| `version`          | `latest` | NSIS version, e.g. `3.12`. `latest` resolves via SourceForge. |
| `large-strings`    | `false`  | `NSIS_MAX_STRLEN=8192`.                                       |
| `advanced-logging` | `false`  | `NSIS_CONFIG_LOG=yes`.                                        |

> [!NOTE]
> On Windows, `large-strings` and `advanced-logging` cannot be combined: the
> action uses upstream's prebuilt special builds and there is no build that
> ships both. Enabling both fails the step.

## Outputs

| Name      | Description                                               |
| --------- | --------------------------------------------------------- |
| `version` | Resolved NSIS version.                                    |
| `nsisdir` | NSIS installation directory (also exported as `NSISDIR`). |

On Linux and macOS, NSIS is built from source; on Windows the action installs
upstream's prebuilt binaries. Either way the result is cached per OS, version
and option combination, so only the first run pays the setup cost.

## License

[Apache License, Version 2.0](LICENSE)
