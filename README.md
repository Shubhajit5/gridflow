<div align="center">

  # ⚡ GridFlow: Smart Grid Power Flow & Substation Balancer

  **An interactive HTML5 Canvas power grid simulation and SCADA monitoring tool featuring real-time power flow distribution, frequency stabilization, and interactive line-tripping mechanics.**

  [![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
  [![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)](https://developer.mozilla.org/en-US/docs/Web/JavaScript)
  [![Canvas API](https://img.shields.io/badge/Canvas_API-000000?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API)
  [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](LICENSE)

</div>

---

## 📌 Overview

**GridFlow** is an interactive, browser-based power system simulator and SCADA monitoring dashboard. It models regional electrical networks comprising thermal/solar generators, main hub substations, and urban/industrial consumer loads. The simulation calculates real-time power flow (MW), monitors grid frequency deviation ($Hz$), and allows operators to interactively stress-test network stability by injecting peak load surges or tripping high-voltage transmission lines.

---

## ✨ Key Features

* **⚡ Real-Time Power Flow Calculation:** Proportional load distribution across transmission lines with live capacity tracking and warning indicators.
* **🎛️ Interactive Line Tripping & Restoration:** Click directly on any transmission line on the canvas to manually trip, damage, or restore it and observe dynamic grid routing changes.
* **📈 Frequency Stability Monitoring:** Computes generation-load imbalances in real time, tracking grid frequency ($50.00\,Hz$ baseline) and switching system status between `SECURE` and `UNSTABLE (OVERLOAD)`.
* **💥 Peak Load Surge Injection:** Instantly stress-test the grid by injecting sudden consumer demand spikes across urban and industrial zones.
* **📊 SCADA Telemetry & Logs:** Live timestamped event console logging operator actions, line faults, and stability warnings.

---

## 🛠️ Tech Stack

* **Frontend:** Vanilla HTML5, CSS3
* **Rendering Engine:** HTML5 2D Canvas API
* **Simulation Logic:** Vanilla JavaScript (ES6+ Vector Geometry, Proportional Power Flow Algorithms)

---

## 🏗️ Grid Simulation Architecture

The SCADA engine continuously evaluates generation-to-load equilibrium and transmission line constraints:

```mermaid
graph TD;
    A[Monitor Total Generation & Consumer Load] --> B[Calculate Supply-Demand Imbalance];
    B --> C[Compute Grid Frequency Deviation Hz];
    C --> D{Is Frequency within 49.0 - 51.0 Hz?};
    D -- Yes --> E[System Status: SECURE];
    D -- No --> F[System Status: UNSTABLE OVERLOAD];
    E --> G[Update Proportional Power Flow on Active Lines];
    F --> G;
