# 20.0.0-rc.2 — LIMITED RC / prerelease

Runtime source: `3a04ccbf9af6a840f825a5301123366ea6dc073d`.
Exact role manifests/executable and dependency identities are attached as
[provenance.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/provenance.json),
[manifest-A.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/manifest-A.json)
and [manifest-B.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/manifest-B.json).
The standalone installed `ops/install/VERSION` says `20.0.0-rc.2`; B uses its source
manifest. Retained About `0.1.0-dev` and inherited protocol labels are presentation/
compatibility metadata, not artifact identity or certification.

This candidate adds maintained public FFmpeg/ffprobe reuse, Ubuntu patch-compatible
package planning, a real M20-compatible new-kit update/rollback interface and named,
confirmed Save and Apply registration. It preserves schemas/configuration/media
interfaces and explicit media Start. The preserved rc.1 tag/assets remain distinct;
these rc.2 kits are new exact-source artifacts.

| Surface | Boundary |
| --- | --- |
| Platform | Ubuntu 24.04 amd64, systemd, cgroup-v2 BPF, synchronized clock, literal IPv4 |
| Roles | Standalone panel/local media; restricted additional media |
| Admin | Supported lines/users/groups/packages/bouquets, content metadata, registration/Apply, explicit Start/Stop and runtime/archive views |
| Live | Explicit approved HTTP(S) MPEG-TS/HLS H.264/AAC stream copy; one shared producer/channel |
| Files | At most two immutable movies/episodes, authorized slices and Range/qualified movie seeks |
| Catch-up | One isolated shared recorder, completed past-minute HLS and turnover; VLC 3.0.20 software profile |
| Catalogue | Entitled M3U/player API/XMLTV; one bounded managed EPG source |
| MAG | Retained protocol/software boundary only; installed public device scopes are not generally commissioned |
| Maintenance | New-kit status/update/retained-previous rollback/stop/recovery, backup and same-host restore; explicit compatible profile |

Historical M20 component-qualified reference (its FFmpeg differs): five local-fixture low-bitrate live channels,
eight TS/eight live HLS clients, two movie/two completed-archive slots and one
recorder over **300.413 seconds**. Input: H.264/AAC 320×180, 15 fps, 574,313 bit/s,
maximum two-second GOP; two movie slots share a synthetic 65-second file.
Twenty allocations initially overlap; each finite slot completes five decoded plays
with archive turnover. A 58.42-second EOF tail is outside the mixed interval.
Peak aggregate memory 1,462,964,224 bytes; CPU median 1.38 cores/p95 1.74/peak 1.94.
Short smaller tiers lasted 120.154 and 120.174 seconds. This is no arbitrary-input,
customer, public-network or larger-capacity promise. It is not a new capacity test
of rc.2. The changed dependency requires its separate shared TS/HLS ≥180-second and
movie/completed-archive ≥30-second checks; the release provenance records their result.
Rc.2's affected native checks PASS: shared TS/HLS 180.208s from one producer,
movie 30.153s and completed archive 30.190s; peak aggregate owned memory
1,506,680,832 bytes within 2 GiB. Normal new-kit update → rollback → update preserves
business/configuration/identity. Named confirmed Save and Apply and disabled/stopped
closure pass, including a 51.201s drain and zero reservations. The media and registration proof uses the preceding rc.2 build; its complete
shipped media/Go/PHP entries are byte-identical to this final build, which adds an
installer platform guard and repeats the normal update/rollback cycle. These are focused
component checks, not another capacity or endurance campaign.

**Endurance UNVERIFIED/DEFERRED**; no twelve-hour proof. HTTP is unencrypted,
including credentials, sessions, bearer links and media. Fresh-host disaster recovery,
physical MAG models/firmware/rendering, public TLS and archive seeking remain
unverified. Software/protocol evidence is not device certification. Existing B
component proof is source-matched reuse; this standalone run is no new two-host test.

No automatic failover/transcoding, arbitrary uploads/imports, new reseller/REST/device
scope, activation/private extension, immediate web EPG reload, provider/TMDb imports,
root server actions or generic remote image/metadata fetches are enabled. Inherited
menus and upstream device lists prove no support. Hostnames/IPv6/UDP and unapproved
redirect/nested source destinations deny. Missing GeoIP is unavailable; restricted
unknown decisions deny.

Fresh installation starts empty. The new kit supports the explicit M20 rc.1-to-rc.2
code-update profile and retained-previous rollback. M19A and arbitrary historical
schema/configuration/interface migrations remain unsupported. No automatic activation or production
cutover is implied. [Installation](INSTALL.md), [first use](FIRST-USE.md),
[operations](OPERATIONS.md) and [source/licences](../SOURCE.md) define the usable path.
