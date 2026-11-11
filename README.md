# AE WindBox (v1.0)

[![Live Browser Simulator](https://img.shields.io/badge/Live%20Demo-AE%20ScriptUI%20Simulator-2c8cff?style=for-the-badge&logo=javascript)](https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Adobe After Effects](https://img.shields.io/badge/Adobe%20After%20Effects-CS6%20--%20CC%202026%2B-9999FF?style=for-the-badge&logo=adobeaftereffects)](https://www.adobe.com/products/aftereffects.html)
[![Built with Antigravity](https://img.shields.io/badge/Built%20With-Antigravity-4285F4?style=for-the-badge&logo=google)](https://deepmind.google/)

**Live Demo**: [https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true](https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true)

A procedural 3D Wind Volume Particle System for Adobe After Effects, integrated with the parametric 3D Cube Maker architecture from:
**[work2survive/AE-Cube-Maker-3D](https://github.com/work2survive/AE-Cube-Maker-3D)**.

> **Live Browser Simulator**: Test and preview this tool interactively in the [AE JS & ScriptUI Simulator](https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true) directly in your web browser without launching After Effects!

---

## 🎲 3D Cube Maker Architecture

The 3D volume bounding box is built directly using the 6-face parametric shape layer architecture from `AE-Cube-Maker-3D`:

- **6 Parametric 3D Shape Layers**:
  - `Face_Front`, `Face_Back`, `Face_Left`, `Face_Right`, `Face_Top`, `Face_Bottom`
- **White Stroke Lines & Face Colors**: Crisp outline edges and customizable face fill colors with live color pickers, opacity, and stroke width.
- **Dynamic Expression Rigging**:
  All 6 faces are parented to the Master Controller. Their 3D positions, dimensions, fill opacity, and stroke are driven by live expressions linked to:
  - `WindBox - Size X`
  - `WindBox - Size Y`
  - `WindBox - Size Z`
  - `WindBox - Cube Fill Color`
  - `WindBox - Cube Fill Opacity`
  - `WindBox - Cube Stroke Color`
  - `WindBox - Cube Stroke Width`
  - `WindBox - Cube Stroke Opacity`
  When you keyframe or change the box size in the timeline, the 3D cube expands, contracts, and tracks the volume in real time!
- **Clean Timeline (`shy = true`)**: The face layers are marked as shy layers, keeping your composition timeline uncluttered.
- **Optional Guide Layer**: Choose whether the cube should act as an editing-only visualizer (`Guide Layer = true`) or render to the final export.

---

## 💨 Procedural Wind Dynamics & Particles

- **Continuous 3D Flow**: Particles move smoothly through 3D space driven by wind speed and a normalized 3D direction vector $[X, Y, Z]$.
- **Seamless Volume Wrapping**: When particles leave the 3D cube bounding box, they seamlessly wrap around to the opposite side, ensuring continuous flow without popping.
- **3-Axis Positional Turbulence**: Independent wiggle frequency and amplitudes along the X, Y, and Z axes.
- **3-Axis Rotational Turbulence**: Independent angular wiggle frequency and amplitudes for pitch, yaw, and roll.
- **Dynamic Particle Culling**: Scale and opacity expressions seamlessly hide inactive particles when the particle count slider is adjusted or animated.
- **Multiple Particle Sources**: Choose between built-in 3D vector circles, 3D vector squares, or custom selected composition layer(s).

---

## 🚀 Animatable Parameters

All parameters are rigged to the master **`[SystemName]_Controller`** layer as native Expression Controls:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| **Size X, Y, Z** | *Slider* | Defines 3D volume dimensions. Drives both particle wrapping and the 6 faces of the 3D cube. |
| **Wind Speed** | *Slider* | Speed of particles along the wind direction vector (in pixels/second). |
| **Number of Particles** | *Slider* | Controls active particle count with smooth visibility culling (opacity & scale). |
| **Direction X, Y, Z** | *Slider* | 3D directional vector controlling wind trajectory. Auto-normalizes in 3D space. |
| **Pos Wiggle Freq** | *Slider* | Frequency (Hz / wiggles per second) of positional turbulence. |
| **Pos Wiggle Amp X, Y, Z** | *Slider* | Independent amplitude (pixels) for positional wiggle on X, Y, and Z axes. |
| **Rot X Wiggle Amp & Freq** | *Slider* | Amplitude (degrees) and Frequency (Hz) for X-axis rotational turbulence. |
| **Rot Y Wiggle Amp & Freq** | *Slider* | Amplitude (degrees) and Frequency (Hz) for Y-axis rotational turbulence. |
| **Rot Z Wiggle Amp & Freq** | *Slider* | Amplitude (degrees) and Frequency (Hz) for Z-axis rotational turbulence. |
| **Cube Fill Color & Opacity** | *Color / Slider* | Color and opacity controls for the 3D cube sides. |
| **Cube Stroke Color & Width** | *Color / Slider* | Color, width, and opacity controls for the 3D cube outline edges. |

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

## 🛠️ Usage

1. Open or create a composition in Adobe After Effects.
2. Open the **AE WindBox** panel.
3. Configure the box dimensions, wind speed, direction, wiggle parameters, and cube appearance.
4. Click **Build / Create WindBox + Cube**.
5. The rigged controller, 3D cube faces, and particles will be automatically created and animated in your composition!
6. Use **Sync to Controller** to push modified panel values to an existing system, or **Read Controller** to pull values from the selected controller back into the UI.

---

## 📁 Repository Structure

```text
AE_windBox/
├── AE_WindBox_Panel.jsx    # Primary ScriptUI panel for After Effects
├── README.md               # Documentation & parameters reference
├── LICENSE                 # MIT License
└── .gitignore              # Git ignore rules
```

---

## 🔗 Related Projects

- **[AE JS & ScriptUI Simulator](https://github.com/work2survive/AE_JS_builder)**: Agnostic browser-based emulator for developing and testing After Effects ScriptUI panels and 2D/3D shape layers.
- **[AE Cube Maker 3D](https://github.com/work2survive/AE-Cube-Maker-3D)**: Parametric 3D cube generator with independent face colors, opacity, stroke controls, and collapsed-transformation master rigging.
- **[AE Cylinder Maker 3D](https://github.com/work2survive/AE-Cylinder-Maker-3D)**: Parametric 3D cylinder and circular slice sector generator with auto-rigged wall facets.
- **[AECustomRoundedRect](https://github.com/work2survive/AECustomRoundedRect)**: Independent 4-corner rounded rectangle generator for After Effects.
- **[AE Message Bubble Generator](https://github.com/work2survive/AE_message_bubble)**: Authentic chat and text message bubble generator for After Effects.

---

## 🤖 Acknowledgments

Engineered, architected, and co-developed using **[Google DeepMind Antigravity](https://deepmind.google/)** agentic coding assistant.

## 📄 License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.
