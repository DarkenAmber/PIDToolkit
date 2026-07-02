# PID Toolkit

**Browser-based PID controller tuning tool.**  
One HTML file — works offline, with no dependencies and no backend.

🌐 **Live Demo:** [PID Toolkit](https://darkenamber.github.io/PIDToolkit/)

📂 **GitHub:** [DarkenAmber/PIDToolkit](https://github.com/DarkenAmber/PIDToolkit)

![DarkenAmber](https://img.shields.io/badge/style-DarkenAmber-E8A020)
![License](https://img.shields.io/badge/license-MIT-green)
![Version](https://img.shields.io/badge/version-1.0-blue)

---

# What it does

Enter your plant model (**K**, **T**, **L**) and PID Toolkit instantly provides:

- PID coefficients calculated using multiple tuning methods
- Animated step response simulation
- Animated Bode plot with Phase Margin and Gain Margin
- Side-by-side comparison of all tuning methods
- Ready-to-use controller code generation
- Engineering warnings about delay, noise and saturation

---

# Supported tuning methods

| Method | Type | Input |
|--------|------|-------|
| Ziegler–Nichols (Open Loop) | Classic | K, T, L |
| Ziegler–Nichols (Closed Loop) | Ultimate Gain | Ku, Tu |
| CHR (0% Overshoot) | Conservative | K, T, L |
| CHR (20% Overshoot) | Moderate | K, T, L |
| ITAE Servo | Servo optimization | K, T, L |
| ITAE Regulator | Disturbance rejection | K, T, L |
| Lambda / IMC | Model-based | K, T, L + λ |

---

# Code generation

Generated implementations include:

- **D on Measurement** (eliminates derivative kick)
- **Conditional Anti-Windup**
- Optional derivative filtering

Supported platforms:

- Arduino
- ESP32 + FreeRTOS
- MicroPython
- IEC 61131-3 Structured Text (Siemens, CODESYS, Schneider, Beckhoff)

---

# Quick presets

| Preset | K | T | L |
|--------|---|---|---|
| 🌡 Temperature | 0.8 | 120 s | 15 s |
| ⚡ Pressure | 1.2 | 5 s | 0.5 s |
| 💧 Level | 1.0 | 30 s | 3 s |
| ⚙ DC Motor Speed | 2.0 | 0.5 s | 0.05 s |
| ⚙ DC Motor Position | 1.0 | 0.8 s | 0.1 s |
| ⚙ Servo | 1.5 | 0.2 s | 0.02 s |
| ⚙ Conveyor / Geared Motor | 0.5 | 2.0 s | 0.3 s |

---

# Features

- Animated oscilloscope-style step response
- Animated Bode plot
- Automatic parameter recalculation
- Sortable comparison table
- Phase Margin and Gain Margin calculation
- First-order derivative filter
- Conditional anti-windup
- URL hash sharing
- Import / Export JSON
- PDF-friendly print layout
- EN / RU interface
- Fully offline operation

---

# Usage

1. Download **pid-toolkit.html**
2. Open it in any modern browser.
3. Enter **K**, **T** and **L**, or choose a preset.
4. Compare tuning methods.
5. Analyze the response.
6. Export controller code for your platform.

---

# Target audience

- Arduino developers
- ESP32 developers
- PLC programmers
- Control engineers
- Automation students
- Anyone who needs quick PID tuning without installing MATLAB or similar software

---

# Architecture

Designed as a **single HTML file**.

No installation.

No build step.

No npm.

No framework.

No backend.

Core execution flow:

```
calcAll()
    ↓
simulate()
    ↓
metrics()
    ↓
renderCompTable()
    ↓
genCode()
```

---

# Roadmap

Planned features:

- Learn Mode (step-by-step calculations)
- Auto Tuning Wizard
- Nichols Chart
- Monte Carlo Robustness
- Additional tuning methods
- More export targets

---

# License

MIT License.

Free to use, modify and distribute.

---

# Author

**DarkenAmber**

GitHub: https://github.com/DarkenAmber

If you find this project useful, consider supporting its development:

☕ Ko-fi: https://ko-fi.com/darkenamber

❤️ Patreon: https://www.patreon.com/cw/DarkenAmber
