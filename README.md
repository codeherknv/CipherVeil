# CipherVeil-Adaptive Multimodal Steganography Workbench

[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/backend-FastAPI-009688.svg)](https://fastapi.tiangolo.com/)
[![React 18](https://img.shields.io/badge/frontend-React%2018%20%7C%20TypeScript-61DAFB.svg)](https://reactjs.org/)
[![Vite](https://img.shields.io/badge/build-Vite-646CFF.svg)](https://vitejs.dev/)
[![Tests](https://img.shields.io/badge/tests-251%20passing-brightgreen.svg)]()
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An enterprise-grade, cross-modal steganographic framework that distributes encrypted payloads across heterogeneous carrier media (**Image**, **Audio**, and **Video**) using mathematical portfolio theory and convex optimization.

Unlike conventional single-media steganography, this system addresses the **Multimodal Trilemma** (Capacity vs. Distortion vs. Risk Concentration) by modeling payload allocation as a constrained quadratic optimization problem inspired by Markowitz Modern Portfolio Theory.

---

## 📑 Complete Academic Project Report

For a complete, publication-grade academic analysis (25 pages) including complete mathematical derivations, signal complexity formulas, full 144-trial benchmark tables, lossy codec stress tests, full-stack architecture, and professor defense scripts, refer to:
👉 **[`Adaptive_Multimodal_Steganography_Complete_Project_Report.pdf`](Adaptive_Multimodal_Steganography_Complete_Project_Report.pdf)**

---

## 🌟 Key Innovations & Capabilities

- **Multimodal Triad Engine:** Deconstructs, embeds, and reconstructs payloads across Image (PNG/BMP), Audio (WAV 16-bit PCM), and Video (MP4/AVI raw frames) carriers simultaneously.
- **Defense-in-Depth Cryptography:**
  - **Authenticated Encryption:** ChaCha20-Poly1305 AEAD with fresh 96-bit nonces.
  - **Key Derivation:** HKDF-SHA256 with 256-bit cryptographically secure salts.
  - **Error Correction:** Reed-Solomon $(N, K)$ forward error correction framing.
  - **Secret Sharing:** Shamir's $(k, n)$ threshold secret sharing for cryptographic share isolation.
- **Signal-Adaptive Complexity Profiling:**
  - **Image:** Sobel gradient magnitude, Laplacian edge variance, and GLCM texture homogeneity.
  - **Audio:** Spectral entropy and Zero-Crossing Rate (ZCR).
  - **Video:** Temporal inter-frame motion differential (MSE) and spatial macroblock variance.
- **8 Mathematical Allocation Paradigms:** Supports baseline, heuristic, theoretical, and convex optimization strategies.
- **Exact Integer Conservation Engine:** Guarantees $\sum b_i = B$ with zero capacity violations via Bound Clamping and Largest Remainder Rounding.
- **Interactive Multi-Strategy Comparison Matrix:** Live real-time benchmarking panel evaluating all 8 strategies simultaneously on user carriers with automatic concentration warnings.
- **Rigorous 144-Trial Benchmark Evaluation:** Evaluated across 4 operational scenarios with independent $\chi^2$ detectability testing and lossy codec stress-testing.

---

## 📐 The 8 Allocation Paradigms

| # | Strategy | Paradigm | Description |
|---|---|---|---|
| 1 | **Fixed Baseline** | Uniform | Equal distribution with capacity water-filling. |
| 2 | **Capacity-Proportional** | Linear Heuristic | Allocates bits strictly proportional to available capacity ($b_i \propto C_i$). |
| 3 | **Adaptive** | Signal-Weighted | Jointly weights carrier capacity and signal entropy/complexity. |
| 4 | **Square-Root-Law** | Asymptotic Steganography | Allocates proportional to Ker's square root of capacity ($b_i \propto \sqrt{C_i}$). |
| 5 | **Random Key-Seeded** | Stochastic | Cryptographic PRNG split (seeded by message key) respecting capacities. |
| 6 | **Max-Complexity Greedy** | Greedy Heuristic | Saturates highest-complexity carriers first to maximize edge masking. |
| 7 | **Minimax Risk** | Conservative Optimization | Minimizes the worst-case carrier risk: $\min_{\mathbf{b}} \max_i (\sigma_i^2 b_i^2)$. |
| 8 | **Portfolio (Markowitz)** | Convex Optimization (QP) | Solves mean-variance trade-off via Sequential Least Squares Programming (SLSQP). |

### Mathematical Formulation of Portfolio Allocation

The Markowitz payload allocation solves the following bounded quadratic program:

$$\min_{\mathbf{b}} \quad \frac{1}{2} \mathbf{b}^T \boldsymbol{\Sigma} \mathbf{b} - \lambda \mathbf{w}^T \mathbf{b}$$

$$\text{subject to} \quad \sum_{i=1}^3 b_i = B, \quad 0 \le b_i \le C_i \quad \forall i \in \{I, A, V\}$$

- $\mathbf{b} = [b_I, b_A, b_V]^T$: Allocated payload bytes across Image, Audio, and Video.
- $\boldsymbol{\Sigma}$: Risk covariance matrix capturing carrier vulnerability, noise covariance, and cross-carrier correlations.
- $\mathbf{w}$: Normalized capacity/complexity utility vector.
- $\lambda \in [0, 1]$: Risk-tolerance parameter controlling the trade-off along the Efficient Frontier.

---

## 📊 Empirical Evaluation & Benchmark Results

Evaluated across **144 systematic trials** over 4 operational scenarios (*Balanced*, *Image-Dominant*, *Audio-Dominant*, *Video-Dominant*):

```
                        EFFICIENT FRONTIER (Risk vs. Throughput)
   Modeled Risk Proxy (b^T Σ b)
        ▲
   High │  [λ=1.00 Capacity-Proportional Target]
        │         •
        │          •
        │            • [λ=0.50 Balanced Portfolio]
        │              •
    Low │                • [λ=0.00 Minimum Variance]
        └────────────────────────────────────────► Capacity-Weighted Throughput (w^T b)
```

### Key Findings
1. **Markowitz Optimization ($\lambda=0.50$):** Consistently balances imperceptibility across modalities, achieving $>53\text{ dB}$ Image PSNR, $>54\text{ dB}$ Audio SNR, and $>58\text{ dB}$ Video PSNR under typical loads.
2. **Independent Detectability:** Evaluated via image $\chi^2$ statistical analysis ($p$-values $>0.999$, indicating low first-order statistical anomaly).
3. **Operational Risks of Heuristics:**
   - *Max-Complexity Greedy* and *Random Key-Seeded* frequently exceed the $>90\%$ concentration threshold, creating severe detection hotspots in a single carrier.
   - *Capacity-Proportional* serves as a strong, predictable baseline for large homogeneous channels.
4. **Channel Robustness Testing:** Lossy re-compression (JPEG $Q=75$, MP3 $128\text{ kbps}$, H.264 $\text{CRF}=23$) degrades LSB spatial carriers ($\text{BER} \approx 45\text{--}50\%$). The ChaCha20-Poly1305 MAC tag detects tamper/corruption and cleanly refuses decryption of corrupted data.

---

## 🏗️ System Architecture

```
                                 +-----------------------+
                                 | Secret Message Input  |
                                 +-----------+-----------+
                                             |
                                    [HKDF-SHA256 / AES]
                                             v
                              +-----------------------------+
                              |   ChaCha20-Poly1305 AEAD    |
                              |   + Reed-Solomon Framing   |
                              +--------------+--------------+
                                             |
                 +---------------------------+---------------------------+
                 | (Carrier Analysis)                                    |
                 v                                                       v
+---------------------------------+                     +---------------------------------+
|      Carrier Triad Upload       |                     |   Mathematical Strategy Selector|
|  - Image: Sobel / GLCM Entropy  |                     |  - 8 Strategies (Fixed -> QP)   |
|  - Audio: Spectral Entropy / ZCR|                     |  - Exact Integer Conservation   |
|  - Video: Temporal Motion MSE   |                     |  - SLSQP Convex Optimizer       |
+----------------+----------------+                     +----------------+----------------+
                 |                                                       |
                 +---------------------------+---------------------------+
                                             v
                              +-----------------------------+
                              |   Payload Allocation Vector |
                              |      b = [b_I, b_A, b_V]    |
                              +--------------+--------------+
                                             |
                 +---------------------------+---------------------------+
                 | (Adaptive LSB Embedding)  |                           |
                 v                           v                           v
        +-----------------+         +-----------------+         +-----------------+
        |   Stego Image   |         |   Stego Audio   |         |   Stego Video   |
        |  (PNG / BMP)    |         |  (WAV 16-bit)   |         |   (MP4 / AVI)   |
        +-----------------+         +-----------------+         +-----------------+
```

---

## 💻 Tech Stack

- **Backend:** Python 3.10+, FastAPI, NumPy, SciPy (SLSQP optimization), OpenCV, SoundFile, Cryptography, Reed-Solomon.
- **Frontend:** React 18, TypeScript, Vite, Tailwind CSS, Lucide React, Recharts (interactive comparative charts & radar).
- **Testing & Verification:** Pytest (**251 passing unit and integration tests**).

---

## 🚀 Quick Start Guide

### Prerequisites
- Python 3.10+
- Node.js 18+ and npm
- (Optional) Google Chrome installed (for automated PDF report generation)

### 1. Clone the Repository
```bash
git clone https://github.com/codeherknv/Adaptive-Multimodal-Steganography.git
cd Adaptive-Multimodal-Steganography
```

### 2. Backend Setup
```bash
# Navigate to backend and create virtual environment
cd backend
python -m venv venv

# Activate virtual environment
# Windows (PowerShell):
.\venv\Scripts\Activate.ps1
# Linux/macOS:
source venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Run test suite to verify installation (251 tests)
pytest tests/ -v

# Start FastAPI server (runs on http://localhost:8000)
uvicorn app.main:app --reload --host 127.0.0.1 --port 8000
```
- Interactive API Documentation (Swagger UI): `http://127.0.0.1:8000/docs`
- Health check: `http://127.0.0.1:8000/api/health`

### 3. Frontend Setup
```bash
# In a new terminal, navigate to frontend
cd frontend

# Install dependencies
npm install

# Start Vite development server (runs on http://localhost:5173)
npm run dev
```

Open your browser and navigate to `http://localhost:5173`.

---

## 🧪 Running the Benchmark Suite

To reproduce the 144-trial evaluation matrix and generate the analytical charts:

```powershell
# From the project root with the backend venv active:
$env:PYTHONPATH='backend'
python scripts/run_phase10_benchmarks.py
```

Generated plots will be saved in `results/figures/`:
- `phase10_efficient_frontier.png`
- `phase10_rate_distortion_curves.png`
- `phase10_allocation_shares.png`
- `phase10_detectability_comparison.png`
- `phase10_ablation_study.png`

---

## 📁 Repository Structure

```text
├── Adaptive_Multimodal_Steganography_Complete_Project_Report.pdf  # 25-page comprehensive academic PDF report
├── backend/
│   ├── app/
│   │   ├── api/routes.py                # FastAPI REST endpoints (including /api/multimodal/compare)
│   │   ├── core/
│   │   │   ├── allocator.py             # 8 Allocation strategies & integer conservation
│   │   │   ├── crypto.py                # ChaCha20-Poly1305, HKDF, Reed-Solomon
│   │   │   ├── profiler.py              # Spatial, spectral, and temporal feature extraction
│   │   │   ├── engine.py                # Multimodal Triad orchestrator
│   │   │   ├── image_stego.py           # Spatial LSB image embedding & extraction
│   │   │   ├── audio_stego.py           # Linear PCM WAV sample LSB embedding
│   │   │   └── video_stego.py           # Multi-frame spatial LSB embedding
│   │   └── schemas.py                   # Pydantic v2 schemas
│   ├── tests/                           # 251 Pytest test suite
│   └── requirements.txt
├── frontend/
│   ├── src/
│   │   ├── pages/MultimodalTriad.tsx    # 8-Card strategy selector UI & embed/extract workflow
│   │   ├── components/
│   │   │   └── StrategyComparisonPanel.tsx # Live 8-strategy comparison table & Recharts
│   └── package.json
├── results/
│   ├── figures/                         # High-res benchmark plots
│   ├── phase10_benchmark_report.md      # 144-trial evaluation report
│   └── phase10_benchmark_summary.csv    # Raw benchmark trial data
└── scripts/
    └── run_phase10_benchmarks.py        # Benchmark automation script
```

---

## ⚖️ Scientific Integrity & Limitations

- **Modeled Risk Proxy:** The metric $\mathbf{b}^T \boldsymbol{\Sigma} \mathbf{b}$ represents the optimizer's internal quadratic loss objective based on spatial/spectral complexity, not an empirical neural network detectability score.
- **Detector Scope:** Independent empirical detectability testing was conducted using image $\chi^2$ sample analysis. Deep learning-based steganalyzers (e.g., SRNet) are not included in this release.
- **Channel Vulnerability:** LSB spatial embedding is designed for lossless channels; distribution over lossy channels (e.g., social media re-compression) requires frequency-domain embedding (DCT/DWT).

---

## 📜 License

This project is open-source and licensed under the [MIT License](LICENSE).
