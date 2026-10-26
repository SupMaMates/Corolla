# Install Corolla

[Home](../README.md) · [First login](FIRST-USE.md#first-login) · [Operations](OPERATIONS.md)

Install the standalone panel on a clean server. If you already run Corolla, use the
[update and rollback guide](OPERATIONS.md#reapply-interruption-update-and-rollback).

## Before you start

- **Ubuntu 24.04 amd64**, systemd, cgroup v2 with BPF support, synchronized time and literal IPv4 addresses.
- A private root terminal. Reference host: **2 vCPU, 4 GiB RAM, 8 GiB free disk** and **40,000 free inodes**.
- A controlled test environment: this is a **prerelease**, and HTTP sends credentials and media **unencrypted**.

The installer does not configure TLS, SSH or firewall policy. No Git, Composer or
compiler is required. Corolla's services have a 2 GiB aggregate budget; this is not
a viewer-capacity promise. Read the [supported features and limits](RELEASE.md) first.

## 1. Download and verify

Use the [standalone installer](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/abc06185afa41d9519228b285f93bfaa5b3ce083-A-install.zip)
from the [20.0.0-rc.2 release](https://github.com/SupMaMates/Corolla/releases/tag/v20.0.0-rc.2).
In your private root terminal:

```sh
apt-get update
apt-get install --no-install-recommends python3 curl ca-certificates
umask 077
cd /root
curl --fail --location --proto '=https' --tlsv1.2 --output corolla-A-install.zip \
  https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/abc06185afa41d9519228b285f93bfaa5b3ce083-A-install.zip
printf '%s  %s\n' 0444b603170ccaf767ee804eb2679da21f11e59199865e3b8206adcfb5a9407e corolla-A-install.zip | sha256sum --check
```

**Continue only when the checksum reports `OK`.** Stop if download or verification
fails. Expected hashes are also in [SHA256SUMS](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/SHA256SUMS).
Checksums are not signatures; obtain the expected hash through a separately trusted,
authenticated channel if you doubt the repository/account's integrity.

Extract the verified kit into a **new private directory**, then run its installer:

```sh
mkdir -m 700 /root/corolla-install-20-rc2
python3 -m zipfile -e /root/corolla-A-install.zip /root/corolla-install-20-rc2
cd /root/corolla-install-20-rc2
python3 install
```

## 2. Create your administrator

Choose **Standalone**. The prompts collect your panel's HTTP IPv4 origin, a unique
node ID, administrator name/password and approved media source origins. Password
entry is hidden. Private inputs are saved locally for reuse; do not share that file.

Review the package, port and storage plan. Type **`INSTALL`** when ready. Cancelling
does not install the panel; a newly saved input file remains available for retry.
Installation starts **no control services, playback or recording**. A fresh panel
has one administrator and no subscriber lines or content.

**Next: [start the panel and sign in →](FIRST-USE.md#first-login)**

<details>
<summary>Input rules and package compatibility</summary>

The default private input file is `/root/corolla-input.json`. An existing root-owned
0600 file is validated and reused unchanged; otherwise the prompts save one. Piped
password input and password arguments are refused. Retain this file and the verified kit.

Administrator names use 3–50 ASCII letters, digits or `_.-`. Passwords use 16–128
UTF-8 bytes. Panel origins use HTTP and a literal IPv4 address; custom ports such as
8080 work. Ports 16620/18620/18621/18623 are reserved. Approved source origins have
explicit ports and no paths/credentials. Every nested or redirect destination must
also be approved. Hostnames, IPv6, UDP, metadata/link-local addresses and arbitrary
imports are unsupported.

`apt-get update` refreshes authenticated Ubuntu package metadata. Supported
noble/noble-updates/security package families and minimums are accepted; compatible
newer patches are retained and actual installed versions recorded. Unsupported
families, missing minimums and proposed removals/downgrades stop the plan. Do not
run a full upgrade to bypass a failure. The [dependency record](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/dependencies.json)
contains the minimums and pinned application binaries.

</details>

## Additional media

For a second media server paired with an existing standalone panel, use the
[additional-media installer](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/abc06185afa41d9519228b285f93bfaa5b3ce083-B-install.zip).
It has **no panel** and receives no SQL, Valkey, witness or signing private credentials.
The standalone server must supply public verification material and bounded stream
configuration. Use a clean host meeting the prerequisites above.

<details>
<summary>Install and configure the additional media server</summary>

In a private root terminal on that host:

```sh
apt-get update
apt-get install --no-install-recommends python3 curl ca-certificates
umask 077
cd /root
curl --fail --location --proto '=https' --tlsv1.2 --output corolla-B-install.zip \
  https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/abc06185afa41d9519228b285f93bfaa5b3ce083-B-install.zip
printf '%s  %s\n' 3ab6d2b7898c2aed25df5206c5ebb9424e6a671cafbc225b28f0fdc46c4449aa corolla-B-install.zip | sha256sum --check
```

Continue only after `OK`; then extract into a new private directory:

```sh
mkdir -m 700 /root/corolla-media-install-20-rc2
python3 -m zipfile -e /root/corolla-B-install.zip /root/corolla-media-install-20-rc2
cd /root/corolla-media-install-20-rc2
python3 install
```

Choose **Additional media**. Supply only public Ed25519 operator/forward keys,
capability verification keys, a node ID/origin and one to five sorted stream
configurations. The stream JSON uses `stream_id`, `profile_id: copy-ts` and `origins`.
Pin the independent SSH host public key over your trusted administration channel.
After explicit control start, restricted SSH uses port 18723; there is no public panel
or web listener. General shell access, automatic pairing and arbitrary unit requests deny.

Use [additional-media control commands](FIRST-USE.md#additional-media-control) after installation.

</details>

Both installers belong to the same release; do not mix older kits. See
[operations](OPERATIONS.md) for installed paths, interrupted setup and maintenance.
