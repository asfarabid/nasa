# Functional Zones System

## Overview

The Functional Zones system allows you to define 3D volumes for different habitat functionalities (sleeping, gym, lab, hygiene, etc.) using an intuitive drag-and-drop interface. These zones are:

- **Adaptive**: Automatically fit within container shapes
- **Transparent & Colorful**: Easy visual identification
- **Moveable**: Drag zones within the habitat structure
- **Collision-Aware**: Automatic collision detection and resolution
- **Constraint-Based**: Stay within container boundaries

## Features

### 🎨 Zone Types

The system includes 12 predefined functional zone types:

1. **Sleeping Zone** 🛏️ - Private crew sleeping quarters
2. **Hygiene Zone** 🚿 - Bathroom and personal hygiene facilities
3. **Laboratory Zone** 🔬 - Science lab and research workstations
4. **Exercise Zone** 💪 - Fitness equipment and exercise space
5. **Galley/Kitchen Zone** 🍽️ - Food preparation and cooking area
6. **Dining Zone** 🪑 - Communal eating and social space
7. **Medical Zone** 🏥 - Medical examination and treatment area
8. **Storage Zone** 📦 - General storage for supplies
9. **Command Zone** 🎛️ - Mission control and communication center
10. **Recreation Zone** 🎮 - Leisure and entertainment space
11. **Greenhouse Zone** 🌱 - Plant growth and food production
12. **Airlock Zone** 🚪 - EVA airlock for extravehicular activities

### 🎯 Key Capabilities

#### Drag & Drop Interface

- Simply drag zones from the palette into the 3D viewport
- Zones automatically appear where you drop them
- Visual feedback during dragging

#### Adaptive Sizing

- Zones automatically adapt to fit within container shapes
- Maintains minimum volume requirements
- Respects container boundaries (boxes, cylinders, etc.)

#### Collision Detection

- Prevents zones from overlapping
- Automatic collision resolution
- Real-time collision feedback

#### Alignment & Constraints

- Zones stay within habitat boundaries
- Snap to container walls
- Grid-based positioning available

#### Visual Properties

- Transparent colorful volumes
- Adjustable opacity (10-80%)
- Edge highlighting for better visibility
- Color-coded by function type

## How to Use

### 1. Access Interior Mode

From the main application, switch to "Interior Design" mode to access the functional zones editor.

### 2. Create Zones

**Method 1: Drag & Drop**

1. Browse the Zone Palette on the left
2. Find the zone type you want (e.g., Sleeping Zone)
3. Click and drag it into the 3D viewport
4. Drop it where you want it placed

**Method 2: Properties Panel**

1. Select an existing zone
2. Manually adjust position and size in the properties panel

### 3. Edit Zones

Select a zone by clicking on it in the 3D viewport. The Properties Panel will show:

- **Position**: X, Y, Z coordinates
- **Size**: Width, Height, Depth
- **Opacity**: Transparency level
- **Volume**: Current volume and minimum requirements
- **Metadata**: Priority, adaptive settings

### 4. Move Zones

Click and drag zones directly in the 3D viewport. The system will:

- Constrain movement to stay within containers
- Prevent collisions with other zones
- Show visual feedback during movement

### 5. Manage Zones

From the Properties Panel, you can:

- 🔒 **Lock/Unlock**: Prevent accidental movement
- 👁️ **Show/Hide**: Toggle visibility
- 🗑️ **Delete**: Remove the zone

## Technical Architecture

### Core Modules

#### `functionalZones.js`

Defines zone types and core zone operations:

- Zone definitions with properties
- Zone creation and management
- Three.js mesh generation
- Volume calculations

#### `zoneConstraints.js`

Handles physics and constraints:

- Collision detection between zones
- Container containment checks
- Adaptive sizing algorithms
- Position constraints
- Collision resolution

#### `ZonePalette.jsx`

Drag-and-drop zone library:

- Searchable zone catalog
- Category filters (Essential, Important, Optional)
- Drag preview generation
- Zone metadata display

#### `ZoneViewport.jsx`

Interactive 3D viewport:

- Three.js scene management
- Drag controls for zones
- Drop target handling
- Visual feedback
- Raycasting for selection

#### `ZonePropertiesPanel.jsx`

Zone editing interface:

- Position/size controls
- Visual property adjustments
- Metadata display
- Lock/hide/delete actions

## Collision Detection System

The system uses multiple levels of collision detection:

### 1. AABB (Axis-Aligned Bounding Box)

- Fast initial collision check
- Compares bounding boxes of zones

### 2. Corner-Based Detection

- Checks all 8 corners of each zone
- Ensures complete containment

### 3. Raycasting (for complex shapes)

- Used for cylindrical and custom containers
- Accurate point-in-mesh testing

### 4. Collision Resolution

- Calculates minimum separation vector
- Pushes overlapping zones apart
- Iterative resolution for multiple collisions

## Adaptive Fitting

Zones adapt to their container shape:

### Box Containers

- Zones scaled to fit within 90% of container dimensions
- Maintains aspect ratio when possible

### Cylindrical Containers

- Calculates maximum box size at each position
- Considers radius constraints
- Adapts to tapering cylinders

### Volume Preservation

- Always maintains minimum volume requirements
- Scales proportionally when needed
- Alerts user if volume constraints can't be met

## Data Storage

Zones are persisted in localStorage:

```javascript
{
  id: "zone_1234567890_abc",
  type: "sleeping",
  name: "Sleeping Zone",
  position: [2.5, 0, 0],
  size: { width: 2.5, height: 2.5, depth: 3.0 },
  color: 0x4a90e2,
  opacity: 0.3,
  rotation: [0, 0, 0],
  locked: false,
  visible: true,
  metadata: {
    volume: 18.75,
    isAdaptive: true,
    containerId: "container_123",
    priority: "high"
  }
}
```

## Keyboard Shortcuts (Future)

- `Ctrl + Z`: Undo zone placement
- `Delete`: Delete selected zone
- `L`: Lock/unlock selected zone
- `H`: Hide/show selected zone
- `D`: Duplicate selected zone
- `G`: Toggle grid snapping

## Performance Considerations

- Zones use instanced rendering for efficiency
- Collision detection optimized with spatial partitioning
- Drag operations use requestAnimationFrame
- Automatic cleanup of disposed meshes

## Future Enhancements

- [ ] Multi-select zones
- [ ] Copy/paste zones
- [ ] Zone templates
- [ ] Auto-layout algorithms
- [ ] Ergonomic analysis
- [ ] Accessibility checks
- [ ] Equipment placement within zones
- [ ] Zone connections/adjacency requirements
- [ ] Export to IFC/BIM formats
- [ ] VR walkthrough mode

## API Reference

### Create a Zone

```javascript
import { createFunctionalZone } from "./utils/functionalZones";

const zone = createFunctionalZone("sleeping", [0, 0, 0]);
```

### Check Collision

```javascript
import { zonesOverlap } from "./utils/zoneConstraints";

const hasCollision = zonesOverlap(zone1, zone2);
```

### Adapt to Container

```javascript
import { adaptZoneToContainer } from "./utils/zoneConstraints";

const adaptedZone = adaptZoneToContainer(zone, containerMesh);
```

### Resolve All Collisions

```javascript
import { resolveZoneCollisions } from "./utils/zoneConstraints";

const resolvedZones = resolveZoneCollisions(allZones);
```

## Troubleshooting

### Zones not appearing

- Check that exterior geometry is loaded
- Verify zones array is not empty
- Check browser console for errors

### Collision detection not working

- Ensure zones have valid geometry
- Check that container mesh is available
- Verify zone positions are within bounds

### Performance issues

- Reduce number of zones
- Lower opacity for better GPU performance
- Disable shadows if enabled

## Credits

Built with:

- **Three.js** - 3D rendering
- **React** - UI framework
- **React Three Fiber** - React renderer for Three.js
- **DragControls** - Interactive dragging

---

For more information, see the main [Interior Design Documentation](./INTERIOR_DOCS_INDEX.md).
