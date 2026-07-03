# Changelog

---

## [1.1.0] — 2026-07-03

### UI / UX
- Added 🌙 Dark / ☀️ Light theme toggle — saved to localStorage
- Light theme: warm gray palette (#CEC8BE base), not plain white
- Canvas graphs (Step Response, Bode Plot) adapt to current theme via `themeColors()`
- Warning blocks and ✓ Stable badge adapt to theme on toggle
- Increased base font size 14px → 15px for better readability
- Sidebar narrowed 265px → 240px to fit 1080p screens
- Added ⏭ Skip button — stops animation and shows final graph immediately
- Collapsible sections: **Method Comparison ▾** and **Code Export ▾** — click header to toggle
- Collapse state saved to localStorage
- Calculate button pulses (orange glow) when parameters have changed since last calculation
- `setCalcDirty()` / `setCalcClean()` — triggered on field input, preset load, mode switch

### Presets
- Expanded from 4 to 7 presets
- Added DC Motor Speed (K=2.0, T=0.5s, L=0.05s)
- Added DC Motor Position (K=1.0, T=0.8s, L=0.1s)
- Added Servo (K=1.5, T=0.2s, L=0.02s)
- Added Conveyor/Geared (K=0.5, T=2.0s, L=0.3s)
- Motor presets grouped under ⚙ Motor section in sidebar
- Tooltip on each preset button shows K/T/L values

### Contextual warnings
- Added after Calculate, re-rendered on language switch and theme change
- D-term without filter → sensor noise warning
- L/T > 0.5 → recommend Lambda/IMC
- L/T > 1 → critical delay, suggest Smith Predictor
- Z-N selected → commissioning advice (reduce Kp 20–30%)
- T > 60s → slow process, windup risk
- T < 0.5s → fast plant, sample rate reminder
- Always → nonlinearity reminder

### Localization
- Full EN/RU translation — all UI elements including warnings, ratio block, graph titles, tabs
- `applyLang()` iterates all `[data-i18n]` elements
- Language switch triggers: `applyLang()` + `renderCompTable()` + `renderRatioBlock()` + `checkPIDWarnings()`
- Technical terms preserved in both languages: Kp, Ki, Kd, PID, Z-N, ITAE, FOPDT, Lambda

### Data management
- Added ↺ Reset settings — resets all parameters to defaults, clears graph
- Added ⛔ Clear all — clears entire localStorage, confirm dialog
- Both buttons translate with language switch

### Other
- URL hash sharing — ⤴ Share button encodes K/T/L/method to link
- `loadFromURL()` on page load restores shared parameters
- Social links in header: 🐙 GitHub, ❤️ Patreon, ☕ Ko-fi
- PDF / Print layout — hides sidebar, redraws graph before printing

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
- Peak marker with σ% annotation
- Live update on parameter change (400ms debounce)
- Save PNG

**Bode Plot**
- Animated gain (dB) and phase (°) curves
- Logarithmic frequency axis
- Phase Margin and Gain Margin — color-coded
- Save PNG

**Method comparison table**
- All 6 methods: Kp, Ki, Kd, Ti, Td, Overshoot
- Simulation cache
- Sort by Kp / Ki / Kd / Overshoot

**Code export — 4 platforms**
- Arduino, ESP32 + FreeRTOS, MicroPython, IEC 61131-3 ST
- D on measurement + conditional anti-windup on all platforms
- Optional D-filter: Tf = Kd / (Kp × N)

**Quick Presets (4)**
- Temperature, Pressure, Level, Motor Speed

**UI**
- DarkenAmber visual style (Space Mono + DM Sans)
- EN / RU language dropdown
- Import / Export JSON
- localStorage persistence
