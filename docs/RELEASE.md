# 20.0.0-rc.4 — LIMITED RC / prerelease

Runtime source: `252778af3b8c5733ae6347c4f1bb0ce09a0ddad0`.
This release fixes missing panel styling and Forbidden on ordinary browser login.
Existing installations use the normal launcher update; passwords and data are retained.
Exact role manifests/executable and dependency identities are attached as
[provenance.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.4/provenance.json),
[manifest-A.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.4/manifest-A.json)
and [manifest-B.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.4/manifest-B.json).
The standalone installed `ops/install/VERSION` says `20.0.0-rc.4`; B uses its source
manifest. Retained About `0.1.0-dev` and inherited protocol labels are presentation/
compatibility metadata, not artifact identity or certification.

This candidate simplifies installation: automatic verified kit preparation, useful
address/port/admin defaults, generated identity and private configuration, immediate
input correction, explicit resume and control startup ending at a checked login URL.
An empty panel needs no source list; registration Apply approves exact channel source
destinations while media Start stays explicit. Existing data/lifecycle boundaries remain.
The rc.1 and rc.2 releases stay immutable and available separately.

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
Historical rc.2 qualification (including its test accounts and closure below):
shared TS/HLS PASS at 180.208s from one producer, movie
30.153s and completed archive30.190s, with1,506,680,832-byte aggregate owned peak.
That proof uses the preceding rc.2 build; every media/Go/FFmpeg/dependency entry
and media interface is byte-identical. The source-bound M20 update/rollback/update
cycle preserves business/configuration/identity and qualifies the unchanged update
path. The corrected candidate passes normal-kit promotion and separately selects
an older record beyond the96 recent choices, saves two pending registrations without
advancing requested_revision, then publishes them with one confirmed Apply.
Final closure disables/BLOCKS all25 registered test accounts, stops media/recording,
drains51.044s and leaves zero reservations or orphan/deleted executables. These are
focused component checks, not another capacity or endurance campaign.

Those 25 accounts and closure describe rc.2 evidence, not the current M22 server.
M22's clean installation starts with zero subscriber lines. Its focused source
Apply/playback test finished with media/recording stopped and zero allocations.

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

Fresh installation starts empty. The new kit preserves the compatible M20/M21
code-update profile and retained-previous rollback. M19A and arbitrary historical
schema/configuration/interface migrations remain unsupported. No automatic activation or production
cutover is implied. [Installation](INSTALL.md), [first use](FIRST-USE.md),
[operations](OPERATIONS.md) and [source/licences](../SOURCE.md) define the usable path.

The final installer retry correction is covered by isolated root-owned filesystem and
explicit RESUME tests on the native host. Runtime/media proof remains the preceding
M22 candidate with identical media/source/dependency payloads; no fresh reinstall
or repeated media qualification is claimed for this installer-only correction.
