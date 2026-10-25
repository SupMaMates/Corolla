# Third-party notices

Project attribution: XC_VM / Vateron-Media and retained contributors; project
licence AGPL-3.0-or-later. The corresponding-source archive preserves `xc_vm/LICENSE`,
`xc_vm/CONTRIBUTORS.md` and the shipped files' notices. Corolla modifications retain
those terms. The source manifest identifies the matching modified release.

| Component | Terms / retained material |
| --- | --- |
| PHP production dependencies | Per-package licences under `xc_vm/src/vendor`; exact versions/source references in `composer.lock` and `vendor/composer/installed.json` |
| Browser JS/CSS/fonts/assets | Retained embedded copyright/licence headers and accompanying files in the exported shipped asset tree; not blanket-relicensed |
| Go runtime/standard library | Go BSD-style licence and PATENTS; Go 1.27.3 source in dependency archive |
| Valkey 8.1.10 | BSD-3-Clause project licence; separately licensed bundled components retain their COPYING/NOTICE files in exact source |
| FFmpeg 6.1.6 profile | LGPL v3-or-later profile (`--enable-version3`, no GPL/nonfree flags); LICENSE.md/COPYING.LGPLv3, source and patches retained |
| Statically linked glibc/libm | LGPL-2.1-or-later plus per-file exceptions/notices; matching Ubuntu glibc source and build instructions for relinking |
| Statically linked OpenSSL | Apache-2.0; matching Ubuntu OpenSSL source, LICENSE and notices |
| Ubuntu installed packages | Independently distributed by Ubuntu, with their own copyright/source packages; exact version lock provided |

FFmpeg is statically linked, including TLS/C libraries. Its licences do not replace
those libraries' terms. Source/build information is in [BUILD.md](BUILD.md).
Original upstream URLs and exact hashes remain in `dependencies.json`; no private
extension licence/activation infrastructure is part of Corolla's supported path.

Production PHP versions: chrisyue/php-m3u8 4.0.3 (MIT), composer/ca-bundle 1.5.13
(MIT), gemorroj/m3u-parser 6.0.1 (LGPL-3.0-or-later), geoip2/geoip2 3.4.0,
maxmind-db/reader 1.13.1 and maxmind/web-service-common 0.11.1 (Apache-2.0),
mobiledetect/mobiledetectlib 4.9.0 and psr/simple-cache 3.0.0 (MIT).

Retained browser notices include Bootstrap 5.3.5/4.5.0, jQuery 3.7.1, ApexCharts
4.2.0, Swiper 11.1.15, jsVectorMap and other MIT components; hls.js 1.4.14 is
BSD-2-Clause and Video.js 8.23.4/vtt.js use Apache-2.0. Font Awesome Free 6.7.2
uses CC-BY-4.0 for icons, SIL OFL-1.1 for fonts and MIT for code; Tabler icons use
MIT. Preserve the embedded per-file headers too. Full supplemental texts are in
[THIRD-PARTY-NOTICES.txt](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.1/THIRD-PARTY-NOTICES.txt),
with exact retrieval URLs/content hashes in
[notice-sources.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.1/notice-sources.json).
