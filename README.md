<img src="assets/corolla.svg" width="64" alt="Corolla">

# Corolla

Corolla is a self-hosted IPTV panel derived from XC_VM. PHP manages accounts and
entitlements, FFmpeg produces media, Go supervises bounded playback, and Nginx
serves bytes. SQL holds durable facts; Valkey holds temporary playback state.

**20.0.0-rc.2 is a LIMITED RC / prerelease. Endurance is UNVERIFIED/DEFERRED.**
HTTP sends credentials and media unencrypted. This release is not production-certified.
Read the [release notes and limits](docs/RELEASE.md) before installation.

## Requirements

Clean Ubuntu 24.04 amd64, systemd, cgroup v2 with BPF support, synchronized clock,
literal IPv4 addresses, and a private root terminal. Reference host: two vCPU,
4 GiB physical RAM, at least 8 GiB free disk and 40,000 free inodes. Corolla's
owned services have a 2 GiB aggregate budget. This is not a viewer-capacity promise.

Choose **A / standalone** for the panel and local media. **B / additional media**
is a restricted media role paired explicitly with an existing A; it has no panel
or business credentials. Use the matching kit for the selected role.

## Download and install

Use the [version-pinned prerelease](https://github.com/SupMaMates/Corolla/releases/tag/v20.0.0-rc.2).
The short standalone path, in a private root terminal on a clean supported host:

```sh
apt-get update
apt-get install --no-install-recommends python3 curl ca-certificates
umask 077
cd /root
curl --fail --location --proto '=https' --tlsv1.2 --output corolla-A-install.zip \
  https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/3a04ccbf9af6a840f825a5301123366ea6dc073d-A-install.zip
printf '%s  %s\n' d2462c04876378adf2ec9546d5371ede276ace608f6b0bc37f137c7f5c42856a corolla-A-install.zip | sha256sum --check
mkdir -m 700 /root/corolla-install-20-rc2
python3 -m zipfile -e /root/corolla-A-install.zip /root/corolla-install-20-rc2
cd /root/corolla-install-20-rc2
python3 install
```

Stop if verification fails. Extract only after a successful checksum check, into a
new private directory. These hashes are not signatures: obtain the expected hash
through a separately trusted authenticated channel if repository/account integrity
is in doubt. Never run a downloaded shell pipeline. No Git, Composer or compiler
is needed on the customer host. [Full installation and B instructions](docs/INSTALL.md)
cover private inputs, package availability, preflight and the `INSTALL` confirmation.

## First use and service management

Installation starts no services or media. The wrapper prints your chosen panel URL.
To expose standalone control, run locally as root:

```sh
python3 /opt/corolla/active/ops/install/control.py start
python3 /opt/corolla/active/ops/install/operations.py status
```

Open your selected origin at `/m1adm/` and log in using the administrator you created.
A fresh panel is empty. Follow [first use](docs/FIRST-USE.md) to create content and
lines, register/Apply, explicitly recover authority when required and Start playback.
Control READY alone does not mean playback is ready.

For planned maintenance:

```sh
python3 /opt/corolla/active/ops/install/control.py stop
```

Stop blocks admissions, stops media/recording, drains at least 50 seconds and checks
zero reservations. [Operations and recovery](docs/OPERATIONS.md) cover status,
backup/readback/restore, reboot recovery and the exact update/rollback limits.

The verified extracted kit also provides a short root interface:

```sh
python3 install status
python3 install update
python3 install rollback
python3 install recover
python3 install stop
```

Run update/rollback from the verified **new** kit. Review its plan and confirm
planned downtime; rollback asks for the retained previous verified kit directory.
One recovery intent handles internal sequencing. Media Start remains explicit.

## Features and help

Supported admin account/catalogue forms, shared live TS/classic HLS producers,
two immutable movie slots, one recorder and completed past-minute catch-up,
entitled M3U/player API/XMLTV and bounded EPG. Software-client scope and
[exclusions](docs/RELEASE.md) apply; inherited menus are not support claims.

Report reproducible problems in [Issues](https://github.com/SupMaMates/Corolla/issues)
with redacted version, platform and error details. Never upload credentials, bearer
links, private input/recovery bundles or full databases. See [security](SECURITY.md)
for sensitive reporting and [licences/source](SOURCE.md) for the complete source offer.

Corolla retains XC_VM attribution and AGPL-3.0-or-later terms. Individual dependencies
retain their distinct licences. This repository contains customer documentation and
release metadata; the matching runtime source is the **corresponding-source release
asset**, not GitHub's automatic documentation-only source ZIP.
