# PID Toolkit

**Browser-based PID controller tuning tool.**  
One HTML file — offline, no dependencies, no backend.

![DarkenAmber](https://img.shields.io/badge/style-DarkenAmber-E8A020)
![License](https://img.shields.io/badge/license-MIT-green)
![Version](https://img.shields.io/badge/version-1.1-blue)

**[▶ Live Demo](https://darkenamber.github.io/PIDToolkit/)**

---

## What it does

Enter your plant model (K, T, L) and get:

- **PID coefficients** — 6 tuning methods calculated simultaneously
- **Step response** — animated oscilloscope-style graph with live update
- **Bode Plot** — gain and phase margins, animated
- **Method comparison table** — all 6 methods side by side, sortable
- **Code export** — ready-to-paste code for 4 platforms
- **Contextual warnings** — real-world advice about noise, delay, and saturation

---

## Tuning methods

| Method | Type | Input |
|--------|------|-------|
| Ziegler-Nichols OL | Classic | K, T, L |
| Ziegler-Nichols CL | Ultimate gain | Ku, Tu |
| CHR 0% overshoot | Conservative | K, T, L |
| CHR 20% overshoot | Moderate | K, T, L |
| ITAE | Optimal integral criterion | K, T, L |
| Lambda / IMC | Model-based | K, T, L + λ |

---

## Code export

All platforms include **D on measurement** (no derivative kick) and **conditional anti-windup**:

- **Arduino** — `computePID()` with optional D-filter
- **ESP32 + FreeRTOS** — `pidTask()` with `vTaskDelay`
- **MicroPython** — `class PID` with `compute(pv)`
- **IEC 61131-3 ST** — Siemens, CODESYS, Schneider, Beckhoff

---

## Quick presets

| Preset | K | T | L |
|--------|---|---|---|
| 🌡 Temperature | 0.8 | 120s | 15s |
| ⚡ Pressure | 1.2 | 5s | 0.5s |
| 💧 Level | 1.0 | 30s | 3s |
| ⚙ DC Motor Speed | 2.0 | 0.5s | 0.05s |
| ⚙ DC Motor Position | 1.0 | 0.8s | 0.1s |
| ⚙ Servo | 1.5 | 0.2s | 0.02s |
| ⚙ Conveyor/Geared | 0.5 | 2.0s | 0.3s |

---

## Features

- Oscilloscope-style animated step response
- Animated Bode Plot with Phase Margin and Gain Margin
- Live parameter update — graph and code update automatically (400ms debounce)
- ⏭ Skip animation button
- Method comparison table — sortable by Kp / Ki / Kd / Overshoot
- Collapsible sections — Method Comparison and Code Export
- D-term filter (first-order, Tf = Kd / (Kp × N))
- Output limits with conditional anti-windup
- Contextual warnings (noise, large delay, Z-N aggressiveness, nonlinearity)
- 🌙 Dark / ☀️ Light theme toggle
- URL hash sharing — send parameters in one link
- EN / RU language switch — full UI translation
- Reset settings / Clear all localStorage
- Import / Export JSON
- PDF / Print layout
- Fully offline

---

## Usage

1. Download `index.html`
2. Open in any browser
3. Enter K, T, L or pick a preset
4. Press **Calculate**
5. Copy the generated code for your platform

---

## Target audience

- Arduino / ESP32 developers
- Process control engineers (SCADA, IEC ST)
- Automation students
- Anyone who needs PID coefficients fast without MATLAB

---

## Architecture

Single HTML file — intentionally. No build step, no npm, no CDN.  
All logic in vanilla JS: `calcAll()` → `simulate()` → `metrics()` → `renderCompTable()` → `genCode()`.

---

## License

MIT — use freely, attribution appreciated.

---

## Author

[DarkenAmber](https://github.com/DarkenAmber)  
Support the project: [Ko-fi](https://ko-fi.com/darkenamber) · [Patreon](https://www.patreon.com/cw/DarkenAmber)
