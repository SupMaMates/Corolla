# First login and playback

[Home](../README.md) · [Installation](INSTALL.md) · [Operations](OPERATIONS.md)

## First login

The installer prepares and starts your empty panel, then prints your login URL,
administrator name and generated password in the private terminal. Open that URL
and sign in. The default name is **admin**; every generated password is unique.

Credentials are retained in root-only `/root/corolla-input.json`. Installation
never starts playback or recording.

## Add your first channel

1. Use the ordinary panel forms to create a bouquet, subscriber line and live
   H.264/AAC MPEG-TS or HLS source. Keep entitlements/packages consistent and approve
   the saved channel source when applying its registration. Sources require literal IPv4;
   hostnames, link-local/metadata addresses and wildcard destinations are refused.
2. Open **Registration**, choose the saved line/channel by name, and **Save pending**.
   When the batch is ready, confirm **Apply registrations**. For one change, you can
   use the confirmed **Save and Apply** shortcut instead. Apply approves the selected channels' exact source destinations (up to four origins),
   interrupts viewers and leaves media stopped; wait for it to finish before more registration edits.
3. After Apply finishes, explicitly **Start** the channel in Live Control. The
   installer has already prepared the initial empty panel. After a later reboot or
   indicated authority failure, use the recovery command below, then Apply and Start.
4. Open an entitled M3U/player API link in a supported software client. Check
   Managed runtime and root status; live TS and classic HLS share one producer.

```sh
python3 install recover
python3 install status
```

An older record missing from the recent choices can be found by **exact name or
ID**. Up to 24 matches are added; use the ID to distinguish duplicate names.

Recovery stops callers, blocks/drains at least 50 seconds and creates fresh playback
authority. It never starts media. After reboot, the panel can return while playback
stays stopped; use the indicated recovery, fresh Apply/publication and explicit Start.
See [operations and recovery](OPERATIONS.md) for status, maintenance and repair.

## Movies and catch-up

For movies/episodes, register at most two root-owned immutable MP4 inputs under the
approved media root. Registration publishes a versioned copy; never overwrite it.
Entitled delivery supports byte Range and qualified movie seeking.

For catch-up, enable recording separately on one healthy registered live channel.
Wait for a completed past-minute window, then use the normal entitled timeshift/
catch-up route. Retention is ten minutes. Completed archive HLS/turnover was checked
with VLC 3.0.20; archive seeking and FFmpeg ffconcat remain unqualified. Recording
stays stopped after source/recovery failure until a fresh explicit request.

[Supported limits](RELEASE.md) · [Backup and maintenance](OPERATIONS.md)

## Additional-media control

The additional media server has no administrator panel. Run its control commands
locally as root; neither command starts a producer:

```sh
python3 /opt/corolla/active/ops/install/media_role.py start-control
python3 /opt/corolla/active/ops/install/media_role.py stop-control
```

The release's standalone checks do not certify a new two-host workload; see the
[release notes](RELEASE.md) for the source-matched additional-media scope.
