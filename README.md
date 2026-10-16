# PhotoCraft archival mirror

This repository is an **independent, automated Git archive** of [storytold/photocraft](https://github.com/storytold/photocraft) (ArtCraft project). It is not affiliated with the original maintainers.

- **Mirror branches:** [`upstream/main`](../../tree/upstream/main) and any other `upstream/*` branches, copied with their original Git history.
- **Retained history:** immutable `retained/<commit-sha>` tags preserve previously observed branch tips even if upstream later force-pushes or removes branches.
- **Upstream release tags:** copied under `source-tags/*` when available; existing copies are never force-overwritten.
- **Schedule:** GitHub Actions once a day at approximately 12:17 JST, plus manual runs.
- **Source unavailable:** synchronization fails safely; existing archived refs are left untouched.
- **Control branch:** `main` contains this explanation and the scheduled archiver workflow; it is intentionally separate from the mirrored application source.

> **Scope:** Git history (including normal tracked files and commit graph) only. Git LFS objects, GitHub Releases binaries, issues, pull requests, and discussions are not included. This is not an offline backup: a second copy outside GitHub is recommended. Verify the original project's license before using or redistributing its code.

To inspect the project source, switch the branch selector to `upstream/main`.
