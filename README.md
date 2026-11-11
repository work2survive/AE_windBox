# AE WindBox (v1.1)

[![Live Browser Simulator](https://img.shields.io/badge/Live%20Demo-AE%20ScriptUI%20Simulator-2c8cff?style=for-the-badge&logo=javascript)](https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)
[![Adobe After Effects](https://img.shields.io/badge/Adobe%20After%20Effects-CS6%20--%20CC%202026%2B-9999FF?style=for-the-badge&logo=adobeaftereffects)](https://www.adobe.com/products/aftereffects.html)
[![Built with Antigravity](https://img.shields.io/badge/Built%20With-Antigravity-4285F4?style=for-the-badge&logo=google)](https://deepmind.google/)

**Live Demo**: [https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true](https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true)

A procedural 3D Wind Volume Particle System for Adobe After Effects, integrated with the parametric 3D Cube Maker architecture from **[work2survive/AE-Cube-Maker-3D](https://github.com/work2survive/AE-Cube-Maker-3D)**.

The primary purpose of **AE WindBox** is to create a **virtual 3D cube bounding box visible only as a Guide Layer** in After Effects. Inside this bounded 3D volume, particles move and rotate along the wind vector with continuous wrapping, aerodynamic orientation, and turbulence. Includes built-in presets (**Leaves**, **Clouds**, **Stars**, **Mountains**, **Circles**, **Squares**), as well as direct instantiation of **Project Compositions** and **Selected Timeline Layers**.

> **Live Browser Simulator**: Test and preview this tool interactively in the [AE JS & ScriptUI Simulator](https://work2survive.github.io/AE_JS_builder/?jsx=AE_WindBox_Panel.jsx&autobuild=true) directly in your web browser without launching After Effects!

---

## 🎯 Key Features

### 1. Virtual 3D Cube (Guide Layer — Viewport Only)
- **Viewport Framing Only**: All 6 bounding faces are created as native After Effects **Guide Layers** (`guideLayer = true`) by default. They remain clearly visible in the working canvas for framing your camera and motion, but are **100% invisible in final exports and renders**.
- **6-Face Rigged Geometry**: Front, Back, Left, Right, Top, and Bottom faces parented to the Master Controller with dynamic expressions driving size, position, fill color, opacity, and outline stroke.
- **Collapsible Timeline**: Face layers are marked as shy layers (`shy = true`), keeping the composition timeline tidy.

### 2. Wind-Driven Motion & Directional Rotation
- **Wind Vector $[X, Y, Z]$**: Particles travel continuously through 3D space driven by wind speed and a 3D direction vector.
- **Align Rotation to Wind**: When enabled, particles dynamically calculate the wind angle $\text{atan2}(dY, dX)$ and steer along the wind vector, mimicking natural aerodynamic flight (leaves, debris, arrows).
- **Seamless 3D Volume Wrapping**: When particles leave the 3D cube bounding box, they seamlessly wrap around to the opposite side, ensuring endless organic flow.
- **3-Axis Positional & Rotational Turbulence**: Realistic atmospheric turbulence with independent frequency and amplitude controls on X, Y, and Z.

### 3. Presets & Particle Sources
- **External JSON Configuration (`AE_windbox/presets.json`)**: All presets and physical parameters are loaded from an external JSON file located in `AE_windbox/presets.json` next to the script. If the folder and file do not exist on first launch, the script automatically generates them with all factory defaults. Edit freely or add your own custom presets, then press the reload button (**🔄**) in the UI to instantly refresh without restarting After Effects!
- **🍃 Falling Leaves**: Procedural Bézier teardrop leaf paths with organic flutter, tumbling wiggle, aerodynamic wind alignment, and natural autumn palettes (forest green, amber, orange, crimson).
- **☁️ Drifting Clouds**: Multi-puff billowy clouds traversing a wide 3D volume on a diagonal breeze ([0.85, -0.12, -0.65]), passing gently in front of the camera with soft ethereal translucency.
- **⭐ Cosmic Stars**: 5-point vector stars with celestial shimmer and gentle cosmic drift.
- **⛰️ Parallax Mountains**: Low-poly geometric mountain silhouettes with majestic slow horizon glide.
- **⚪ 3D Circles**: Dust motes, snow, bubbles, or spores.
- **⬛ 3D Squares**: Confetti, geometric debris, or pixel tiles.
- **🎬 Project Composition**: Instantiate any existing CompItem from your active After Effects project via dropdown picker!
- **🎯 Selected Layer(s)**: Duplicate and drive any user-selected timeline layer(s) as the particle source.

---

## 🚀 Animatable Parameters

All parameters are rigged to the master **`[SystemName]_Controller`** layer as native Expression Controls:

| Parameter | Type | Description |
| :--- | :--- | :--- |
| **Random Seed** | *Slider* | Master integer seed governing deterministic PRNG for all particles (`seed + pIndex`). |
| **Size X, Y, Z** | *Slider* | Defines 3D volume dimensions. Drives both particle wrapping and the 6 faces of the virtual cube. |
| **Wind Speed** | *Slider* | Speed of particles along the wind direction vector (in pixels/second). |
| **Direction X, Y, Z** | *Slider* | 3D directional vector controlling wind trajectory. Auto-normalizes in 3D space. |
| **Align to Wind** | *Checkbox* | When enabled, dynamically rotates particles to orient along the wind vector. |
| **Number of Particles** | *Slider* | Controls active particle count with smooth visibility culling (opacity & scale). |
| **Fade In / Out Distance** | *Slider* | Boundary fade distances (px) that transition opacity smoothly from 0 to 100% at birth and 100% to 0 at exit, eliminating wrapping pops. |
| **Size Random (%)** | *Slider* | Percentage of particle scale variation applied at birth. |
| **Scale Wiggle Freq & Amp**| *Slider* | Dynamic scale breathing/pulsating frequency (Hz) and amplitude (%). |
| **Cube Guide Layer** | *Checkbox* | Toggles Guide Layer status on the virtual bounding box. |
| **Cube Fill & Stroke** | *Color / Slider* | Live color pickers, opacity, and stroke width for the virtual cube faces. |
| **Pos Wiggle Freq & Amp** | *Slider* | 3-axis positional turbulence frequency (Hz) and amplitudes (px) for X, Y, Z. |
| **Rot X, Y, Z Wiggle** | *Slider* | Independent rotational turbulence amplitudes (degrees) and frequencies (Hz) for pitch, yaw, and roll. |

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

1. Open or create an active composition in Adobe After Effects.
2. Launch the **AE WindBox** panel.
3. Select a preset (e.g. **🍃 Falling Leaves**, **☁️ Drifting Clouds**, **⭐ Stars**, or **🎬 Project Composition**).
4. Customize dimensions, wind speed, wind direction vector, and wiggle parameters.
5. Click **Build / Create WindBox + Cube**.
6. A master controller null, 6 guide layer cube faces, and particles will be automatically created and animated in 3D space!
7. All parameters can be keyframed and customized directly on the Master Controller null in After Effects via native Expression Controls.

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
