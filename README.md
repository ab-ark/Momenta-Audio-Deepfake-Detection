# 🔍 Top 3 Audio Deepfake Detection Models

This section outlines the three most promising models for real-time audio deepfake detection, particularly suited for detecting AI-generated human speech in real conversations.

---

## ✅ 1. RawNet2

- **📌 Key Technical Innovation**:
  - End-to-end model operating directly on **raw audio waveforms**
  - Uses deep **residual CNN blocks** followed by **GRU layers**
  - Joint optimization of **speaker verification** and **anti-spoofing**

- **📈 Performance**:
  - EER: ~0.24% on ASVspoof 2019 LA
  - EER: **1.12%**, t-DCF: **0.033** (ASVspoof 2021 LA)

- **🚀 Why Promising**:
  - No need for hand-crafted features (e.g., MFCCs or spectrograms)
  - Strong **generalization** against unknown attacks
  - **Lightweight architecture** supports near real-time inference
  - Good baseline and reproducibility

- **⚠️ Limitations**:
  - Raw audio requires **careful normalization**
  - Sensitive to **noisy/uncontrolled environments** (mitigable via augmentation or preprocessing)

- **📦 Dataset**: [ASVspoof 2019 LA](https://datashare.ed.ac.uk/handle/10283/3336)
- **🔗 Repo**: [github.com/eurecom-asp/rawnet2-antispoofing](https://github.com/eurecom-asp/rawnet2-antispoofing)

---

## ✅ 2. AASIST (Audio Anti-Spoofing using Integrated Spectro-Temporal features)

- **📌 Key Technical Innovation**:
  - Leverages **Spectro-Temporal Graph Attention Networks (GATs)**
  - Captures both **local time-frequency features** and **global structure**
  - Fuses topological and spectral information for improved robustness

- **📈 Performance**:
  - EER: **0.83%**, t-DCF: **0.028** (ASVspoof 2021 LA)

- **🚀 Why Promising**:
  - Robust against a wide range of spoofing techniques, including **unseen attacks**
  - Attention-based architecture supports **better generalization**
  - Optimizable for **online detection** scenarios

- **⚠️ Limitations**:
  - Requires **spectrogram preprocessing**
  - **Heavier model** than RawNet2, less ideal for edge devices

- **📦 Dataset**: [ASVspoof 2021 LA](https://datashare.ed.ac.uk/handle/10283/3336)
- **🔗 Repo**: [github.com/clovaai/aasist](https://github.com/clovaai/aasist)

---

## ✅ 3. LFCC-GAN + LCNN

- **📌 Key Technical Innovation**:
  - Uses **Linear Frequency Cepstral Coefficients (LFCC)** as input
  - Employs a **Light CNN (LCNN)** with **GAN-style adversarial training**
  - Designed to boost generalization across attack types

- **📈 Performance**:
  - Competitive results on ASVspoof 2019 and 2021 datasets
  - EER and t-DCF values comparable to SOTA models (exact values vary per run/dataset)

- **🚀 Why Promising**:
  - **GAN-based training** helps detect subtle artifacts
  - Especially useful for **real conversations** with nuanced manipulation
  - LFCC features are **less overfit-prone** than spectrograms

- **⚠️ Limitations**:
  - **Training instability** due to GAN architecture
  - Heavier and more complex to tune than RawNet2
  - Less suitable for low-latency, on-device detection

- **📦 Dataset**: [ASVspoof 2019/2021](https://datashare.ed.ac.uk/handle/10283/3336)
- **🔗 Repo**: Likely integrated in various academic implementations (custom integration required)

---

## 🏆 **Top Pick: RawNet2**

RawNet2 stands out due to its:

- Simplicity (works on raw audio directly)
- Speed (lightweight enough for near real-time)
- Strong performance even on unknown attacks
- Ease of integration for production or online systems

It’s a solid foundation for prototyping a real-time audio deepfake detection system with room for further enhancement and deployment optimization.

---
