# setup-nsis

![License](https://img.shields.io/github/license/nsis-dev/setup-nsis?color=blue&style=for-the-badge)
![Tag](https://img.shields.io/github/v/tag/nsis-dev/setup-nsis?style=for-the-badge)
![CI](https://img.shields.io/github/actions/workflow/status/nsis-dev/setup-nsis/ci.yml?style=for-the-badge)

Set up [NSIS](https://nsis.sourceforge.io/) in your GitHub workflow.

> [!WARNING]
> This action currently only supports Linux and macOS runners.

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
| `large-strings`    | `false`  | Build with `NSIS_MAX_STRLEN=8192`.                            |
| `advanced-logging` | `false`  | Build with `NSIS_CONFIG_LOG=yes`.                             |

## Outputs

| Name      | Description                                               |
| --------- | --------------------------------------------------------- |
| `version` | Resolved NSIS version.                                    |
| `nsisdir` | NSIS installation directory (also exported as `NSISDIR`). |

Builds are cached per OS, version and option combination, so only the first run
pays the compile cost.

## License

[Apache License, Version 2.0](LICENSE)
