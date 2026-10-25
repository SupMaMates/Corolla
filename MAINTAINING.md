# Maintaining this distribution

The authoritative runtime is maintained in the development repository. This customer
home holds docs and immutable versioned release assets, not a second runtime fork.

1. Select accepted exact source and protected matching A/B kits. Preserve originals.
2. Export the explicit source allowlist with build/patch/lock/licence materials and
   exact dependency sources/notices. Review all tree and asset contents for privacy.
3. Prepare a draft prerelease with pinned install URLs, trusted SHA256SUMS and source/
   role/provenance mapping. Never point a prerelease at `releases/latest`.
4. Download uploaded assets and verify every outer/embedded/member/mode/source hash,
   complete inventories, source completeness and docs/links/examples.
5. Architect reviews the concrete tree/assets, accepts the development delivery,
   then makes the repository public, enables GitHub private vulnerability reporting,
   verifies the Security reporting link, and publishes the prerelease. The enable
   endpoint returns HTTP404 while the repo is private; retain this as an explicit
   publication prerequisite. Verify anonymous README/install/source/release downloads
   afterward. Keep the development repository private.

Keep public bytes stable; a correction gets a separately identified release.
Checksums are not signatures. Do not manufacture signing identities or attestations.
