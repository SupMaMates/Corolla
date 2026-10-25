# 20.0.0-rc.1 — LIMITED RC / prerelease

Runtime source: `1e2b8eccb061c7d3127d98ad48c78fad56180fcd`.
Exact role manifests/executable and dependency identities are attached as
[provenance.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.1/provenance.json),
[manifest-A.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.1/manifest-A.json)
and [manifest-B.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.1/manifest-B.json).
The standalone installed `ops/install/VERSION` says `20.0.0-rc.1`; B uses its source
manifest. Retained About `0.1.0-dev` and inherited protocol labels are presentation/
compatibility metadata, not artifact identity or certification.

This freezes accepted installer, business forms/EPG, scoped media/security and
operational behavior. It publishes existing byte-identical kits; no runtime refresh.

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
| Maintenance | Root status/stop, backup/same-host restore, explicit recovery and VERSION-only lifecycle |

Measured short reference only: five local-fixture low-bitrate live channels,
eight TS/eight live HLS clients, two movie/two completed-archive slots and one
recorder over **300.413 seconds**. Input: H.264/AAC 320×180, 15 fps, 574,313 bit/s,
maximum two-second GOP; two movie slots share a synthetic 65-second file.
Twenty allocations initially overlap; each finite slot completes five decoded plays
with archive turnover. A 58.42-second EOF tail is outside the mixed interval.
Peak aggregate memory 1,462,964,224 bytes; CPU median 1.38 cores/p95 1.74/peak 1.94.
Short smaller tiers lasted 120.154 and 120.174 seconds. This is no arbitrary-input,
customer, public-network or larger-capacity promise.

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

Fresh installation starts empty. M19A-to-RC is **not supported by VERSION-only
upgrade** because its lock changes. No migration, automatic activation or production
cutover is implied. [Installation](INSTALL.md), [first use](FIRST-USE.md),
[operations](OPERATIONS.md) and [source/licences](../SOURCE.md) define the usable path.
