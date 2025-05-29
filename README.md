# ⚡ HyBridge – Optimising Mixed EV + H₂V Infrastructure for Last-Mile Delivery  
Integrated Agent-Based Model + Genetic Algorithm + LLM Decision Layer

<p align="center">
  <img src="docs/img/ui-dashboard.png" width="70%" alt="HyBridge AnyLogic dashboard showing Sheffield map, KPI cards and controls">
</p>

**HyBridge** models a dual-fuel parcel fleet (battery-electric vans + hydrogen fuel-cell vans) operating across Sheffield, UK.  
It couples an *AnyLogic* agent-based simulation, a *Genetic Algorithm* refuelling-station optimiser, and a *large-language-model* assistant that answers planners’ questions in plain English.

> The full 125-page thesis is **not** in this repo.  
> A 4-page extended abstract and all key code, data and figures are included; email me if you need the dissertation PDF.

---

## 🏆 Headline Results (5-day city-wide simulation)

| KPI | EV-only baseline | Optimised 80 % EV / 20 % H₂V | Δ |
|-----|-----------------|--------------------------------|---|
|Average delivery cycle time| **1.63 h**| **1.26 h** | −22.8 %:contentReference[oaicite:1]{index=1}|
|EV queuing wait (avg)| **213 min**| **140 min** | −34.4 %:contentReference[oaicite:3]{index=3}|
|Infeasible trips (range)| 3180| 2715 | −14.6 %:contentReference[oaicite:5]{index=5}|
|Delivery completion| 98.90 %| 98.91 %|≈ identical:contentReference[oaicite:7]{index=7}|
|Grid electricity used| 269 MWh| 211 MWh| −21.9 %:contentReference[oaicite:9]{index=9}|
|CO₂ saved vs diesel| 51.9 t| 48.6 t| −6.4 %*:contentReference[oaicite:11]{index=11}|

\* Drop is due to grey-hydrogen emissions; sourcing green H₂ reverses this trade-off.

---

## 📊 Visual Storyboard

| Visual | What it shows |
|--------|---------------|
|<img src="docs/img/scenario-compare-bars.png" width="320">|Side-by-side cost & CO₂ bars – Optimised beats Baseline on both.|
|<img src="docs/img/sensitivity-tornado.png" width="320">|Tornado plot – electricity tariff swings NPV the most, hydrogen price is next.|
|<img src="docs/img/convergence-curve.png" width="340">|GA convergence – objective plateaus after ≈120 iterations (best = 0.907 h).|

---

## 📁 Repository Map



hybridge/
├─ abstract/            # 4-page PDF summary
├─ model/               # AnyLogic .alp project + CSV inputs
├─ notebooks/           # Jupyter KPI & plot scripts
├─ docs/
│   ├─ img/             # ← put the four .png files here
│   ├─ Results.docx
│   └─ Sensitivity Analysis.docx
├─ README.md
├─ LICENSE              # MIT
└─ .gitignore



---

## 🚀 Quick Start

bash
git clone https://github.com/<you>/hybridge.git
cd hybridge

# open the model
# AnyLogic 8.7+ ➜ File ▸ Open ▸ model/HyBridge.alp

# (optional) regenerate plots
pip install -r notebooks/requirements.txt
jupyter nbconvert --execute notebooks/01_postprocess.ipynb


---

## 🔍 Data & Assumptions

* **Fleet:** 600 vans → 480 EV, 120 H₂V.
* **Candidate sites:** 71 existing public EV chargers; GA adds **1 H₂ pump each**.
* **Refuel triggers:** EV ≤10 % SoC, H₂V ≤50 % tank (from optimisation).
* **Energy factors:** UK grid = 0.182 kg CO₂/kWh, grey H₂ = 10 kg CO₂/kg.
* **Study window:** 5 simulated days, 1-min time-step.

Full parameter table lives in `abstract/HyBridge_Abstract.pdf`.

---

## 🤖 LLM Assistant

The simulation streams KPI logs to an OpenAI GPT-4o endpoint.  Ask:

```text
"How much electricity did the fleet save after optimisation?"
```

…and the assistant returns a grounded answer citing the exact log lines – no extra BI tooling needed.

---

## ✍️ Citing HyBridge

bibtex
@article{AlKuhali2025HyBridge,
  title  = {HyBridge: Mixed Battery–Electric and Hydrogen Infrastructure Optimisation for Urban Last-Mile Delivery},
  author = {Mohammed Hashem Al-Kuhali},

  year   = {2025}
}

---

## 🛡 License

Released under the **MIT licence** – free for academic & commercial use.

---

<p align="center"><em>Less time • Less fuel • Smarter dual-energy logistics.</em></p>
```

