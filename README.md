---

## Project Overview

This project is a **3rd Person Character Controller with Minimap** built using React, Three.js (via React Three Fiber), and Rapier physics. It allows users to control a 3D character in various detailed environments, with real-time minimap tracking and smooth camera/character controls. The environments are loaded from high-quality GLB models, and the user can switch between different maps interactively.

---

## Features

- **3rd Person Character Controller**: Move a character using WASD/arrow keys and Shift to run, with smooth rotation and animation blending.
- **Multiple 3D Maps**: Switch between several detailed environments (castle, city, fantasy, etc.) with physics-enabled navigation.
- **Minimap**: Real-time minimap with zoom and autorotation, showing the character’s position and orientation.
- **Physics Integration**: Uses Rapier for realistic movement and collision.
- **Customizable Controls**: Tweak movement speed, rotation, and minimap settings via Leva UI panels.
- **Responsive UI**: Fullscreen canvas with fixed-position minimap overlay.
- **Modern React Stack**: Built with Vite, React 19, and hooks-based state management (Valtio).

---

## Directory Structure

```
/
├── public/
│   ├── models/         # GLB 3D models for maps and character
│   └── textures/       # Textures for minimap/character
├── src/
│   ├── components/     # Main React components (Character, Controller, Map, Minimap, Experience)
│   ├── assets/         # Static assets (e.g., react.svg)
│   ├── App.jsx         # Main app entry, layout, and state
│   ├── main.jsx        # ReactDOM entry point
│   └── index.css       # Global styles
├── index.html          # HTML entry point
├── package.json        # Dependencies and scripts
└── README.md           # Project documentation
```

---

## Installation

### Prerequisites

- Node.js (v16+ recommended)
- Yarn (or npm)

### Steps

```bash
yarn install
yarn dev
```

Open [http://localhost:5173](http://localhost:5173) in your browser.

---

## Usage

- **Move Character**: `WASD` or `Arrow Keys`
- **Run**: Hold `Shift`
- **Switch Map**: Use the Leva UI panel (top-right by default)
- **Minimap Controls**: Use Leva UI to zoom or toggle autorotation

---

## Component Architecture

### 1. `App.jsx`
- Sets up the main 3D canvas and overlays (`Experience` and `Minimap`).
- Manages global game state (current map, character position, container rotation) using Valtio.
- Keyboard controls are mapped for movement and running.

### 2. `Experience.jsx`
- Handles environment setup, lighting, and physics.
- Allows map switching via Leva controls.
- Loads the selected map and the character controller.

### 3. `CharacterController.jsx`
- Handles all character movement, rotation, and animation state.
- Integrates keyboard and mouse/touch controls.
- Updates camera position and orientation smoothly.
- Uses Rapier physics for realistic movement and collision.

### 4. `Character.jsx`
- Loads and animates the character GLB model.
- Switches between idle, walk, and run animations based on controller state.

### 5. `Map.jsx`
- Loads the selected map GLB model.
- Applies physics colliders for navigation.
- Ensures all meshes cast and receive shadows.

### 6. `Minimap.jsx`
- Renders a top-down minimap of the current map and character.
- Camera follows the character and can autorotate.
- Character’s position and orientation are shown with a custom marker.

---

## Customization

- **Add New Maps**: Place new `.glb` files in `public/models/` and add their config to `maps` in `Experience.jsx`.
- **Change Character**: Replace `public/models/character.glb` and update `Character.jsx` if the skeleton changes.
- **Textures**: Update `public/textures/wawa.jpg` for the minimap character marker.

---

## Dependencies

- `react`, `react-dom`: UI framework
- `three`: 3D rendering
- `@react-three/fiber`: React renderer for Three.js
- `@react-three/drei`: Useful helpers for R3F
- `@react-three/rapier`: Physics integration
- `leva`: UI controls for tweaking parameters
- `valtio`: Proxy-based state management
- `vite`: Fast dev server and build tool

---

## Scripts

- `yarn dev`: Start development server
- `yarn build`: Build for production
- `yarn preview`: Preview production build

---

## 3D Models Credits

- [Castle on Hills](https://sketchfab.com/3d-models/castle-on-hills-b874cb19b42741729b950f6afbdf0dea)
- [De Dust 2 with Real Light](https://sketchfab.com/3d-models/de-dust-2-with-real-light-4ce74cd95c584ce9b12b5ed9dc418db5)
- [Animal Crossing Map](https://sketchfab.com/3d-models/animal-crossing-map-9f53cb8a02134037887875e022b2eae2)
- [Medieval Fantasy Book](https://sketchfab.com/3d-models/medieval-fantasy-book-06d5a80a04fc4c5ab552759e9a97d91a)
- [City Scene Tokyo](https://sketchfab.com/3d-models/city-scene-tokyo-b25d23ff186949dca3df669c14447db5)

---

## Advanced Details

- **Physics**: Uses trimesh colliders for maps and capsule collider for the character.
- **State Management**: Valtio proxies for real-time reactivity across components.
- **Performance**: Shadows, environment lighting, and camera lerping for smooth visuals.
- **Extensibility**: Easily add new maps, characters, or UI controls.

---