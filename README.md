# PhotoCraft — independent archival snapshots

**Upstream:** [storytold/photocraft](https://github.com/storytold/photocraft) (ArtCraft / Photoshop-style software)

This repository independently preserves the public **Git commit history** of the upstream repository through independently stored [GitHub Release snapshots](../../releases). It is not a GitHub fork and is not affiliated with upstream maintainers.


## 保存先カタログ (ArtCraft × 10)

| 保存先 | 元リポジトリ | 想定される用途 |
| --- | --- | --- |
| [a — PhotoCraft](https://github.com/Rinka-Shiraishi/a/releases) | [storytold/photocraft](https://github.com/storytold/photocraft) | Photoshop系 |
| [b — VectorCraft](https://github.com/Rinka-Shiraishi/b/releases) | [storytold/vectorcraft](https://github.com/storytold/vectorcraft) | Illustrator系 |
| [c — LightCraft](https://github.com/Rinka-Shiraishi/c/releases) | [storytold/lightcraft](https://github.com/storytold/lightcraft) | Lightroom系 |
| [d — FilmCraft](https://github.com/Rinka-Shiraishi/d/releases) | [storytold/filmcraft](https://github.com/storytold/filmcraft) | Premiere Pro系 |
| [e — EffectCraft](https://github.com/Rinka-Shiraishi/e/releases) | [storytold/effectcraft](https://github.com/storytold/effectcraft) | After Effects系 |
| [f — WordCraft](https://github.com/Rinka-Shiraishi/f/releases) | [storytold/wordcraft](https://github.com/storytold/wordcraft) | Word系 |
| [g — GridCraft](https://github.com/Rinka-Shiraishi/g/releases) | [storytold/gridcraft](https://github.com/storytold/gridcraft) | Excel系 |
| [h — DeckCraft](https://github.com/Rinka-Shiraishi/h/releases) | [storytold/deckcraft](https://github.com/storytold/deckcraft) | PowerPoint系 |
| [i — DesignCraft](https://github.com/Rinka-Shiraishi/i/releases) | [storytold/designcraft](https://github.com/storytold/designcraft) | InDesign系 |
| [j — PdfCraft](https://github.com/Rinka-Shiraishi/j/releases) | [storytold/pdfcraft](https://github.com/storytold/pdfcraft) | Acrobat系 |

## How it works

- GitHub Actions checks upstream every day at about **12:17 JST** (03:17 UTC), or when manually triggered.
- If any upstream branch or tag changes, the workflow creates a new `snapshot-<fingerprint>` Release containing `upstream.bundle` and `SNAPSHOT.txt`.
- Every bundle is a complete Git snapshot (all observed Git branches and tags, with original commit IDs). After a successful upstream check, the workflow retains **only the newest 2 snapshots** and automatically deletes older `snapshot-*` Releases **and their tags**. It verifies that both retained Releases contain a nonempty `upstream.bundle` first. Unrelated Releases are never targeted.
- If upstream is unavailable or a new snapshot fails to publish, the run fails safely: previously saved snapshots are **not pruned**. Only successful checks trigger retention.
- No personal token or local GitHub CLI is needed for the automatic process.

## Restore from a snapshot

Download `upstream.bundle` from a snapshot Release, then use:

```bash
git clone upstream.bundle restored-project
```

The default `main` branch contains only these archive instructions and the workflow, **not** the application source. To inspect original source code, restore the bundle.

**Limits:** Git LFS content, GitHub Releases binaries, issues/PRs/discussions and externally hosted files are not included. GitHub storage is not an off-site backup; keep a separate copy for stronger preservation. Check the original license before redistributing or using the code.
