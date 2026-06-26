# Uni-Hierarchy

*Standalone add-on — requires [Uni-Inspector](uni-inspector.md)*

A drop-in companion to your Hierarchy window that tames messy scenes: real **Folders** you can
drag GameObjects into (they vanish from your build automatically) and purely visual **Groups**
that collapse a handful of siblings into one tidy, color-tinted row.

| Feature | What it costs you |
|---|---|
| Folders (nestable, drag-and-drop) | Nothing in your build |
| Groups (collapse selected siblings) | Nothing — purely visual |
| Color tint & custom icon | Nothing — Editor only |
| Visibility / picking toggles | Nothing — Editor only |
| Full native right-click menu | Same options as the built-in Hierarchy, plus more |

## Quick Start

1. Click **+** in the toolbar → **Create Folder**. Drag GameObjects onto it to file them away.
2. Select a few sibling GameObjects, click the **Group** icon to collapse them into one tinted
   block.
3. Click **Open** on a group block to inspect its members in a sub-panel.
4. Alt-click any folder or group row to tint it from a quick palette; right-click for icon and
   rename options.

> **Plays nicely with the built-in Hierarchy** — dock Uni-Hierarchy alongside or in place of
> Unity's own Hierarchy tab — both read and write the very same scene, so everything stays in
> sync.

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
