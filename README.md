# Audio Deepfake Detection - RawNet2 Implementation

## 👋 Welcome!

Thanks for checking out this implementation of a deepfake audio detection system! This repository was created as part of a take-home assessment for Momenta, focusing on real-world application of deepfake detection techniques using state-of-the-art methods.

The model implemented here is based on **RawNet2**, a convolutional recurrent neural network architecture specifically designed for speaker verification and spoofing detection. The goal of this project was to explore its effectiveness on the **ASVspoof2019** Logical Access (LA) dataset.

---

## 🚀 Overview

This project implements a mini version of RawNet2 to:
- Load and preprocess raw audio `.flac` files
- Use a subset of the ASVspoof2019 LA dataset to reduce training time
- Run a small-scale training loop for deepfake classification

---

## 🛠 Project Structure

```
├── LA_subset/                        # Mini subset of ASVspoof2019-LA dataset
│   ├── ASVspoof2019_LA_cm_protocols/  # Protocol files (train, dev, eval)
│   ├── ASVspoof2019_LA_train/flac     # Training audio samples
│   ├── ASVspoof2019_LA_dev/flac       # Dev audio samples
│   └── ASVspoof2019_LA_eval/flac      # Evaluation audio samples
├── main.py                           # Training + evaluation script
├── model.py                          # RawNet2 model definition
├── data_utils_LA.py                  # Dataset loading and preprocessing
├── model_config_RawNet2.yaml         # RawNet2 model config
├── requirements.txt                  # Python dependencies
└── README.md                         # This file
```

---

## 💻 Setup Instructions

### 1. Clone the Repo
```bash
git clone https://github.com/ab-ark/Momenta-Audio-Deepfake-Detection
cd Momenta-Audio-Deepfake-Detection
cd rawnet2-antispoofing
```

### 2. Create and Activate Environment
```bash
python3 -m venv venv
source venv/bin/activate  # For Linux/Mac
# OR
venv\Scripts\activate     # For Windows
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Dataset Setup
Place your subset of the ASVspoof2019-LA dataset under a folder named `LA_subset` in the root of the repo. Structure it as shown above.

You can also create a subset manually by copying a few `.flac` files from the official dataset into the respective `train`, `dev`, and `eval` folders and ensuring the protocol files list only those.

---

## 🧪 Usage Guide

### ✅ Train the Model
```bash
python main.py \
  --batch_size 4 \
  --num_epochs 2 \
  --comment "mini_test" \
  --features Raw_audio \
  --database_path LA_subset \
  --protocols_path LA_subset/ASVspoof2019_LA_cm_protocols
```

You should see logs like:
```

0 - 0.27 - 88.00 - 0.00
```
![alt text](image.png)
### 📁 Output Files
- `models/` — Saved checkpoints
- `logs/` — TensorBoard logs
- `cache_*.npy` — Preprocessed audio cache files

To visualize training:
```bash
tensorboard --logdir logs/
```

---

## 🧠 Model Highlights

- **RawNet2** architecture combines sinc-based convolution layers and GRU for temporal modeling.
- End-to-end learning directly from raw waveform
- Lightweight config: Reduced number of samples for fast experimentation

---

## 📝 Notes

This repo is a **lightweight proof-of-concept**, created to demonstrate:
- Familiarity with audio deepfake datasets
- Ability to modify and run an existing deepfake detection pipeline
- Writing clean, reproducible ML code for real-world use

---

## 🤔 Gotchas

- Ensure `.flac` files listed in protocols actually exist
- Paths must match WSL or local file system structure correctly
- If training accuracy is high but dev accuracy is 0, try increasing `sample_size` or check for imbalance in `dev` protocol

---

## 📬 Contact
For questions or collaboration, feel free to reach out at `yourname@domain.com` or through GitHub issues.

---

Good luck and happy experimenting! 🚀

