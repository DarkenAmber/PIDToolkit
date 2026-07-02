# PID Toolkit

**Browser-based PID controller tuning tool.**  
One HTML file — offline, no dependencies, no backend.

🌐 **Live Demo:** https://darkenamber.github.io/PIDToolkit/

📂 **GitHub:** https://github.com/DarkenAmber/PIDToolkit

![DarkenAmber](https://img.shields.io/badge/style-DarkenAmber-E8A020)
![License](https://img.shields.io/badge/license-MIT-green)
![Version](https://img.shields.io/badge/version-1.0-blue)

---

## What it does

Enter your plant model (**K**, **T**, **L**) and the toolkit instantly provides:

- **PID coefficients** calculated using multiple tuning methods
- **Animated step response** (oscilloscope-style)
- **Bode plot** with Phase Margin and Gain Margin
- **Method comparison table** (sortable)
- **Code generation** for multiple platforms
- **Engineering warnings** about delay, noise and saturation

---

## Tuning methods

| Method | Type | Input |
|--------|------|-------|
| Ziegler–Nichols (Open Loop) | Classic | K, T, L |
| Ziegler–Nichols (Closed Loop) | Ultimate gain | Ku, Tu |
| CHR (0% Overshoot) | Conservative | K, T, L |
| CHR (20% Overshoot) | Moderate | K, T, L |
| ITAE Servo | Optimal integral criterion | K, T, L |
| ITAE Regulator | Optimal disturbance rejection | K, T, L |
| Lambda / IMC | Model-based | K, T, L + λ |

---

## Code generation

Generated implementations include **D on Measurement** (eliminates derivative kick) and **Conditional Anti-Windup**.

Supported platforms:

- Arduino
- ESP32 + FreeRTOS
- MicroPython
- IEC 61131-3 Structured Text (Siemens, CODESYS, Schneider, Beckhoff)

---

## Quick presets

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

## Features

- Animated oscilloscope-style step response
- Animated Bode plot with Phase Margin and Gain Margin
- Live parameter updates
- Comparison table with sortable Kp, Ki and Kd
- First-order derivative filter
- Conditional anti-windup
- URL sharing via hash parameters
- EN / RU interface
- Import / Export JSON
- PDF-friendly print layout
- Fully offline operation

---

## Usage

1. Download `pid-toolkit.html`
2. Open it in any modern browser.
3. Enter **K**, **T** and **L**, or select a preset.
4. Compare tuning methods.
5. Simulate the response.
6. Export the generated controller code.

---

## Target audience

- Arduino / ESP32 developers
- Control and automation engineers
- SCADA / PLC programmers
- Engineering students
- Anyone who needs quick PID tuning without installing MATLAB or other software

---

## Architecture

A single HTML file by design.

No build step.  
No npm.  
No framework.  
No backend.

Core flow:

`calcAll() → simulate() → metrics() → renderCompTable() → genCode()`

---

## License

MIT — free to use and modify.

---

## Author

**DarkenAmber**

GitHub: https://github.com/DarkenAmber

If you find the project useful, consider supporting its development:

- Ko-fi: https://ko-fi.com/darkenamber
- Patreon: https://www.patreon.com/cw/DarkenAmber
