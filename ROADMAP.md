# Roadmap

## v1.0 — Released ✅

Core tuning engine, 6 methods, animated graphs, 4-platform code export, EN/RU, presets, contextual warnings.  
See [CHANGELOG.md](CHANGELOG.md) for full details.

---

## v2.0 — In progress

### 1. Learn Mode ⭐ priority
Show the formula with substituted numbers directly under each KPI card.

```
Kp = 1.2 × T / (K × L)
   = 1.2 × 10 / (1.0 × 2.0)
   = 6.000
```

No other online PID calculator does this. Aimed at students and engineers who want to understand the math, not just get numbers.

### 2. Auto Tuning Wizard
User picks plant type → tool recommends the best method with explanation.

```
What kind of process?
○ Temperature / Slow thermal
○ Flow / Pressure (fast)
○ Level
○ Motor / Servo
↓
Recommended: Lambda/IMC
Why: large dead time (L/T = 0.6), Z-N will overshoot heavily
```

### 3. Nichols Chart
Completes the frequency-domain trio alongside Bode Plot.  
Analytical calculation from the same open-loop transfer function — no extra plant data needed.

### 4. Monte Carlo Robustness
Run N simulations with randomized plant parameters (K ±20%, T ±15%, L ±10%).  
Display the envelope of possible responses on the step response graph.  
Shows how robust the tuning is to real-world plant variation.

---

## v3.0 — Planned

- Feed Forward term
- Cascade PID (inner + outer loop)
- Relay Auto-Tuning (find Ku/Tu automatically from relay experiment)
- Gain Scheduling
- SOPDT plant model (second order)
- CSV import → identify K/T/L from step experiment data
- Siemens SCL export
- CODESYS export (separate template)
- Nyquist Plot
- Root Locus

---

## Community ideas

Suggestions from engineers after v1.0 launch:
- SVG export (in addition to PNG)
- Structured PDF report (plant + method + graph + code in one document)
- MATLAB / Simulink comparison mode

---

## Not planned

- SaaS / cloud version — single-file offline architecture is a core constraint, not a limitation
- Mobile app — Android considered, iOS not currently possible
- Backend / API — intentionally no server dependency
