# Install Corolla

[Home](../README.md) · [First login](FIRST-USE.md#first-login) · [Operations](OPERATIONS.md)

## Before you start

Use a clean **Ubuntu 24.04 amd64** server, systemd, synchronized time and a private
root terminal. Reference setup: **2 vCPU, 4 GiB RAM, 8 GiB free disk** and 40,000 free
inodes. This is a prerelease for controlled testing. **HTTP is unencrypted.**
The installer leaves your SSH and firewall policy alone. See [supported limits](RELEASE.md).

## Download and run

In your private root terminal:

```sh
cd /root
curl --fail --location --proto '=https' --output install https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.3/install
python3 install
```

The launcher downloads the matching standalone kit, checks its SHA256, role and
source, then runs the existing installer. No Git, compiler, manual extraction or
copied checksum is needed. Download from the [release](https://github.com/SupMaMates/Corolla/releases/tag/v20.0.0-rc.3)
if you prefer saving the launcher yourself. Python 3 and trusted HTTPS CA certificates
must be available; Ubuntu server installations normally supply these.

Accept the suggested IPv4 address and port 80, or enter your advertised IPv4 and a
free HTTP port. If several addresses exist, choose the one your users can reach.
The administrator name defaults to **admin**. Accept a unique generated password or
choose hidden custom entry. Invalid answers are corrected immediately.

Review the short plan, then type **INSTALL** once to install packages and start
the control UI. Setup ends with your **working login URL and private credentials**.
Sign in there. The panel starts empty: no content, subscriber accounts, playback or
recording is activated. Add sources through the normal panel when you add content.

## Retry or resume

Run the same command again:

```sh
python3 install
```

Your saved configuration, credentials, identity and data are reused. An interrupted
installation asks you to type **RESUME** before continuing its recorded step.
Failures identify the step and retry action. Private details stay in
`/root/.corolla-setup/` and `/var/log/corolla/`; do not share raw diagnostics or
`/root/corolla-input.json`, which contains login credentials. Keep that private file
for maintenance. No reset or directory deletion is needed for an ordinary retry.

Administrator names allow 3–50 ASCII letters, digits or `_.-`; custom passwords need
16–128 UTF8 bytes. Panel addresses use literal IPv4 and HTTP. Ports
16620/18620/18621/18623 are reserved. Occupied ports are refused.
Supported Ubuntu package families/minimums are checked automatically; compatible
patches are retained and installed versions recorded. Missing packages, removals or
downgrades stop safely. The installer does not take over another web/database service.

## Additional media

A second media server uses the same launcher, with an explicit advanced role:

```sh
python3 install --media
```

Use a clean supported host. The matching B kit has **no panel**, SQL, Valkey, witness
or signing private credentials. Supply only A's public Ed25519 operator/forward
keys, capability verification keys and one to five commissioned stream configurations.
Internal node identity and private configuration are generated and retained.
The existing bounded stream JSON uses `stream_id`, `profile_id: copy-ts` and `origins`.
Restricted SSH uses port 18723; no public web listener is created.

See [additional-media control](FIRST-USE.md#additional-media-control) and
[operations](OPERATIONS.md) for lifecycle commands. Both roles use the same release.
