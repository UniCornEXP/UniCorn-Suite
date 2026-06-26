# UniCorn Suite

Editor productivity tools for Unity that share one visual language and one launcher button.
Watch and restore Play Mode tweaks, diff GameObjects, preview a dozen assets at once, pin your
most-used components and assets, and tame messy Hierarchies with real folders and groups.

Every window in the suite is 100% Editor-only — nothing ships in your build.

| Product | Tier | Needs Uni-Inspector? | Docs |
|---|---|---|---|
| Uni-Inspector | Free | — | [docs/uni-inspector.md](docs/uni-inspector.md) |
| Uni-Compare Components | Free | ✅ | [docs/compare-components.md](docs/compare-components.md) |
| Uni-Pinned Components | Free | ✅ | [docs/pinned-components.md](docs/pinned-components.md) |
| Uni-Preview | Pro add-on | ✅ | [docs/uni-preview.md](docs/uni-preview.md) |
| Uni-Favourite | Standalone add-on | ✅ | [docs/uni-favourite.md](docs/uni-favourite.md) |
| Uni-Hierarchy | Standalone add-on | ✅ | [docs/uni-hierarchy.md](docs/uni-hierarchy.md) |

This repo is the documentation home for the suite — the package you bought ships with a short
quick-start text file; come here for the full guide, troubleshooting, and themes/settings.

## Installation

- **Requirements:** Unity 2022.2+. Import **Uni-Inspector** first — every other product in the
  suite reuses its theme.
- **Install:** Asset Store / Package Manager → *My Assets* → Download → Import — repeat for each
  add-on you own.
- **Verify:** **Tools → Unicorn Inspector** (or **Window → Unicorn Inspector**) lists every
  installed product. Every component header in the normal Inspector also grows four small icon
  buttons.
- **Suite launcher:** the crown icon in Uni-Inspector's toolbar opens every product you own — and
  shows you what you're missing.

## Quick Start

1. Click **Watch** on a component's header. Enter Play, tweak it, click **Save Now**. Exit Play —
   click any snapshot to restore it (undoable).
2. **Uni-Compare Components:** drag two GameObjects in, click →/← on any amber (differs) or rose
   (missing) row to sync.
3. **Uni-Pinned Components:** drag a component out of the Inspector and drop it into the window to
   pin a permanent shortcut to it.
4. *(Pro)* **Uni-Preview:** drag animated/particle/sprite/mesh GameObjects into the grid, hit Play
   on the Sync bar.
5. **Uni-Favourite:** drag any asset in to favourite it; drag it back out whenever you need it
   again.
6. **Uni-Hierarchy:** create a folder or group selected siblings from the toolbar.

## More

- [Themes & Settings](docs/themes-and-settings.md)
- [Performance](docs/themes-and-settings.md#performance)
- [Troubleshooting](docs/troubleshooting.md)

## Get the Full Suite

Uni-Inspector is the free foundation — every other window in this guide is an add-on that slots
straight in.

- 🎮 Itch.io Shop: https://unicornexpress.itch.io/
- 💬 Discord: https://discord.gg/QjcRyAzEc9

&copy; UniCorn Express. All rights reserved. Unauthorized distribution of any product or tier in
this suite is strictly prohibited.
