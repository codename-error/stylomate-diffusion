# Codename Error's Here!

## 🛍️ VITON-HD+: Virtual Try-On for Full-Body Outfits

Enhanced version of VITON-HD with support for **upper clothing + pants** and improved accuracy.
This is the basic model of Virtual Try-on that embedded with StyloMate; Codename Error's project of Hackvidia

## 📋 Prerequisites
- Python 3.9+
- NVIDIA GPU (≥8GB VRAM)
- CUDA 12.8 & cuDNN 8.9.7+
- PyTorch 2.0+

## 🚀 Quick Start
### 1. Clone Repository
```bash
git clone https://github.com/yourusername/VITON-HD-Plus.git
cd VITON-HD-Plus
```

### 2. Install Dependencies
```bash
conda create -n vitonhd python=3.9
conda activate vitonhd
pip install -r requirements.txt
```

### 3. Download Pretrained Models
```bash
wget https://huggingface.co/yourusername/vitonhd-plus/resolve/main/checkpoints.zip
unzip checkpoints.zip -d ./checkpoints
```

### 4. Prepare Dataset
```Folder Structure
datasets/
├── test/
│   ├── image/          # Full-body images (e.g., 01234_00.jpg)
│   ├── cloth_upper/    # Upper clothing images
│   ├── cloth_pants/    # Pants images
│   ├── image-parse/    # Segmentation maps (include pants label)
└── test_pairs.txt      # Format: human_image.jpg upper_cloth.jpg pants.jpg
```

### 5. Run Inference
Basic
```bash
python test.py \
  --name output_demo \
  --dataset_mode full_body \
  --load_width 768 \
  --load_height 1024```
```

Advanced
```bash
python test.py \
  --use_pants 1 \               # Enable pants processing
  --texture_weight 0.7 \        # Fabric preservation strength
  --gmm_grid_size 5 \           # Warping precision
  --alias_resolution high       # Output quality
```

## Advanced Configuration
```bash
python train.py \
  --name my_train \
  --semantic_nc 14 \        # 13 (original) + 1 pants class
  --dataset_dir ./custom_data \
  --save_epoch_freq 5
```

## Training Your Own Model
Prepare training data:
```bash
python scripts/preprocess.py \
  --input_dir ./raw_data \
  --output_dir ./datasets/train
```

Start training:
```bash
python train.py \
  --name my_model \
  --epochs 100 \
  --batch_size 4 \
  --save_freq 10
```

## License
Creative Commons Attribution 4.0 © 2025 Ifan Hakim

📧 Contact
For support: ifanhakm@gmail.com
