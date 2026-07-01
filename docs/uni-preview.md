# Uni-Preview

*Pro add-on — requires [Uni-Inspector](uni-inspector.md)*

A configurable grid (up to 4×3) of independent preview panes. Drag in any GameObject,
animation clip, texture, or material and each pane figures out what it has: animated character,
particle effect, sprite, UI canvas, static mesh, or flat image. All panes run on instantiated
clones — your actual assets and scene objects are never touched.

Open from **Tools → UniCorn Suite → Uni-Preview**.

## Grid

A **Rows** and **Cols** slider at the top of the window (1–4 rows, 1–3 columns) resizes the
grid at any time. Existing content in surviving cells is preserved; cells that no longer fit
are cleaned up. Two columns side by side is the default starting layout.

## What you can drag in

Drop any of these onto a cell's header row:

| Asset type | How it previews |
|---|---|
| **Animated GameObject** (Animator/Animation controller, or FBX with embedded clips) | Animation pane — plays the clip, shows playback controls |
| **Particle System prefab** | Particle pane — deterministic Simulate scrub |
| **Static mesh / prop FBX** | Model pane — orbit/zoom, no playback |
| **UI prefab** (Canvas, Image, Text, RawImage, …) | Model pane — world-space canvas, front view by default |
| **Texture2D / Sprite** | Flat image — letterboxed to the viewport, no 3D camera |
| **Material** | Sphere — the material rendered on a unit sphere |

Drop a **Component** instead of a GameObject and Uni-Preview uses its owner.

## Per-cell controls

### Cell header

The numbered header bar shows the slot index, the content name, and two buttons:

- **… (content library)** — opens the *Content Library* menu (see [Libraries](#libraries)).
- **X (clear)** — empties the slot.

### Model row *(animation panes only)*

Some FBX packs ship animation clips in a separate file with no character mesh of their own.
The **Model:** row lets you drag a rigged character in as a stand-in. Uni-Preview uses
`AnimationClip.SampleAnimation` directly, so any Humanoid-compatible rig works regardless of
which Animator controller is attached. A **…** button opens the *Model Library* menu.

### Playlist row *(animation panes only)*

A per-cell ordered list of clips that plays through in sequence, advancing automatically when
each clip ends and wrapping back to the start when *Loop* is on.

- Drag one or more **AnimationClip** assets (or a whole GameObject/FBX) onto this row to add
  clips. Dragging a GameObject adds every clip that asset carries.
- Click **+** to browse and pick clips from anywhere in the project.
- Drag any row up or down to reorder.
- Click **−** on a row to remove that clip. Remove every entry to return to the single-clip
  dropdown.
- The currently playing entry is highlighted.

### Transport row *(hidden per-cell when Sync is on)*

- **▶ / ⏸** — play or pause this pane.
- **Loop** — restart from the beginning when the clip ends.
- **Bnc (Bounce)** — reverse direction at each end instead of restarting. Takes priority over
  playlist auto-advance while active.
- **Speed** — 0.1×–2× playback speed slider.
- **Anim / FX** — shown only when the dragged-in object contains *both* an Animator and
  a Particle System. Switches which preview the pane renders.

### View preset row

Six axis-aligned view buttons matching Unity's Scene View gizmo arms:

**F** (Front) · **Bk** (Back) · **L** (Left) · **R** (Right) · **T** (Top) · **Bo** (Bottom)

Clicking one snaps this pane's camera without moving the model.

### Render row

- **3D / 2D** — toggles perspective vs. orthographic projection.
- **Lit / Unlit** — swaps every renderer on the clone to an Unlit shader variant (same texture
  and tint, no lighting term). The original materials are restored when you toggle back.
- **Pivot** *(experimental)* — overlay gizmos: a flat ring on the ground at the root position
  with a forward direction line, and an RGB axis triad at the physics center of mass (or the
  Hips bone for Humanoid rigs when no Rigidbody is present).
- **BG** — shows a skybox and ground plane, matching Unity's built-in Model preview look.
- **Wire** *(shown when BG is on)* — swaps the ground to an unlit tiled grid texture.

### Clip dropdown

When the pane has multiple clips available *and* no playlist is set, a dropdown lets you switch
which clip is playing.

### Time scrub bar

A horizontal slider spans the full clip or effect duration, with a label showing:
- **Animation**: current frame / total frames (e.g. `12/48f`)
- **Particle**: current time / total duration in seconds (e.g. `1.20/3.00s`)

Dragging the slider pauses playback.

### Viewport

- **Left-drag** — orbit.
- **Middle-drag** — pan (the look-at target shifts; pan resets when new content is dropped in).
- **Scroll wheel** — zoom.

### Zoom rail

A narrow column to the right of each viewport:

- **<>** toggle — when on, zooming this pane also zooms every other *unlocked* pane by the
  same relative fraction of their own zoom range.
- **+** / **−** — step zoom in/out.
- **Vertical slider** — continuous zoom drag.
- **L (Lock)** — excludes this pane from zoom broadcasts. Does not prevent this pane's own
  zoom controls from working.

## Sync bar

The main toolbar above the grid applies to every **unlocked** pane at once.

**Sync** toggle:

| Button | Effect |
|---|---|
| **▶ / ⏸** | Play or pause all playable panes together |
| **\|<** | Restart all panes from t=0 |
| **Loop** | Loop all panes |
| **Bnc** | Bounce all panes |
| **Speed** | Set playback speed for all panes |

**View** row — **F / Bk / L / R / T / Bo** buttons snap every unlocked pane to that axis view
at once.

**Model** and **Clip** buttons (right side of the toolbar) open a project-wide picker and apply
the selected model or clip to every cell in one action.

## Libraries

Uni-Preview saves up to 10 entries per library, persisted between Editor sessions.

### Content library (the … button on a cell header)

- **Browse All Clips…** — opens Unity's object picker across every AnimationClip in the
  project, then loads the picked clip into this cell.
- Saved entries are listed below; click one to reload it into the cell.
- **Save Current** — adds the currently loaded clip or effect to the library.
- **Remove / …** — removes a saved entry.

### Model library (the … button on a Model row)

- **Browse All Models…** — opens Unity's object picker across every GameObject in the project.
- Saved models are listed below; click one to assign it as the stand-in for this cell.
- **Save Current Model** / **Remove / …** — same add/remove pattern as the content library.

## Non-destructive previews

Every pane instantiates a private clone of the dragged-in GameObject (or material sphere).
`AnimationClip.SampleAnimation` and `ParticleSystem.Simulate` drive the clone only — your live
scene objects and project assets are never modified.

Additional automatic adaptations on the clone:

- **Optimized GameObjects** (the Humanoid import default) are de-optimized so bone-parented
  accessories follow correctly.
- **Screen Space canvases** are converted to World Space so they render inside the pane's
  off-screen camera.
- **Root motion** is neutralized horizontally (X/Z) every frame, keeping walk/run cycles
  "in-place" the same way an Animator would.

---
See also: [Uni-Favourite](uni-favourite.md) · [Troubleshooting](troubleshooting.md)
