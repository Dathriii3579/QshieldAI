
The result files in `results/` are the exact files generated during our evaluation and used to produce all tables and figures in the paper. The figures in `figures/` are the exact PDFs included in the paper.

---

## How to Run

Everything runs in Google Colab. You need a Google account and about 20 GB free on Google Drive.

**Run the notebook cells in this order:**

1. Folder structure cells — sets up Drive folders
2. Setup cells — clears memory, installs packages
3. Person A cells — builds liboqs, encrypts the model, generates keys and signatures
4. Person B cells — loads the encrypted model chunk by chunk, runs correctness and baseline tests
5. Logging cells — runs anomaly detection tests
6. Person C cells — generates all figures and tables

**Important:** Always run cells top to bottom in a fresh session. Never skip Person A's key restore cell.

---

## First Time Setup

The notebook downloads Mistral-7B automatically from HuggingFace on first run (14.5 GB, takes about 40 minutes). After that it is cached on Drive.

The first time you run Person A's encryption cell it takes about 10 minutes and writes 14.5 GB of encrypted chunks to Drive. This only needs to run once. After that, the copy cell handles copying chunks to local disk each session.

**Do not re-run the encryption cell** if encrypted chunks already exist on Drive — it generates new keys and breaks existing chunks.

---

## Requirements

- Google Colab Pro or Pro+ recommended (needs Tesla T4 GPU and ~50 GB RAM)
- Google Drive with 20 GB free
- No local installation needed — everything installs automatically in the notebook

**Hardware used in our evaluation:**
- GPU: Tesla T4 (15.6 GB VRAM)
- RAM: 54.8 GB
- CUDA: 12.8
- Python: 3.12.13
- PyTorch: 2.11.0

---

## Model

This artifact uses **Mistral-7B-v0.1**, publicly available at:
https://huggingface.co/mistralai/Mistral-7B-v0.1

Model weights are not included in this repo. The notebook downloads them automatically.

---

## Expected Runtime for Full Reproduction

| Step | Time |
|------|------|
| Model download (first time only) | ~40 minutes |
| Encryption pipeline (first time only) | ~10 minutes |
| Copy chunks to local disk | ~2 minutes |
| Benchmark (5 runs) | ~6 minutes |
| Person B evaluation | ~20 minutes |
| Anomaly detection tests | ~2 minutes |
| Figure generation | ~1 minute |
| **Total (first time)** | **~80 minutes** |
| **Total (repeat sessions)** | **~30 minutes** |

---

## License

Apache 2.0
