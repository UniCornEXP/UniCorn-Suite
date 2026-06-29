# Uni-Inspector (Free)

A faster, friendlier Unity Inspector. Free, forever — every other product in the suite builds on
top of it.

## Component Header Buttons

Icons on every component header:

- **Pop Out** — own floating window
- **Watch** — PlayMode Recorder
- **Save** — Component Clipboard
- **Save Now** — Play Mode only; snapshot this component's current values on the spot, without
  first adding it to the Watch list
- **Pin** — [Uni-Pinned Components](pinned-components.md)
- **Compare** — [Uni-Compare Components](compare-components.md)

## PlayMode Recorder

Watching a component captures a snapshot the instant Play begins and another the instant it
stops, plus manual snapshots on demand (hotkey) or automatically on a timer, configurable in
Settings. Lock a field to exclude it from being recorded. Restoring is always undoable.

## Component Clipboard

Save whole components to a clipboard that survives Editor restarts. Paste onto any GameObject —
adds the component first if missing.

## Selection History

◄/► toolbar buttons — browser-style back/forward across everything you've selected, anywhere in
the Editor.

## Navigation History

A separate, three-lane history — **Folders**, **Items** (other Project assets), and
**Hierarchy** (scene GameObjects) — each its own independent timeline of up to 30 entries, so
jumping around in one lane never bumps anything out of the others. Every visited entry shows up
as a dot with its name underneath; hovering or clicking either the dot or the name jumps you
straight back to it, and the view auto-scrolls to whatever you most recently selected.

- **Full History tab** — its own tab in the main window, scrollable, all 30 entries per lane.
- **Mini History panel** — the same three lanes embedded right above your selection's components
  in the Components tab, so you don't have to leave it to jump back to something. Resize it by
  dragging its bottom edge, collapse it via its foldout, or click the history icon on its header
  to jump straight to the full History tab.

## Component Pop-Out

Opens one component in its own small always-on-top window — useful on a second monitor while the
main Inspector shows something else.

---
See also: [Uni-Compare Components](compare-components.md) · [Uni-Pinned Components](pinned-components.md) · [Themes & Settings](themes-and-settings.md) · [Troubleshooting](troubleshooting.md)
