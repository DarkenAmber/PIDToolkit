# Changelog

All notable changes to PID Toolkit are documented here.

---

## [1.0.0] — 2026-07-01

### Initial release

**Calculation**
- 6 tuning methods: Z-N OL, Z-N CL, CHR 0%, CHR 20%, ITAE (Servo/Regulator), Lambda/IMC (PI/PID)
- P / PI / PID controller type selector
- ITAE NaN protection: disabled when L/T > 5.41 (Servo) or > 6.24 (Regulator)
- Z-N CL returns null for invalid Ku ≤ 0 or Tu ≤ 0
- L/T ratio block with difficulty rating and method recommendation
- `safeL()` guard prevents division by zero at L = 0

**Simulation**
- Discrete FOPDT model with transport delay
- D on measurement — no derivative kick
- Conditional anti-windup — integrator holds when output saturated
- Output Min/Max limits from user settings
- Stability detector: overshoot > 300%, final value out of range, crossing count > 8

**Step Response graph**
- Oscilloscope-style animated scan (1500ms, requestAnimationFrame)
- Setpoint dashed line, ±5% settling band
- Peak marker with σ% annotation (appears after animation completes)
- Scanning dot during animation
- Live update on parameter change (400ms debounce)
- Save PNG

**Bode Plot**
- Animated gain (dB) and phase (°) curves
- Logarithmic frequency axis
- Phase Margin and Gain Margin — color-coded (PM < 30° red, GM < 6dB red)
- Save PNG

**Method comparison table**
- All 6 methods: Kp, Ki, Kd, Ti, Td, Overshoot
- Simulation cache — computed once at Calculate, not on every click
- Sort by Kp / Ki / Kd / Overshoot (click header)
- Click row to switch active method

**Code export — 4 platforms**
- Arduino: D on measurement, conditional anti-windup, `constrain()`
- ESP32 + FreeRTOS: `pidTask()`, `volatile` variables, `vTaskDelay`
- MicroPython: `class PID`, `compute(pv)`, `time.ticks_diff`
- IEC 61131-3 ST: typed `VAR` block, `LIMIT()`, works with Siemens / CODESYS / Schneider / Beckhoff

**D-filter option**
- First-order filter: `Tf = Kd / (Kp × N)`
- N range 2–50, default 10
- Adds to all 4 platforms when enabled

**Quick Presets**
- 🌡 Temperature: K=0.8, T=120s, L=15s
- ⚡ Pressure: K=1.2, T=5s, L=0.5s
- 💧 Level: K=1.0, T=30s, L=3s
- ⚙ DC Motor Speed: K=2.0, T=0.5s, L=0.05s
- ⚙ DC Motor Position: K=1.0, T=0.8s, L=0.1s
- ⚙ Servo: K=1.5, T=0.2s, L=0.02s
- ⚙ Conveyor/Geared: K=0.5, T=2.0s, L=0.3s

**Contextual warnings**
- D-term without filter → noise warning
- L/T > 0.5 → recommend Lambda/IMC
- L/T > 1 → critical delay, Smith Predictor suggested
- Z-N selected → commissioning advice
- T > 60s → slow process, windup risk
- T < 0.5s → fast plant, sample rate reminder
- Always → nonlinearity reminder

**UI / UX**
- DarkenAmber visual style (Space Mono + DM Sans)
- EN / RU language dropdown — full UI translation
- Calculate button pulse animation when parameters changed
- URL hash sharing — encode K/T/L/method in link
- Import / Export JSON
- PDF / Print layout
- localStorage persistence — all settings restored on reload
- ResizeObserver with 60ms debounce — no canvas resize loop
