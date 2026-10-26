# Licences and corresponding source

Corolla is derived from [Vateron-Media/XC_VM](https://github.com/Vateron-Media/XC_VM).
Retained project terms are **AGPL-3.0-or-later**; see [LICENSE](LICENSE) and the
retained notices in the source. Preserve attribution and offer matching source to
recipients/network users as required by the applicable licences. Dependencies keep
their own terms, listed in [THIRD-PARTY.md](THIRD-PARTY.md); they are not relicensed AGPL.

The original XC_VM pin is `ef88d7e32524afee63271f27027764b7f087ad3d`.
Selective later alignment compared `3470255f95ffb39668d3f26d520c224d1d73d6db`.
Corolla changes include media/authority boundaries, supported installer/recovery,
bounded services, ingress/egress and selected compatible upstream form/EPG fixes.
Neither upstream private activation/extensions nor its runtime ownership is adopted.

Download matching accepted runtime **`abc06185afa41d9519228b285f93bfaa5b3ce083`**:

- [Corresponding runtime/build source](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/Corolla-20.0.0-rc.2-corresponding-source.tar.gz)
- [Dependency source/notices archive](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/Corolla-20.0.0-rc.2-dependency-source.tar.gz)
- [SHA256SUMS](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/SHA256SUMS)
- [Build instructions](BUILD.md)

The explicit source inventory includes shipped PHP/vendor/assets, Go source,
installer/build scripts, locks and FFmpeg patches. It excludes private Git history,
captures, credentials, access records and owner evidence. Source is available
directly without private-development-repository access or asking the owner.
The customer repository intentionally holds documentation/release metadata with
independent history. GitHub's automatic **Source code (zip/tar.gz)** for this repo
contains those docs; obtain the named corresponding-source assets above for runtime.
