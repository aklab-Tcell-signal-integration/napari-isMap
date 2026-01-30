# isMap (immunological synapse map analysis program)

This repository provides a **isMap-Napari** plugin for analyzing T-cell activation from microscopy images.  
It integrates **data preprocessing, segmentation, feature extraction, and interactive visualization** in a single workflow.

---

## ✨ Features

- **TIFF conversion**
- **Background correction** (e.g. rolling ball for ICAM1 channel)
- **T-cell segmentation** with [Cellpose](https://www.cellpose.org/) (including denoising models)
- **Per-cell feature extraction** (intensity metrics, shape, circularity, etc.)
- **Single-cell image cropping**
- **Interactive visualization in Napari**:
  - Image + mask overlay  
  - Per-cell properties and text labels  
  - Filtering by shape features  
  - Export results as CSV  

---

## 📂 Project Structure

```bash
ismap-napari/           # Python package (Napari plugin)
├── src/tcell_analysis  # Source code
│   ├── analysis.py     # Main analysis pipeline
│   ├── preprocessing/  # Background correction etc.
│   ├── masking/        # Segmentation (Cellpose)
│   ├── metrics.py      # Per-cell features
│   ├── visualization/  # Napari visualization
│   ├── _widget.py      # Napari widget definition
│   └── napari.yaml     # Plugin manifest
└── test_data/          # Example input files
```

---

## 🚀 Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/.../isMap-napari.git
cd isMap-napari
```

### 2. Create and activate a virtual environment
Linux/macOS:
```bash
python3 -m venv .venv-ismap
source .venv-ismap/bin/activate
```

Windows (PowerShell):
```powershell
python -m venv .venv-ismap
.venv-ismap\Scripts\Activate.ps1
```

### 3. Install the plugin
From inside the repo:
```bash
pip install -e ".[gui]"
```

### 4. Validate installation
```bash
npe2 validate ismap-napari
```
You should see:
```
✔ Manifest for 'immunological synapse Map analysis program' valid!
```

---

## 🧪 Usage in Napari

1. Start Napari:
   ```bash
   napari
   ```
2. Open the plugin:
   **Plugins → isMap (immunological synapse map analysis program)**
3. In the docked widget:
   - **Input Folder** → folder with `.nd2` files  
   - **Output Folder** → where results are saved  
   - **Channels** → e.g. `ICAM1,pTyr,Actin`  
   - **Run Analysis** → runs processing with progress bar  
4. After processing, results appear in the same Napari window:
   - Multi-channel images  
   - Actin segmentation masks  
   - Points layer with per-cell properties + text labels  
   - Interactive filters (circularity, eccentricity, diameter)  
   - CSV export widget (choose save location)  

---

## 📦 Requirements

- For Windows and Linux: Python **3.10+**
- For Mac with Apple silicon: Python **3.11**
- Core:
  - `numpy`, `pandas`, `scikit-image`, `opencv-python`, `tifffile`
- Deep learning:
  - `torch`, `torchvision`, `cellpose==3.1.1.2`
- Napari & GUI:
  - `napari[all]`, `magicgui`, `qtpy`
- Others:
  - `scikit-learn`, `nd2reader`

---

## 📜 License
BSD-3-Clause  


