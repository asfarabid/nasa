# Transform Controls Quick Reference

## Keyboard Shortcuts

| Key           | Action   | Description                        |
| ------------- | -------- | ---------------------------------- |
| **G**         | Move     | Switch to translate/move mode      |
| **R**         | Rotate   | Switch to rotation mode            |
| **S**         | Scale    | Switch to scale mode               |
| **Delete**    | Delete   | Remove selected zone               |
| **Backspace** | Delete   | Remove selected zone (alternative) |
| **Escape**    | Deselect | Clear zone selection               |

## Toolbar Buttons

```
┌─────────────────┐
│   TRANSFORM     │  ← Fixed Right Side
├─────────────────┤
│   ↔️  (Move)    │  ← Translate mode (G)
├─────────────────┤
│   🔄  (Rotate)  │  ← Rotation mode (R)
├─────────────────┤
│   ⚏  (Scale)   │  ← Scale mode (S)
├─────────────────┤
│   🗑️  (Delete)  │  ← Delete zone (Del)
└─────────────────┘
```

## Transform Modes

### Move Mode (G)

- **Gizmo**: 3 colored arrows (X/Y/Z axes)
- **Usage**: Drag arrow to move along that axis
- **Constraints**: Stays within container bounds
- **Collision**: Prevents overlap with other zones

### Rotate Mode (R)

- **Gizmo**: 3 colored circles (X/Y/Z rotation)
- **Usage**: Drag circle to rotate around that axis
- **Constraints**: None (zones can rotate freely)
- **Collision**: Checked after rotation

### Scale Mode (S)

- **Gizmo**: 3 colored boxes on axes + center box
- **Usage**:
  - Drag axis box: Scale along that dimension
  - Drag center: Uniform scale
- **Constraints**: Minimum size enforced
- **Collision**: Prevents scaling into other zones

## Workflow Examples

### Placing a New Zone

```
1. Drag zone from palette (left side)
   └─> Zone library with search/filter

2. Drop into viewport
   └─> Zone appears at drop location

3. Zone auto-adapts to container
   └─> Size/shape adjusts to fit

4. Collision resolution
   └─> Moves if overlapping others
```

### Moving an Existing Zone

```
1. Click zone to select
   └─> Highlights + shows gizmo

2. Press G or click Move button
   └─> Translate gizmo appears

3. Drag arrow to move
   └─> Real-time constraint check

4. Release to finalize
   └─> Applies final position
```

### Rotating a Zone

```
1. Select zone
2. Press R or click Rotate button
3. Drag rotation circle
4. Zone rotates around selected axis
```

### Scaling a Zone

```
1. Select zone
2. Press S or click Scale button
3. Drag scale handle
4. Zone resizes (maintains minimum)
```

## Visual Feedback

### Zone States

**Unselected**:

- Normal opacity (0.3 default)
- Low emissive (0.2 intensity)
- Colored edges matching zone type

**Selected**:

- Increased opacity (+0.1)
- High emissive (0.5 intensity)
- Transform gizmo visible
- Toolbar enabled

**Dragging**:

- OrbitControls disabled
- Real-time position update
- Container constraints active

**Colliding** (prevented):

- Transform blocked
- Stays at previous valid position
- No visual warning (limitation)

## Container Adaptation

### Cylindrical Containers

```
Zone enters cylinder:
  ├─ Calculate distance from center axis
  ├─ Determine available radius
  ├─ Scale width/depth to fit
  └─ Maintain height
```

### Box Containers

```
Zone enters box:
  ├─ Get container dimensions
  ├─ Calculate scale factors
  ├─ Proportional resize
  └─ Center within bounds
```

## Collision System

### Detection

- Uses AABB (Axis-Aligned Bounding Boxes)
- Checks overlap on all 3 axes
- Computed in world space

### Resolution

- Prevents transform if collision detected
- Maintains previous valid state
- No automatic push-away (manual adjustment needed)

## Tips & Tricks

### Precise Movement

1. Zoom in close to zone
2. Use Move mode (G)
3. Drag slowly for fine control

### Constrained Rotation

1. Use Rotate mode (R)
2. Drag one axis circle at a time
3. Hold shift for snapping (if enabled)

### Uniform Scaling

1. Use Scale mode (S)
2. Drag center box (not axis boxes)
3. Maintains proportions

### Quick Delete

- Select zone
- Press Delete or Backspace
- Or use toolbar button

### Multi-step Transform

1. Move zone roughly (G)
2. Rotate to desired angle (R)
3. Scale to final size (S)
4. Fine-tune position (G)

## Troubleshooting

### Transform Not Working

- ✓ Check if zone is selected (highlight visible)
- ✓ Check if correct mode is active
- ✓ Ensure not blocked by collision
- ✓ Verify zone is not locked

### Zone Jumps Back

- Reason: Collision or containment violation
- Solution: Move zone to valid position first

### Can't Select Zone

- Click directly on zone mesh
- Not on empty space
- Not on container shape

### Gizmo Not Visible

- Zone must be selected first
- Check if gizmo is behind camera
- Zoom out to see full scene

### Toolbar Disabled

- No zone is selected
- Click a zone to enable
- Selection shown by highlight

## Performance Notes

### Optimal Usage

- **Zones**: Works well with < 30 zones
- **Containers**: 1-5 containers recommended
- **Real-time**: Transform updates at ~60 FPS

### Lag Indicators

- Slow gizmo response
- Delayed mesh updates
- Frame drops during drag

### Optimization Tips

- Hide unneeded containers
- Reduce zone count
- Simplify container geometry
- Use lower quality on weak hardware

## Accessibility

### Mouse Operations

- Left-click: Select
- Left-drag: Transform (on gizmo)
- Right-drag: Orbit camera
- Scroll: Zoom

### Keyboard Shortcuts

- All major operations have shortcuts
- No mouse required for mode switching
- ESC for quick deselect

### Visual Indicators

- Color-coded transform axes
- Highlight on selection
- Opacity changes for feedback

## Common Patterns

### Layout Workflow

```
1. Place essential zones first (high priority)
2. Arrange in logical clusters
3. Add secondary zones around edges
4. Fine-tune spacing between zones
5. Verify no overlaps
```

### Iteration Workflow

```
1. Quick placement (don't worry about precision)
2. Select and refine positions
3. Adjust rotations if needed
4. Scale to optimize space usage
5. Final polish pass
```

## Integration Points

### With Zone Palette

- Drag from palette → Drop in viewport
- Zone type determines initial properties
- Auto-adaptation on placement

### With Properties Panel

- Select zone → Properties appear
- Manual numeric input available
- Sync with transform gizmo

### With Exterior Design

- Containers loaded from exterior app
- Zones placed inside containers
- Updates save to localStorage

## Browser Compatibility

### Supported Browsers

- ✅ Chrome 90+ (Recommended)
- ✅ Firefox 88+
- ✅ Safari 14+
- ✅ Edge 90+

### Known Issues

- Safari: Transform gizmo may flicker
- Firefox: Slight performance lag with many zones
- All: WebGL context loss on tab switch

## Quick Start

### First Time Use

1. Design exterior structure first
2. Switch to Interior Design mode
3. See containers appear as wireframes
4. Drag functional zones from left palette
5. Drop inside containers
6. Zones auto-fit to shape
7. Select and transform to refine
8. Use keyboard shortcuts for speed

### Daily Workflow

1. Load existing design
2. Select zone (click)
3. Transform with G/R/S keys
4. Delete with Del key
5. Save auto-happens (localStorage)

---

**For detailed implementation**: See `TRANSFORM_CONTROLS_UPDATE.md`
**For system architecture**: See `FUNCTIONAL_ZONES_README.md`
**For troubleshooting**: See `DEBUGGING_GUIDE.md`
