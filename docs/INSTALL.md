# Installation

Read [requirements and verified standalone download](../README.md) first. Supported:
Ubuntu 24.04 amd64/systemd/cgroup-v2 BPF, IPv4 and synchronized time. The installer
does not configure TLS, global SSH or firewall policy. HTTP credentials/capabilities/
media are unencrypted. Use a controlled environment appropriate to this limited RC.

Refresh authenticated Ubuntu package metadata with `apt-get update` before starting.
The installer accepts supported package families/minimums from authenticated Ubuntu
noble/noble-updates/security repositories and retains compatible newer installed
patches. It records actual installed versions; historical transitive solver output
is reference information, not an equality requirement. Missing minimums, unsupported
required families and proposed removals/downgrades stop the plan. Do not run a full
upgrade to bypass a failure. The [dependency record](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/dependencies.json)
identifies minimums and pinned downloaded application binaries. Runtime Git, Composer
and compilers are unnecessary.

## Additional media (B)

A standalone installation must already exist and supply its public verification
material and bounded stream configuration. B gets no SQL, Valkey, witness or
signing private credentials. In a private root terminal on a clean supported B host:

```sh
apt-get update
apt-get install --no-install-recommends python3 curl ca-certificates
umask 077
cd /root
curl --fail --location --proto '=https' --tlsv1.2 --output corolla-B-install.zip \
  https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/3150c8ded9bebf07d23b40d60be509f12e0b1b86-B-install.zip
printf '%s  %s\n' b68aede42d588d72e4a798040db5a5b86e2e180497ca744f9ae2963006586cff corolla-B-install.zip | sha256sum --check
mkdir -m 700 /root/corolla-media-install-20-rc2
python3 -m zipfile -e /root/corolla-B-install.zip /root/corolla-media-install-20-rc2
cd /root/corolla-media-install-20-rc2
python3 install
```

Both roles identify runtime source `3150c8ded9bebf07d23b40d60be509f12e0b1b86`.
Do not mix older role kits. B exposes restricted SSH on port 18723 after explicit
control start; it has no public panel/web listener. Pin its independent SSH host
public key over your trusted administration channel before authentication.
General shell access, automatic pairing/discovery and arbitrary unit requests deny.

## Private inputs and confirmation

The interactive wrapper asks for standalone/additional media and a private input
filename (normally `/root/corolla-input.json`). A root-owned 0600 file is validated
and reused unchanged. Otherwise prompts collect and save it privately. Use a private
root terminal; piped input/password arguments/no-echo fallbacks are refused.
Never copy a password-bearing JSON example into a public report.

Standalone prompts collect explicit HTTP IPv4 origin, unique node ID, administrator
name/password and approved media origins. The password is entered twice without echo;
use a unique 16–128 UTF-8-byte password. Administrator names use 3–50 ASCII letters,
digits or `_.-`. Approved media origins have explicit ports, no paths/credentials.
Custom panel HTTP ports such as 8080 work; 16620/18620/18621/18623 are reserved.
Media source destinations must be explicitly approved literal IPv4 address/port pairs.
Hostnames, IPv6, UDP, metadata/link-local, arbitrary imports and unapproved nested/
redirect destinations deny. A starts with one administrator and zero lines/streams/files.

B collects public Ed25519 operator/forward keys, capability verification keys,
node ID/origin and one to five sorted stream configurations. The existing stream JSON
uses `stream_id`, `profile_id: copy-ts`, and `origins`. Supply public material only.

The wrapper verifies the bundle before loading bootstrap, runs read-only preflight,
prints package/port/owned-root plans without secrets, then asks you to type `INSTALL`.
Cancellation applies no installation; a newly saved input file remains private for
retry. Installation stages immutable code at `/opt/corolla/releases/<source>`, promotes
`/opt/corolla/active`, and records owned resources in `/etc/corolla/installation.json`.
Data is under `/var/lib/corolla`, volatile state `/run/corolla`, bounded private
diagnostics `/var/log/corolla`. The wrapper never starts control/media/recording.

Retain the exact kit, trusted hashes and private input. Same-input ready reapply
verifies without reseeding identities. Interrupted/changed installs stop with exact
guidance: inspect the root-only first failure and recorded stage before an explicit
engine `--resume`. Do not drop schemas, mark migrations complete or blindly reseed.
The source archive's unchanged installer and `--help` document advanced engine flags;
the verified kit's descriptor names the source, inner bundle and its SHA256.

Proceed to [first use](FIRST-USE.md). For update/rollback and recovery use
[operations](OPERATIONS.md). The new kit supports the explicitly compatible M20
rc.1-to-rc.2 path; M19A and arbitrary historical/schema migrations remain unsupported.
