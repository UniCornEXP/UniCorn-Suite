# Uni-Hierarchy

*Standalone add-on — requires [Uni-Inspector](uni-inspector.md)*

A drop-in companion to your Hierarchy window that tames messy scenes: real **Folders** you can
drag GameObjects into (they vanish from your build automatically), purely visual **Pockets**
that collapse a handful of siblings into one tidy, color-tinted row, and **Uni-Groups**, a
separate multi-membership tag system for cross-cutting sets that don't map to one parent's
children.

| Feature | What it costs you |
|---|---|
| Folders (nestable, drag-and-drop) | Nothing in your build |
| Pockets (collapse selected siblings) | Nothing — purely visual |
| Uni-Groups (multi-membership tags) | Nothing — Editor only |
| Color tint & custom icon | Nothing — Editor only |
| Visibility / picking toggles | Nothing — Editor only |
| Full native right-click menu | Same options as the built-in Hierarchy, plus more |

## Folders vs. Pockets — which to use

- **Folders** are real GameObjects. Zero ongoing cost once created, full Undo support, and they
  vanish from your build automatically. Use them for anything large or permanent.
- **Pockets** are a pure visual collapse — no GameObject is created, so they're great for a
  quick, temporary declutter of a handful of siblings. They are *not* recommended for large or
  permanent clusters (hundreds-to-thousands of members): every Pocket has to resolve its members
  each time the tree rebuilds, which adds up and can make the Hierarchy feel sluggish. If a
  cluster is going to stay that big, fold it into a Folder instead.

## Quick Start

1. Click **+** in the toolbar → **Create Folder**. Drag GameObjects onto it to file them away.
2. Select a few sibling GameObjects, click the **Pocket** icon to collapse them into one tinted
   block.
3. Click **Open** on a pocket block to inspect its members in a sub-panel.
4. Alt-click any folder or pocket row to tint it from a quick palette; right-click for icon and
   rename options. Icons are drawn from a built-in emoji set, so there's nothing to license.

> **Plays nicely with the built-in Hierarchy** — dock Uni-Hierarchy alongside or in place of
> Unity's own Hierarchy tab — both read and write the very same scene, so everything stays in
> sync.

## Auto-organizing

- Toolbar **+** → **Auto-Pocket by Name** / **Auto-Folder by Name** scans the whole scene and
  gathers siblings that share a base name (e.g. `Rock_1`, `Rock_2` or `Tree (1)`, `Tree (2)`)
  into one Pocket or one real Folder. Re-running either is safe — it tops up existing
  pockets/folders instead of duplicating them.
- **GameObject** menu → **Uni-Hierarchy** → **Auto-Pocket/Auto-Folder Children by Name** does the
  same thing scoped to just the parents you have selected, so you can include or exclude
  specific parts of the scene instead of scanning everything.
- Prefer Auto-Folder over Auto-Pocket whenever the result is going to be large or permanent (see
  *Folders vs. Pockets* above).

## Cleaning up

- Right-click 2+ selected Pocket blocks for **Merge Pockets** (combines split auto-pockets back
  into one) or **Unpocket** them.
- **GameObject** menu → **Uni-Hierarchy** → **Unpocket All Children** removes every Pocket
  anchored at, or nested under, your current selection in one step — handy for undoing an
  Auto-Pocket run.
- **GameObject** menu → **Uni-Hierarchy** → **Merge Selected Folders** combines 2+ sibling
  Folders into the first one (their contents move in, the emptied folders are deleted). Real
  GameObjects, so this is fully undoable.

## Uni-Groups (Tools → UniCorn Suite → Uni-Groups)

A separate, multi-membership tag system. Unlike a Pocket (one membership at a time,
sibling-scoped only), the same GameObject or asset can belong to any number of groups at once,
and nothing is ever reparented. Use it for cross-cutting sets ("all enemy spawners", "needs VFX
pass") that don't map to one parent's children.

- Select 2+ objects and click **Save as Group** on Uni-Favourite's selection cell, or build a
  group straight from the Uni-Groups browser window.
- Tag groups freely (flat tags, not folders) and filter the browser's group list by tag with
  **Match AND** / **Match OR**.
- **Promote to Folder** turns a group's current members into a real Folder in one click, fully
  undoable, without deleting the group itself.
- The eye-toggle on a group row switches Uni-Hierarchy's main tree into **Flat Group View** —
  just that group's resolved members, with a tinted header and a one-click exit back to normal.

## Right-Click, Visibility & Shortcuts

Right-clicking a row shows the same full GameObject menu you already know from Unity's
Hierarchy — nothing is missing, and Uni-Hierarchy's own folder/group commands are merged right
in. The toolbar's eye and arrow icons toggle visibility and picking, cascading to children.

Keyboard shortcuts (window focused, no text field active):

| Key | Action |
|---|---|
| Delete | Delete selection |
| Ctrl/Cmd+D | Duplicate selection |
| Ctrl/Cmd+X / C / V | Cut / Copy / Paste |
| H | Toggle visibility for selection |
| L | Toggle picking for selection |

---
See also: [Uni-Pinned Components](pinned-components.md) · [Troubleshooting](troubleshooting.md)
