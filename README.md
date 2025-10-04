# Monet Style Transfer - CycleGAN Implementation

Transform landscape photos into Monet-style paintings using CycleGAN (unpaired image-to-image translation).

## Dataset

- **Monet paintings**: 300 images (256×256 RGB)
- **Photo images**: 7,038 images (256×256 RGB)
- **Source**: Kaggle "I'm Something of a Painter Myself" competition

## Model Architecture

### CycleGAN

**Generators**:

- **G_XY**: Photo → Monet (ResNet-based with 9 residual blocks)
- **G_YX**: Monet → Photo (ResNet-based with 9 residual blocks)

**Discriminators**:

- **D_X**: Photo discriminator (PatchGAN)
- **D_Y**: Monet discriminator (PatchGAN)

### Loss Functions

- **Adversarial Loss**: LSGAN (MSE)
- **Cycle Consistency Loss**: L1 (λ=10)
- **Identity Loss**: L1 (λ=5)

## Training

- **Optimizer**: Adam (lr=2e-4, beta1=0.5)
- **Batch size**: 1
- **Epochs**: 30
- **Mixed Precision**: Enabled for memory efficiency

## Key Advantages

1. **Data Utilization**: Uses all 7,038 photos (vs 300 Monet only)
2. **No Mode Collapse**: Maintains photo diversity
3. **Content Preservation**: Structural elements preserved
4. **Stable Training**: Cycle consistency ensures stability

## Results

- **Generated**: 7,000 Monet-style images
- **Output**: `images.zip` for Kaggle submission
- **Quality**: High-quality style transfer with preserved content structure

## Usage

**Assignment version** (complete analysis with DCGAN comparison):

```bash
jupyter notebook gan_monet.ipynb
```
