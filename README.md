# Nodeau release distribution

This repository is a **generated serving copy** of Nodeau's public releases. Nothing
in it is written by hand, and nothing in it decides what is released.

- **Install Nodeau** with `curl -fsSL https://get.nodeau.ai/install.sh | bash`. That
  is the only supported entry point; you never need a URL from this repository.
- **Releases** here hold each version's archives and their `SHA256SUMS` as immutable
  release assets. A version appearing here is downloadable, not released.
- **`channel/`** holds the channel pointers that get.nodeau.ai serves at
  `https://get.nodeau.ai/channel/<name>.json`. A version is released when the `beta`
  channel names it, and only then.
- **`SHA256SUMS`** lists every other file of this tree, so any copy of it can be
  checked against one commit of this repository.

## What every installer checks

`install.sh` reads the channel, downloads the archive it names and refuses to install
unless the archive's SHA-256 equals the one the channel declares. A pinned install
(`--version vX`) checks the version's own `SHA256SUMS`. A fleet upgrade additionally
requires the digest the rollout was authorised with.

To check by hand:

```bash
curl -fsSL https://get.nodeau.ai/channel/beta.json      # version, commit, sha256 per archive
curl -fsSL -o nodeau.tar.gz https://get.nodeau.ai/releases/<version>/nodeau-linux-amd64.tar.gz
sha256sum nodeau.tar.gz                                   # must equal the channel's sha256
```

## Channels at this commit

| channel | version | commit |
|---|---|---|
| `alpha` | v0.1.0-alpha.5 | `0ab991efde02` |
| `beta` | v0.19.0-beta.11 | `d13b1d4b565f` |

Security reports: see https://get.nodeau.ai/SECURITY.md.
