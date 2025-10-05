# 🎨 Functional Zones - Visual UI Guide

## Interface Layout

```
┌────────────────────────────────────────────────────────────────────────────┐
│  🚀 Habitat Creator     [🏗️ Exterior Design] [🏠 Interior Design]          │
│                          → Interior: Default Test Habitat (7.5m × 20m)     │
├────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌──────────┐  ┌──────────────────────────────────────┐  ┌──────────┐   │
│  │          │  │                                        │  │          │   │
│  │  Zone    │  │         3D Viewport                   │  │  Zone    │   │
│  │ Palette  │  │     (Drag & Drop Here)                │  │Properties│   │
│  │          │  │                                        │  │          │   │
│  │  🔍      │  │  ┌─────────────────────────────┐     │  │  🛏️      │   │
│  │ Search   │  │  │                              │     │  │ Sleeping │   │
│  │          │  │  │   🏗️  [Wireframe Container]│     │  │  Zone    │   │
│  │ [All]    │  │  │                              │     │  │          │   │
│  │Essential │  │  │   ┏━━━━━━━━━┓               │     │  │ Position │   │
│  │Important │  │  │   ┃ Zone 1  ┃ ← Transparent│     │  │  X: 2.5  │   │
│  │ Optional │  │  │   ┗━━━━━━━━━┛   Colorful   │     │  │  Y: 0.0  │   │
│  │          │  │  │                    Volume   │     │  │  Z: 0.0  │   │
│  │┌────────┐│  │  │                              │     │  │          │   │
│  ││🛏️Sleep││  │  │   Grid                       │     │  │ Size     │   │
│  ││Sleeping││  │  └─────────────────────────────┘     │  │  W: 2.5  │   │
│  │└────────┘│  │                                        │  │  H: 2.5  │   │
│  │          │  │  Info: Zones: 3                       │  │  D: 3.0  │   │
│  │┌────────┐│  │                                        │  │          │   │
│  ││🚿Hygiene││  │  🎯 Drop to place zone               │  │ Opacity  │   │
│  │└────────┘│  │                                        │  │ ▓▓▓░░ 30%│   │
│  │          │  │                                        │  │          │   │
│  │┌────────┐│  │                                        │  │ 🔒 🗑️   │   │
│  ││🔬 Lab  ││  │                                        │  │          │   │
│  │└────────┘│  │                                        │  └──────────┘   │
│  │          │  │                                        │                 │
│  └──────────┘  └──────────────────────────────────────┘                 │
│                                                                             │
└────────────────────────────────────────────────────────────────────────────┘
```

## Panel Breakdown

### 1️⃣ Left Panel: Zone Palette (320px)

```
┌─────────────────────────┐
│ 🎨 Functional Zones     │
│ Drag zones into habitat │
├─────────────────────────┤
│ 🔍 Search zones...      │
├─────────────────────────┤
│ [All] Essential         │
│ Important Optional      │
├─────────────────────────┤
│ ┌─────────────────────┐ │
│ │ 🛏️  Sleeping Zone   │ │  ← Draggable Cards
│ │ Private sleeping... │ │
│ │ high | 6m³ min     │ │
│ └─────────────────────┘ │
│                         │
│ ┌─────────────────────┐ │
│ │ 🚿  Hygiene Zone    │ │
│ │ Bathroom and...     │ │
│ │ high | 3m³ min     │ │
│ └─────────────────────┘ │
│                         │
│ ┌─────────────────────┐ │
│ │ 🔬  Laboratory Zone │ │
│ │ Science lab...      │ │
│ │ medium | 8m³ min   │ │
│ └─────────────────────┘ │
│                         │
│ ... (more zones)        │
├─────────────────────────┤
│ Instructions:           │
│ 🖱️ Drag zones into 3D  │
│ 🎯 Auto-adapt to shape │
│ 🚫 Auto-collision       │
└─────────────────────────┘
```

### 2️⃣ Center: 3D Viewport (Flexible)

```
┌─────────────────────────────────────────┐
│ 🏗️ Interior Functional Zones            │
│ [1 Containers] [3 Zones]                │
├─────────────────────────────────────────┤
│                                         │
│         Camera Controls                 │
│    ┌───────────────────────┐           │
│    │                        │           │
│    │  🌐 OrbitControls      │           │
│    │  • Rotate: Drag        │           │
│    │  • Pan: Right-drag     │           │
│    │  • Zoom: Scroll        │           │
│    │                        │           │
│    │  ┏━━━━━━━━━━━┓         │  ← Zones
│    │  ┃  Zone 1   ┃         │  (Transparent
│    │  ┗━━━━━━━━━━━┛         │   Colored)
│    │                        │
│    │  ┏━━━━━━━━━━━┓         │
│    │  ┃  Zone 2   ┃         │
│    │  ┗━━━━━━━━━━━┛         │
│    │                        │
│    │  [Wireframe Container] │  ← Habitat
│    │                        │   (Semi-trans)
│    │  ═══════════════       │  ← Grid
│    └───────────────────────┘
│                                         │
│ Info: Zones: 3                         │
│ 🎯 Drop to place sleeping zone         │ ← Drop hint
└─────────────────────────────────────────┘
```

### 3️⃣ Right Panel: Properties (320px)

```
┌─────────────────────────┐
│ 🛏️ Sleeping Zone        │
│ 🔒 👁️                   │  ← Lock/Hide
├─────────────────────────┤
│ Private crew sleeping   │
│ quarters with storage   │
├─────────────────────────┤
│ Volume: 18.75 m³        │  ← Volume check
│ ✓ Meets minimum         │
├─────────────────────────┤
│ ▼ Position              │
│   X  [ 2.50 ] m         │
│   Y  [ 0.00 ] m         │
│   Z  [ 0.00 ] m         │
├─────────────────────────┤
│ ▼ Size                  │
│   Width  [ 2.50 ] m     │
│   Height [ 2.50 ] m     │
│   Depth  [ 3.00 ] m     │
├─────────────────────────┤
│ ▼ Appearance            │
│   Opacity ▓▓▓░░░ 30%    │
├─────────────────────────┤
│ ▼ Metadata              │
│   Priority: high        │
│   Min Volume: 6 m³      │
│   Adaptive: ✓ Yes       │
├─────────────────────────┤
│ [ 🗑️ Delete Zone ]      │  ← Delete button
└─────────────────────────┘
```

## Zone Visual Styles

### Zone Appearance in 3D

```
┌─────────────────────────────────────────┐
│                                         │
│   Sleeping Zone (Blue)                  │
│   ┏━━━━━━━━━━━━━┓                      │
│   ┃             ┃  ← Transparent fill  │
│   ┃  🛏️         ┃     (opacity 30%)    │
│   ┃             ┃                      │
│   ┗━━━━━━━━━━━━━┛  ← Colored edges     │
│        (Blue glow when selected)        │
│                                         │
│   Lab Zone (Cyan)                       │
│   ┏━━━━━━━━━━━━━┓                      │
│   ┃             ┃                      │
│   ┃  🔬         ┃                      │
│   ┃             ┃                      │
│   ┗━━━━━━━━━━━━━┛                      │
│                                         │
│   Gym Zone (Purple)                     │
│   ┏━━━━━━━━━━━━━┓                      │
│   ┃             ┃                      │
│   ┃  💪         ┃                      │
│   ┃             ┃                      │
│   ┗━━━━━━━━━━━━━┛                      │
│                                         │
└─────────────────────────────────────────┘
```

## Color Coding

| Zone Type     | Color      | Hex     | Priority |
| ------------- | ---------- | ------- | -------- |
| 🛏️ Sleeping   | Blue       | #4a90e2 | High     |
| 🚿 Hygiene    | Green      | #7ed321 | High     |
| 🔬 Lab        | Cyan       | #50e3c2 | Medium   |
| 💪 Gym        | Purple     | #bd10e0 | Medium   |
| 🍽️ Kitchen    | Orange     | #f5a623 | High     |
| 🪑 Dining     | Yellow     | #f8b500 | Medium   |
| 🏥 Medical    | Red        | #ff4444 | High     |
| 📦 Storage    | Violet     | #9013fe | Low      |
| 🎛️ Command    | Royal Blue | #4169e1 | High     |
| 🎮 Recreation | Cyan       | #00d4ff | Low      |
| 🌱 Greenhouse | Lime       | #00ff88 | Medium   |
| 🚪 Airlock    | Gray       | #666666 | High     |

## Interaction States

### Normal State

```
┏━━━━━━━━━━━┓
┃  Zone     ┃  ← 30% opacity
┗━━━━━━━━━━━┛    Colored edges
```

### Hover State

```
┏━━━━━━━━━━━┓
┃  Zone     ┃  ← 35% opacity
┗━━━━━━━━━━━┛    Brighter edges
   (cursor: grab)
```

### Selected State

```
╔═══════════╗
║  Zone     ║  ← 40% opacity
╚═══════════╝    Glowing edges
                 Thicker border
```

### Dragging State

```
┏━━━━━━━━━━━┓
┃  Zone     ┃  ← 50% opacity
┗━━━━━━━━━━━┛    Pulse animation
   (cursor: grabbing)
```

### Collision Warning

```
┏━━━━━━━━━━━┓
┃  Zone     ┃  ← Red tint
┗━━━━━━━━━━━┛    Red edges
   ⚠️ Collision detected
```

## Responsive Behavior

### Desktop (> 1200px)

```
[Zone Palette 320px] [Viewport Flex] [Properties 320px]
```

### Tablet (968px - 1200px)

```
[Zone Palette 280px] [Viewport Flex] [Properties 280px]
```

### Mobile (< 968px)

```
┌──────────────────────┐
│  Zone Palette (50vh) │  ← Collapsible
├──────────────────────┤
│  Viewport (50vh)     │
└──────────────────────┘
Properties hidden on mobile
```

## Animation Effects

### Fade In

- All panels fade in on load
- Duration: 0.3s

### Drop Hint Pulse

- Pulsing glow when dragging
- Scale: 1.0 → 1.05 → 1.0
- Duration: 2s loop

### Border Flash

- Selected zones flash border
- Opacity: 1.0 → 0.5 → 1.0
- Duration: 1s loop

### Bounce Icon

- Drag hint icon bounces
- Y offset: 0 → -10px → 0
- Duration: 1s loop

---

## Quick Reference

### Mouse Controls

- **Select**: Left click zone
- **Move**: Click + drag zone
- **Rotate View**: Left drag empty space
- **Pan View**: Right drag
- **Zoom**: Scroll wheel

### Visual Hierarchy

1. Selected zone: Brightest, glowing
2. Hovered zone: Slightly brighter
3. Normal zones: Standard opacity
4. Container: Very transparent (10%)

---

_This guide shows the complete visual structure of the Functional Zones interface!_
