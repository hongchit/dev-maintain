# Personal Maintenance Scripts

Small zsh maintenance tools for my local macOS development environment.

This repository currently contains:

- `node-maintain` - maintains Node.js versions installed with `nvm`, updates the active LTS release, updates global npm packages, checks deprecated packages, and suggests old Node versions that may be removable.
- `phpbrew-maintain` - maintains PHP versions installed with PHPBrew on Apple Silicon macOS, builds PHP on a temporary RAM disk, installs selected PECL extensions, validates the build, and safely cleans up the RAM disk.

## Requirements

These scripts are written for `zsh` and assume a personal macOS development machine.

`node-maintain` expects:

- `nvm`
- `node`
- `npm`
- `curl`
- A workspace-style project directory, defaulting to `$HOME/workspace`

`phpbrew-maintain` expects:

- Apple Silicon macOS
- Homebrew under `/opt/homebrew`
- `phpbrew`
- macOS tools such as `diskutil`, `hdiutil`, `sysctl`, `uuidgen`, and `/usr/libexec/PlistBuddy`
- Homebrew formulae needed to build PHP and selected extensions

## Usage

Run the scripts directly after reviewing them:

```sh
./node-maintain
```

```sh
./phpbrew-maintain check
./phpbrew-maintain status
./phpbrew-maintain upgrade 8.4
./phpbrew-maintain cleanup-ramdisk
```

## Safety Notes

These are personal maintenance scripts, not a general-purpose package manager.

Before running them on another machine, read the scripts and adjust the defaults for your own environment. In particular:

- `node-maintain` writes logs under `$HOME/workspace/logs/node-maintain`.
- `node-maintain` may install Node versions, set the `nvm` default alias, update global npm packages, and prompt before uninstalling old Node versions.
- `phpbrew-maintain` creates and destroys a temporary RAM disk.
- `phpbrew-maintain` may install Homebrew dependencies, compile PHP, install PECL extensions, switch the default PHPBrew version, and prompt before removing an older PHP patch version.
- Generated logs, temporary files, cache files, and RAM-disk state files should not be committed.

## Disclaimer

Use these scripts at your own risk.

They are provided as examples of my personal maintenance workflow and may not match your system, installed tools, shell configuration, Homebrew layout, PHPBrew setup, npm configuration, or project structure. Review the commands before running them, keep backups of important local work, and do not run them with `sudo` unless you have independently verified that a command requires it.

The scripts perform real system maintenance actions, including package installation, package updates, PHP compilation, default version changes, RAM-disk operations, and optional removal of old runtime versions. The author is not responsible for data loss, broken local environments, failed builds, downtime, or other damage resulting from use or modification of these scripts.

## License

MIT. See [LICENSE](LICENSE).
