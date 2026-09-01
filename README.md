# setup-nsis

> Sets up [NSIS](https://nsis.sourceforge.io/) on Linux and macOS.

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
