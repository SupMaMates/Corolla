# Building the corresponding source

Customers install the verified role kit; no compiler, Git or Composer is required
on the runtime host. Builders use a separate Linux amd64 environment. Verify source
assets with the release SHA256SUMS before extraction into fresh directories.
`SOURCE-MANIFEST.json` records the exact Corolla source blobs; no private checkout
or development history is needed.

## Ready-made FFmpeg and exact source

This release reuses BtbN's dated **LGPL linux64 8.1** build from
`autobuild-2026-10-25-13-00`, archive SHA256
`a816e76a32abd1fb75fdef65e6a9ca2efdfebc0ee55ace1c27367a60d1f8658f`.
FFmpeg/ffprobe version: `n8.1.3-24-g92611900bb-20261025`. The exact binaries are
already in both role kits; there is no mutable latest fetch at installation.
If the provider retires its daily download, obtain the same verified bytes from
this release's role kit. The lock pins both executable and notice hashes.

The dependency-source archive contains the matching full FFmpeg source snapshot,
exact BtbN recipe archive, and `SOURCES.json`: repository URLs plus pinned Git
commits/tags or SVN revisions for dependency build inputs. FFmpeg commit is
`92611900bb112123e9bf997fdcc2d78e4c4922fc`; recipe commit is
`937868360a21d711ec94a33f5591d345ad9b7754`. Its scripts retain configuration,
patches, source revisions and upstream notices. Source retrieval requires no
private account or owner request. The source map also retains disabled variants;
those entries are not claims that their GPL/nonfree libraries are linked.

For a source rebuild, follow the included provider README/Docker recipes with
`linux64 lgpl 8.1`, using the pinned FFmpeg commit above in place of the moving
`release/8.1` branch. Keep the recipe's per-library source revisions/patches. Do not
infer a bit-identical third-party rebuild from the version label. These binaries
contain libav. ELF dependencies resolve the Ubuntu C runtime/libgcc; the actual
qualified process also maps Ubuntu's Vulkan loader. Installed package/source records
cover these system libraries. There is no external system libav fallback and no GPU
profile claim. Supported media behavior remains H.264/AAC copy, not every codec
compiled into this general public build.

The historical minimal FFmpeg6.1 builder, signed source and patches are retained
as fallback/provenance material. That custom build is not a prerequisite or the
default dependency for these rc.2 kits, and its exclusion-based proof is not claimed
for the public binary.

## Go and PHP

The shipped PHP/vendor and browser assets are source/deployable files. Exact
production package versions/references/licences are retained in
`xc_vm/src/composer.lock` and `vendor/`; no Composer install is needed.

Use Go1.27.3 from the URL/hash in `ops/install/dependencies.json`. Verify both the
archive and compiler executable. The module uses the Go standard library only:

```sh
cd media
mkdir ../built-bin
export GOTOOLCHAIN=local GOPROXY=off CGO_ENABLED=0 GOMAXPROCS=2
export GOFLAGS=-p=2
for name in corolla-media corolla-file-auth corolla-archive corolla-egress; do
  /verified/go/bin/go build -trimpath -buildvcs=false -o ../built-bin/$name ./cmd/$name
done
```

The dependency archive offers the matching Go source/licences and Valkey8.1.10
source. A uses the official Valkey noble-x86_64 binary archive pinned in the lock;
its upstream Makefile builds source with `make -j2`. Preserve its distinct bundled
notices. Distribution/compiler choices may change locally rebuilt hashes.

## Packaging a local developer build

The unchanged role-assembly/staging rules live in `ops/install/build.py`. For the
FFmpeg input directory, take `bin/ffmpeg`, `bin/ffprobe` and the three files under
`licenses/ffmpeg/` from a verified role payload; put those five files directly into
`/verified/public-ffmpeg`. The builder checks all five hashes from the lock.
It does not compile FFmpeg. Use the official pinned Valkey archive and Go compiler.
Git, bash, PHP CLI, zip, make and ordinary Unix archive tools are builder prerequisites.

The clean export has no historical Git object database. Create an isolated local
commit to use the existing exact-commit recipe; this creates a new developer
artifact identity, not the accepted release identity:

```sh
git init
git add .
git -c user.name='Local builder' -c user.email='builder@localhost' commit -m 'Local corresponding-source build'
python3 ops/install/build.py --repo "$PWD" --source "$(git rev-parse HEAD)" \
  --output /new/role-build --go /verified/go/bin/go \
  --valkey-archive /verified/valkey-8.1.10-noble-x86_64.tar.gz \
  --ffmpeg-build /verified/public-ffmpeg --roles AB
```

Retained `xc_vm/install`/Makefile/lb_configs are included for legacy packaging checks
only. Never execute that inherited installer/updater. The supported customer
entrypoint is the existing verified role kit's `python3 install`.

Ubuntu packages come from authenticated noble/noble-updates/security repositories,
with supported families/minimums and no downgrade. `resolved_packages` is historical
reference, not an exact transitive install constraint. Actual installed versions
for required packages are reported by installer verification; Ubuntu's dpkg database
retains the complete actual transitive inventory (`dpkg-query -W`). Installed packages retain
`/usr/share/doc/<package>/copyright`; matching signed Ubuntu `deb-src` indices and
`apt-get source PACKAGE=SOURCE_VERSION` provide their source. Binary/source package
names and versions can differ. Locally modified/rebuilt outputs are not certified
release artifacts and must not be relabelled as accepted bytes.
