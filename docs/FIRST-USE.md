# First login and playback

[Home](../README.md) · [Installation](INSTALL.md) · [Operations](OPERATIONS.md)

## First login

In your private root terminal, return to the verified kit directory used during
[installation](INSTALL.md). Start the panel explicitly and check its status:

```sh
cd /root/corolla-install-20-rc2
python3 install start
python3 install status
```

If you extracted the kit elsewhere, use that directory. Open the panel address you
selected during setup, with **`/m1adm/`** at the end, and sign in with the administrator
you created. There are no default credentials. The fresh panel is empty.

Starting the panel does **not** start playback or recording.

## Add your first channel

1. Use the ordinary panel forms to create a bouquet, subscriber line and live
   H.264/AAC MPEG-TS or HLS source. Keep entitlements/packages consistent and approve
   every source IPv4 address/port, including nested resources and redirects.
2. Open **Registration**, choose the saved line/channel by name, and **Save pending**.
   When the batch is ready, confirm **Apply registrations**. For one change, you can
   use the confirmed **Save and Apply** shortcut instead. Apply interrupts viewers
   and leaves media stopped; wait for it to finish before more registration edits.
3. Check status. If it requests recovery, run the explicit recovery command below
   from your verified kit. Wait for registration to refresh for this boot, then
   Apply/publish enabled lines and explicitly **Start** the channel in Live Control.
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
