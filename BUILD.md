# Building the corresponding source

Runtime compilation is unnecessary for installation. Builders use a separate Linux
amd64 environment. The corresponding-source archive records exact accepted blobs
in `SOURCE-MANIFEST.json`; no private checkout is needed to read/modify/build them.
The dependency-source archive supplies exact external source and retained licences.
Verify both against the release SHA256SUMS before extracting to fresh directories.

The shipped PHP/vendor and browser assets are already source/deployable files.
`xc_vm/src/composer.lock` and production `vendor/` record exact packages, references
and licences; no Composer install is needed. Do not replace them with newer packages.

## Go services

Obtain Go **1.27.3** from the URL/hash in `ops/install/dependencies.json`; verify the
archive and compiler executable against that lock. The module uses only the Go
standard library. In the extracted source, using that compiler:

```sh
cd media
mkdir ../built-bin
export GOTOOLCHAIN=local GOPROXY=off CGO_ENABLED=0 GOMAXPROCS=2
export GOFLAGS=-p=2
for name in corolla-media corolla-file-auth corolla-archive corolla-egress; do
  /verified/go/bin/go build -trimpath -buildvcs=false -o ../built-bin/$name ./cmd/$name
done
```

The published executable identities are in provenance and role manifests. Do not
relabel locally changed binaries as accepted release bytes.

## Application FFmpeg/ffprobe

Use the dependency archive's signed `ffmpeg-6.1.6.tar.xz`, signature and public key;
the lock contains each input hash and signer fingerprint. `build_ffmpeg.py` verifies
them, checks the exact compiler/static-library/binutils hashes, applies the retained
mechanical hvcC count-guard backport without fuzz, enforces the minimal profile and
builds the two executables. The signed release already contains the four CENC guards;
its separate original patch is preserved for provenance, not applied twice.

```sh
python3 ops/install/build_ffmpeg.py --inputs /verified/ffmpeg-inputs --output /new/ffmpeg-build
```

Match Ubuntu 24.04 build inputs: GCC 13 `13.3.0-6ubuntu2~24.04.1`, binutils
`2.42-4ubuntu2.8`, libc6-dev `2.39-0ubuntu8.9`, libssl-dev `3.0.13-0ubuntu3.16`.
Use authenticated Ubuntu package/source metadata, `build-essential`, `pkg-config`,
`libssl-dev`, `gnupg`, `patch`, `python3`, `make` and the locked compiler. Static
libc/libm/libssl/libcrypto inputs are identified individually in the lock; a mismatch
stops the builder rather than claiming reproducibility. The configure flags, epoch,
patches and required/excluded components are in the unchanged build script/lock.
The release ships these generated configs and FFmpeg licence texts in both kits.

For modified/relinked LGPL builds, unpack the supplied FFmpeg source, apply
`ops/install/ffmpeg-patches/CVE-2026-75141-6.1.patch` using `patch -p1`, run configure
with the flags from the lock, then `make -j2 ffmpeg ffprobe`. Substitute your static
libc/TLS libraries as needed; the exact-release hash guards deliberately reject
modified inputs. All relevant source/configuration is offered for rebuilding and
relinking; modified outputs are not qualified release artifacts.

## Valkey and package dependencies

The A kit reuses the official Valkey 8.1.10 noble-x86_64 binary archive, pinned by
URL/archive/executable SHA256 in the lock. Corresponding source, bundled notices and
its upstream build instructions are in the dependency-source archive. Build from
that version with its provided Makefile (`make -j2`); distribution packaging/compiler
choices may change the resulting hash. The official binary is not a Corolla rebuild.

Ubuntu runtime packages are installed from authenticated repositories rather than
redistributed inside the kits. `resolved_packages.A/B` pins their exact versions.
Use Ubuntu's matching signed source indices and `apt-get source PACKAGE=SOURCE_VERSION`
(with noble/noble-updates/noble-security `deb-src` enabled) for package source; binary
and source package names/versions can differ. Each installed package retains its
`/usr/share/doc/<package>/copyright`. Distinct LGPL/BSD/Apache/MIT/GPL terms remain.

## Role packaging records

`ops/install/build.py` is the unchanged accepted package recipe: role allowlists,
production vendor checks, Go flags, official Valkey selection, FFmpeg/hash checks,
regular-file/mode inventories and the existing three-member `python3 install` kit.
It normally selects a Git commit and runs retained legacy `make main`/`make lb`
packaging checks before assembling supported role payloads. The source export has
no historical Git object database or excluded legacy native binaries. To use the
unchanged recipe, make an isolated local source commit and pass its identity. This
creates a new developer artifact identity, not the accepted historical release.
On the Linux builder, from the extracted source root:

```sh
git init
git add .
git -c user.name='Local builder' -c user.email='builder@localhost' commit -m 'Local corresponding-source build'
python3 ops/install/build.py --repo "$PWD" --source "$(git rev-parse HEAD)" \
  --output /new/role-build --go /verified/go/bin/go \
  --valkey-archive /verified/valkey-8.1.10-noble-x86_64.tar.gz \
  --ffmpeg-build /verified/ffmpeg-build --roles AB
```

The builder also needs Git, PHP CLI, bash, zip, make and normal Unix archive tools.
Retained `xc_vm/install` and `lb_configs` are included solely for those legacy
packaging checks; never execute that inherited installer. Supported role payloads
are assembled separately by `build.py`. No bit-identical third-party rebuild or
acceptance of locally rebuilt kits is implied. Use published role manifests for
the accepted payload paths, modes and hashes.

Do not use inherited XC_VM installers/updaters or private extensions. The supported
customer entrypoint remains the verified immutable role kit's `python3 install`.
