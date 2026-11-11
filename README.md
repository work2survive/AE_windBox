# AE WindBox Panel + 3D Cube Maker (After Effects ScriptUI)

A procedural 3D Wind Volume Particle System for Adobe After Effects, integrated with the parametric 3D Cube Maker architecture from:
**[work2survive/AE-Cube-Maker-3D](https://github.com/work2survive/AE-Cube-Maker-3D)**

---

## 🎲 3D Cube Maker Architecture

The 3D volume bounding box is built directly using the 6-face parametric shape layer architecture from `AE-Cube-Maker-3D`:

- **6 Parametric 3D Shape Layers**:
  - `Face_Front`, `Face_Back`, `Face_Left`, `Face_Right`, `Face_Top`, `Face_Bottom`
- **White Stroke Lines**: Crisp `#FFFFFF` outline edges (customizable stroke width and opacity).
- **Semitransparent Grey Sides**: `#888888` fill with very low opacity (default 12%) for a subtle holographic/glass container look.
- **Dynamic Expression Rigging**:
  All 6 faces are parented to the Master Controller. Their 3D positions, dimensions, fill opacity, and stroke are driven by live expressions linked to:
  - `WindBox - Size X`
  - `WindBox - Size Y`
  - `WindBox - Size Z`
  - `WindBox - Cube Fill Opacity`
  - `WindBox - Cube Stroke Width`
  - `WindBox - Cube Stroke Opacity`
  When you keyframe or change the box size in the timeline, the 3D cube expands, contracts, and tracks the volume in real time!
- **Clean Timeline (`shy = true`)**: The face layers are marked as shy layers, keeping your composition timeline uncluttered.
- **Optional Guide Layer**: Choose whether the cube should act as an editing-only visualizer (`Guide Layer = true`) or render to the final export.

---

## 🚀 Animatable Parameters

All parameters are rigged to the master **`[SystemName]_Controller`** layer as native Expression Sliders:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| **Size X, Y, Z** | *Animatable* | Defines the 3D volume dimensions. Drives both particle wrapping and the 6 faces of the 3D cube. |
| **Wind Speed** | *Animatable* | Speed of particles along the wind direction vector (in pixels/second). |
| **Number of Particles** | *Animatable* | Controls active particle count with smooth visibility culling (opacity & scale). |
| **Direction X, Y, Z** | *Animatable* | 3D directional vector controlling wind trajectory. Auto-normalizes in 3D space. |
| **Pos Wiggle Frequency** | *Animatable* | Frequency (Hz / wiggles per second) of positional turbulence. |
| **Pos Wiggle Amp X, Y, Z** | *Animatable* | Independent amplitude (pixels) for positional wiggle on X, Y, and Z axes. |
| **Rot X Wiggle Amp & Freq** | *Animatable* | Amplitude (degrees) and Frequency (Hz) for X-axis rotational turbulence. |
| **Rot Y Wiggle Amp & Freq** | *Animatable* | Amplitude (degrees) and Frequency (Hz) for Y-axis rotational turbulence. |
| **Rot Z Wiggle Amp & Freq** | *Animatable* | Amplitude (degrees) and Frequency (Hz) for Z-axis rotational turbulence. |
| **Cube Fill & Stroke** | *Animatable* | Color and opacity controls for the 3D cube sides and white outline edges. |

---

## 📥 Installation

### As a Dockable ScriptUI Panel (Recommended)
1. Copy `AE_WindBox_Panel.jsx` into your After Effects `ScriptUI Panels` directory:
   - **Windows**: `C:\Program Files\Adobe\Adobe After Effects <Version>\Support Files\Scripts\ScriptUI Panels\`
   - **macOS**: `/Applications/Adobe After Effects <Version>/Scripts/ScriptUI Panels/`
2. Restart After Effects (or refresh scripts).
3. In After Effects, open **Window** > **AE_WindBox_Panel.jsx**.
4. Drag and dock the panel anywhere in your workspace.

### Run Standalone
- In After Effects, go to **File** > **Scripts** > **Run Script File...** and select `AE_WindBox_Panel.jsx`.

---

## 🔗 Credits
- 3D Cube Maker Topology: [github.com/work2survive/AE-Cube-Maker-3D](https://github.com/work2survive/AE-Cube-Maker-3D)
