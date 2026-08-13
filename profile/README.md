# Tuxery

**Tuxery** is a modern, agnostic App Store for Linux. It aggregates and merges packages from
Flatpak (Flathub), Snap (Snapcraft), AppImage, native (`.deb`, `.rpm`, ...) and other sources
into a single unified search engine — with one card per app, not one per source.

The GitHub organization is currently being bootstrapped. The first repositories establish the
shared foundation before the product repository grows:

| Repository | Role |
| --- | --- |
| [`.github`](https://github.com/tuxery/.github) | Shared GitHub defaults, community files, and org profile |
| [`.dev`](https://github.com/tuxery/.dev) | Shared VS Code workspace, devcontainer, and AI guidance |
| [`app`](https://github.com/tuxery/app) | The product: search UI, matching engine, source connectors |

## Direction

- one unified card per app, deduplicated across Flatpak/Snap/AppImage/native
- a scoring/matching engine (name distance, app IDs, icon filenames) to group duplicates
- a clean, minimalist search-first UI (Qwik)
- eventually, a public API other frontends and distros can build on

## Roadmap

We track work on the [Tuxery GitHub Project](https://github.com/orgs/tuxery/projects/1) instead
of local TODO/ROADMAP files.
