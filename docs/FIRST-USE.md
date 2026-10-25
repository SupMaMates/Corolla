# First use

All host commands run locally as root. For standalone:

```sh
python3 /opt/corolla/active/ops/install/control.py start
python3 /opt/corolla/active/ops/install/operations.py status
```

Open the wrapper's chosen panel origin at `/m1adm/`. Use your private administrator;
there are no default credentials, inherited customers or seeded test channels.
Status separates control readiness from registration, authority, publication,
actual producers and storage. UNKNOWN/BLOCKED requires its indicated repair.

1. Use ordinary supported forms to create a bouquet, package/entitlements as needed,
   subscriber line and a live H.264/AAC MPEG-TS or HLS source. Approve every literal
   IPv4 source address/port, including nested resources and redirects.
2. Open Registration, choose the saved line/channel by name, and confirm **Save and
   Apply** during planned maintenance. No manual ID copying is needed. The confirmed
   action saves and requests Apply together; it interrupts viewers and leaves media
   stopped. Keep line entitlements/bouquets consistent.
3. If authority recovery is required, use the explicit operation below. Wait for
   registration to refresh for this boot; then Apply/publish enabled lines and
   explicitly Start the desired streams in Live Control.
4. Open an entitled M3U/player API link in a supported software client and check
   Managed runtime plus root status. TS and classic live HLS share a producer.

```sh
python3 /opt/corolla/active/ops/install/control.py recover
python3 /opt/corolla/active/ops/install/operations.py status
```

Recover stops callers, blocks/drains at least 50 seconds and creates fresh witnessed
authority. It never starts producers or recording. Old bearer capabilities deny.
After reboot, the control UI can return while playback remains stopped; explicit
recovery, fresh Apply/publication and Start are required. Never delete witness or
Valkey state as a shortcut.

For files, register at most two root-owned immutable MP4 inputs under the approved
media root. Registration publishes a versioned copy. Never overwrite published media.
Entitled file delivery supports byte Range and qualified movie seeking.

For catch-up, enable recording separately on one healthy registered live stream.
Wait for a completed past-minute window, then use the normal entitled timeshift/
catch-up route. Completed archive HLS/turnover was qualified with stock VLC 3.0.20;
FFmpeg ffconcat and archive seeking are unqualified. Recording stays stopped after
source/recovery failure until a fresh explicit request. Normal retention is ten minutes.

For B, explicit control commands expose restricted SSH status/operations and opaque
delivery only; neither command starts a producer:

```sh
python3 /opt/corolla/active/ops/install/media_role.py start-control
python3 /opt/corolla/active/ops/install/media_role.py stop-control
```

Source-matched B component proof is reused; this RC's standalone short run does not
certify a new two-host workload. See [limits](RELEASE.md) and [maintenance](OPERATIONS.md).
