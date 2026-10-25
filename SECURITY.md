# Security reporting

HTTP in this limited RC is unencrypted. See [release limits](docs/RELEASE.md).
Keep administrator/line secrets, bearer/source URLs, input files, databases,
recovery payloads/companions and private first-error diagnostics out of public issues.

Never post vulnerability details or secrets in public issues. For a sensitive report,
use this repository's GitHub **Security → Report a vulnerability**
[private reporting channel](https://github.com/SupMaMates/Corolla/security/advisories/new).
Report affected release/source, platform, minimal redacted reproduction and impact.
Provide no live credentials or customer data. No response-time/support SLA is promised.

Private preparation note: this channel becomes available after the repository is
made public and private vulnerability reporting is enabled. The release publisher
must enable and verify it before publishing this prerelease; it is not yet enabled
in the private draft.

For ordinary issues use [Issues](https://github.com/SupMaMates/Corolla/issues), with
redacted version, platform, operation and error code. Do not upload full diagnostics
or databases. Rotate any secret accidentally exposed before discussing it further.
