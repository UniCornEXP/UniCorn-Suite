# Uni-Inspector (Free)

A faster, friendlier Unity Inspector. Free, forever — every other product in the suite builds on
top of it.

**Non-invasive.** Uni-Inspector is its own dock window — it doesn't replace Unity's native
Inspector. Both can be open side-by-side. The only thing it adds to the native Inspector is a row
of small icon buttons on each component header.

## Components Tab

The Components tab is a full alternative view of the selected GameObject's components. It
complements Unity's native Inspector rather than replacing it: use whichever feels right for the
current task.

### Collapsed tiles vs. expanded cards

Components start collapsed as icon tiles — a compact grid you can scan at a glance. Click a tile
to expand it into a full card that draws the same foldout inspector Unity's own Inspector shows
(custom `[CustomEditor]` drawers, Odin, NaughtyAttributes, and other third-party inspector
frameworks all work exactly as they do in Unity's window).

### Enable/disable toggle

Every enableable component — `MonoBehaviour`, `Renderer`, `Collider`, `Cloth`, `LODGroup`, and
more — shows a checkbox in both views:

- **Collapsed tile** — small checkbox in the bottom-left corner of the tile. Toggles the
  component without expanding it.
- **Expanded card header** — left-aligned checkbox next to the component icon and name.

Toggling either writes through `SerializedObject`, so the change is fully undoable and appears
in Unity's native Inspector immediately.

### Add Component

The **+ Add Component** button at the bottom of the list opens a searchable dropdown
(`AdvancedDropdown`) with a search field auto-focused on open. Components are grouped by
namespace and `[AddComponentMenu]` path, matching the category layout of Unity's native dropdown.
The last-typed search query persists across different GameObjects within the session (resets on
domain reload), identical to native behavior.

### Material preview

When a `MeshRenderer` or `MeshFilter` component is expanded, a preview panel appears below the
component list showing the material applied to the mesh. Controls on the preview header:

- **Shape button** — cycles through five built-in preview shapes (sphere, cube, torus, capsule,
  plane). Click to advance. Drag any **Mesh** asset or any **GameObject** that has a MeshFilter
  onto the preview area to preview an arbitrary mesh instead; click the shape button again to
  return to built-in shapes.
- **▶ / ⏸ button** — starts or pauses auto-rotation (40°/sec).
- **Soft / Hi / Drm / Rim** — four light presets (balanced, high-intensity, dramatic one-sided,
  and rim-lit).
- Drag inside the preview to orbit; scroll to zoom.

## Component Header Buttons (native Inspector)

These four icon buttons are appended to every component's header in Unity's **native** Inspector
— they work whether you have the Components tab open or not:

- **Pop Out** — opens that component in its own small floating window.
- **Watch** — adds it to the PlayMode Recorder tab.
- **Save** — adds it (with current values) to the Component Clipboard tab.
- **Save Now** *(Play Mode only)* — snapshots the component's current values on the spot, without
  needing it to be on the Watch list first.
- **Pin** — [Uni-Pinned Components](pinned-components.md) *(requires Uni-Pinned Components add-on)*.
- **Compare** — adds this GameObject to [Uni-Compare Components](compare-components.md).

## PlayMode Recorder

The native Inspector discards every in-Play change the instant you exit Play Mode — there is no
built-in save. The Recorder solves this:

1. Click **Watch** on a component. It auto-captures a **Start** snapshot when Play begins and an
   **End** snapshot when it stops.
2. Click **Save Now** (header button or global hotkey) at any point during Play to save a **Manual**
   snapshot (up to five, ring-buffered).
3. Turn on **Auto-Save** in Settings to snapshot on a timer automatically.
4. After Play stops, click any snapshot row to **restore** those exact values — fully undoable.
5. **Lock** individual fields to exclude them from both recording and restore.

## Component Clipboard

Save whole components (with all serialized values) to a named clipboard that persists across
Editor restarts. Paste onto any GameObject — adds the component type first if it's missing. Paste
is fully undoable.

## Selection History

◄/► toolbar buttons — browser-style back/forward across everything you've selected, anywhere in
the Editor.

## Navigation History

A three-lane history — **Folders**, **Items** (other Project assets), and **Hierarchy** (scene
GameObjects) — each lane independently tracks up to 30 entries. Jumping in one lane never
displaces entries in the others.

- **Full History tab** — all 30 entries per lane, scrollable.
- **Mini History panel** — the same three lanes embedded above the component list in the
  Components tab, resizable by dragging its bottom edge. Jump straight to anything without
  switching tabs.

## Component Pop-Out

Opens one component in its own small, always-on-top window — useful on a second monitor while
the main Inspector shows something else.

## Third-party compatibility

The Components tab uses `Editor.DrawFoldoutInspector` (public Unity API) to draw each expanded
card, so custom drawers from **Odin Inspector**, **NaughtyAttributes**, **Tri-Inspector**, and
similar frameworks are fully respected. No monkey-patching, no reflection into Unity internals.

## Requirements

Unity 2022.2+ (uses `SerializedProperty.boxedValue`). Editor-only — nothing ships in your build.

---
See also: [Uni-Compare Components](compare-components.md) · [Uni-Pinned Components](pinned-components.md) · [Themes & Settings](themes-and-settings.md) · [Troubleshooting](troubleshooting.md)
