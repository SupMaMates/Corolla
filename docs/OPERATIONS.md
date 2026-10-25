# Operations and recovery

Run commands locally as root on standalone A. [First use](FIRST-USE.md) covers
explicit control start, registration/Apply, authority recovery and media Start.
Status never repairs or Starts:

```sh
python3 /opt/corolla/active/ops/install/operations.py status
python3 /opt/corolla/active/ops/install/control.py stop
```

Stop blocks admissions, Stops media/recording, checks all commissioned nodes,
drains at least 50 seconds and verifies zero reservations. Keep five-live/32-account/
two-file/one-recorder and aggregate 2 GiB budgets; ring 8 MiB, HLS 64 MiB/140 inodes,
archive 256 MiB/512 inodes. Bounded private first-error files live in `/var/log/corolla`.
HTTP access/error logs and service stdout/stderr are discarded to avoid secret leakage.
To return after planned Stop, use the kit's one `python3 install recover` intent
(or installed `control.py recover`), then explicitly Start selected media in the
panel. Recovery handles its internal control/authority sequence; a separate control
Start is only needed when you want idle administration without recovery/playback.

## Backup and independent readback

Plan downtime. Capture stops/drains and leaves playback unavailable:

```sh
python3 /opt/corolla/active/ops/install/operations.py capture
```

The result prints capture ID, exact source, private payload/companion locations and
their SHA256 values. Keep this receipt through your authenticated administration
channel. The capture directory is `/var/lib/corolla/backups/m19/<capture-id>`.
The payload contains durable SQL and immutable media; it can contain reversible
business secrets. The separate companion contains installation/encryption/signing
secrets. Protect both, and keep their storage/access separate.

Using an independently verified SSH host key and authenticated SFTP, copy the exact
`payload.tar.gz` to private off-host storage and `companion.json` to separately
protected storage. Do not accept a changed host key automatically. On independent
storage, compute each SHA256 and compare against the trusted capture receipt:

```sh
sha256sum /private/payload.tar.gz
sha256sum /separate-private/companion.json
gzip -t /private/payload.tar.gz
```

These are operator-selected local private paths, not installer paths. Read back the
complete off-host files, not an on-host copy; preserve the source/capture pairing.
Retain originals until replacement readback succeeds. At most two capture sets are
admitted; there is no automatic pruning. Payload and unpacked data each ≤1 GiB,
SQL ≤32 MiB/schema, ≤4096 members. Capture/restore need 4 GiB temporary headroom
plus 8 GiB free/40,000 free inodes; off-host copy needs 4 GiB free too.

For restoration, return only the independently verified off-host pair through
verified SFTP to a **new**, root-owned 0700 `/var/lib/corolla/recovery-input` directory.
Use root-owned 0600 regular files named `payload.tar.gz` and `companion.json`.
If the directory exists, inspect its ownership/content; never overwrite unknown
or prior recovery objects. Do not use the original on-host capture as restore input.

## Same-host restoration

This requires the existing verified installation/identity and matching exact
source/role/schema/encryption binding. Fresh-host DR is unverified. Replace the
uppercase placeholders with authenticated capture receipt values, not values
trusted solely because they appear inside the archive:

```sh
python3 /opt/corolla/active/ops/install/operations.py verify \
  --payload /var/lib/corolla/recovery-input/payload.tar.gz --sha256 PAYLOAD_SHA256 \
  --companion /var/lib/corolla/recovery-input/companion.json --companion-sha256 COMPANION_SHA256 --source SOURCE_SHA
python3 /opt/corolla/active/ops/install/operations.py restore-stage \
  --payload /var/lib/corolla/recovery-input/payload.tar.gz --sha256 PAYLOAD_SHA256 \
  --companion /var/lib/corolla/recovery-input/companion.json --companion-sha256 COMPANION_SHA256 --source SOURCE_SHA
python3 /opt/corolla/active/ops/install/operations.py activate \
  --payload /var/lib/corolla/recovery-input/payload.tar.gz --sha256 PAYLOAD_SHA256 \
  --companion /var/lib/corolla/recovery-input/companion.json --companion-sha256 COMPANION_SHA256 --source SOURCE_SHA
```

Validation precedes target mutation. Stage imports into new isolated main/scratch
databases, verifies durable facts and fences intents. Activation rereads staged
objects, restores bounded archive/movie bytes and configuration, preserving original
SQL/media/image objects. Registration rebuilds with all line modes BLOCKED, policies
disabled and intents STOPPED. No old Valkey/witness/epoch/allocation/PID/HLS/pin or
recorder authority is restored. Normal ten-minute archive retention still applies.

An interrupted MAIN stage can use `resume` with the same arguments only after
inspection; imported main is read back before empty scratch continues. Unknown or
partially importing/activating state remains BLOCKED with a private first error.
Do not drop schemas, blindly repeat imports or roll authority back. Explicitly
repair the recorded stage. Preserve original recovery objects.

After stopped/drained readiness, run `control.py recover`, check status, explicitly
Apply verified registration/publish enabled lines, then Start selected producers.
Enable recording only after healthy live. Check entitled playback, file Range206
and completed past-minute archive. Recovery itself Starts no media.

## Reapply, interruption, update and rollback

Keep the verified kit and original private input. `python3 install` on a ready
same-source/same-input installation verifies without reseeding or changing identity.
For interrupted initial installation inspect the recorded stage/root-only failure.
The wrapper prints explicit engine guidance and refuses automatic recovery.

Engine operations use `ops/install/install.py` from a verified bootstrap or active
installation. Arguments for `install --resume`, `upgrade` and `rollback` are
`--role standalone --input /root/corolla-input.json --bundle VERIFIED_BUNDLE_PATH
--source FULL_SOURCE_SHA --sha256 TRUSTED_INNER_BUNDLE_SHA256`. The kit descriptor
identifies its embedded bundle; verify the kit before extracting it. `preflight`
uses the same arguments and is read-only. `verify` needs no bundle arguments:

```sh
python3 /opt/corolla/active/ops/install/install.py verify
```

The new kit supports actual compatible application-byte updates from M20
`1e2b8eccb061c7d3127d98ad48c78fad56180fcd` to this rc.2 profile. Use the **new kit's**
entrypoint so the old installed VERSION-only guard is not invoked:

```sh
cd /root/corolla-install-20-rc2
python3 install update
python3 install rollback
python3 install status
python3 install recover
```

Update reuses the original private input, prints the source/code/package plan and
requires `UPGRADE`. Rollback asks for the extracted previous verified kit directory
and requires `ROLLBACK`. Keep that kit and the current new kit. Only the retained
previous source can be selected for rollback; the new kit continues to provide the
interface after rollback. The declared profile freezes schema, configuration and
media interfaces; an unknown profile or changed invariant refuses before downtime.
There is no compatibility override switch, database migration or private commissioning
script in this customer path. B release changes remain refused. Maintenance
stops actual serving nodes, blocks/drains ≥50 seconds, checks zero reservations,
captures a private durable pre-change backup, stages/readbacks and switches code.
Rollback requires the retained previous compatible source; current durable edits
and media survive. Neither operation restores old SQL or authority. Keep current,
previous and one staging release; unknown/executing old objects block pruning.
Explicit recovery/Apply/Start remains required after switching a backend incarnation.

**M19A-to-20.0.0-rc.2 remains unsupported.** This is an explicit M20-compatible
code profile, not arbitrary historical compatibility. No customer migration,
cross-product import, arbitrary downgrade or private commissioning-script interface
is offered. There is no erase/reset procedure in this release.
