# Maintaining this distribution

The authoritative runtime is maintained in the development repository. This customer
home holds docs and immutable versioned release assets, not a second runtime fork.

[The Corolla mindset](COROLLA.md) applies to every change, including tooling and
review. Reuse applicable XC_VM/standard behavior and check the actual customer
journey. Do not accept unnecessary operator steps because internal tests pass;
fix them within the normal delivery process rather than adding another review gate.

For a new release:

1. Select accepted exact source and protected matching A/B kits. Preserve originals.
2. Export the explicit source allowlist with build/patch/lock/licence materials and
   exact dependency sources/notices. Review all tree and asset contents for privacy.
3. Prepare a draft prerelease with pinned install URLs, trusted SHA256SUMS and source/
   role/provenance mapping. Never point a prerelease at `releases/latest`.
4. Download uploaded assets and verify every outer/embedded/member/mode/source hash,
   complete inventories, source completeness and docs/links/examples.
5. Architect reviews the concrete tree/assets, accepts the development delivery,
   and publishes the prerelease. Keep private vulnerability reporting enabled and
   verify anonymous documentation/source/download access afterward. Keep the
   development repository private.

Published tags, runtime assets and checksums are immutable; a runtime/asset correction
gets a separately identified release. Documentation may advance on main after review,
without moving the frozen release tag. Keep the development mirror consistent,
inspect the rendered GitHub pages, and check changed links/commands. Record the
presentation head separately; reuse unchanged release proof for documentation edits.
Checksums are not signatures. Do not manufacture signing identities or attestations.
