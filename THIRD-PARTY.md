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
| Public FFmpeg/ffprobe 8.1 | BtbN LGPL8.1 dated binary, no GPL/nonfree flags; LGPLv3 text, full FFmpeg source and exact build recipes/source revisions retained |
| Public build's linked libraries | Distinct upstream LGPL/BSD/MIT/Apache/zlib and other terms; exact per-library source/revision/build/patch inputs and retained source notices in public SOURCES.json/provider recipes; disabled variants are not claimed linked |
| glibc/libm/libgcc | Ubuntu system runtime libraries, dynamically resolved; their distinct licences/copyright and source packages remain applicable |
| Historical custom FFmpeg fallback | Signed6.1.6 source, LGPLv3 and exact patches/static-library build inputs retained as historical fallback material, not this rc.2 binary's configuration |
| Ubuntu installed packages | Independently distributed by Ubuntu, with their own copyright/source packages; exact version lock provided |

The public FFmpeg binaries contain their libav and codec/TLS dependencies while
resolving system libraries dynamically (C runtime/libgcc; the observed process also
maps Ubuntu's Vulkan loader). Their LGPL text does not replace
linked components' distinct terms. Source/build information is in [BUILD.md](BUILD.md).
The dependency-source archive includes `public-library-notices.tar.gz`: supplemental
copyright/licence texts from 79 exact provider inputs and a URL/revision/hash index.
Provider inputs also include disabled variants; those notices do not imply that
their libraries are linked. Preserve per-file notices in each offered source too.
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
[THIRD-PARTY-NOTICES.txt](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/THIRD-PARTY-NOTICES.txt),
with exact retrieval URLs/content hashes in
[notice-sources.json](https://github.com/SupMaMates/Corolla/releases/download/v20.0.0-rc.2/notice-sources.json).
