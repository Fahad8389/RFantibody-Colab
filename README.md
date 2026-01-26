# RFantibody Colab

Structure-based *de novo* antibody and nanobody design on Google Colab - no Docker required.

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/YOUR_USERNAME/RFantibody-Colab/blob/main/RFantibody_Colab.ipynb)

## What is this?

A Google Colab notebook for running [RFantibody](https://github.com/RosettaCommons/RFantibody) without Docker. Design antibodies or nanobodies against any protein target.

## Pipeline

| Step | Model | Purpose |
|------|-------|---------|
| 1 | RFdiffusion (Ab) | Generate antibody backbone |
| 2 | ProteinMPNN | Design amino acid sequence |
| 3 | RF2 (Ab) | Validate structure prediction |

## Features

- **Antibody mode**: Design with Heavy + Light chains
- **Nanobody mode**: Design single-domain antibodies (VHH)
- **GPU accelerated**: Runs on Colab's free T4 GPU
- **No installation**: Everything runs in the cloud

## Requirements

- Google account (for Colab)
- Target PDB file (your antigen)
- Hotspot residues (epitope on target)

## Quick Start

1. Click the "Open in Colab" badge above
2. Enable GPU: Runtime → Change runtime type → T4 GPU
3. Run setup cells (clone, weights, dependencies)
4. Upload your target PDB
5. Set parameters (hotspots, loop lengths, number of designs)
6. Run the pipeline
7. Download results

## Input Format

### Target PDB
- Your antigen structure (from RCSB PDB or AlphaFold)
- Chain will be automatically renamed to T

### Hotspot Residues
- Epitope residues where you want the antibody to bind
- Format: `[T195,T197,T256]`
- Find these using ChimeraX: `select zone /antibody 4 /target`

### Design Loops
- **Antibody**: `[L1:8-13,L2:7,L3:9-11,H1:7,H2:6,H3:5-13]`
- **Nanobody**: `[H1:7,H2:6,H3:5-13]`

## Output

- Validated PDB files with designed antibody/nanobody
- Each design includes:
  - Backbone structure
  - Amino acid sequence
  - Target complex

## Filtering Criteria

Designs pass RF2 validation if:
- pAE < 10 (predicted aligned error)
- RMSD < 2 Å (structure deviation)

## Runtime

On T4 GPU:
- Setup: ~5 min
- Per design: ~1-2 min
- Total (10 designs): ~20-25 min

## Credits

Based on [RFantibody](https://github.com/RosettaCommons/RFantibody) by:
- RosettaCommons / Baker Lab
- Institute for Protein Design, University of Washington

## Citation

If you use this notebook, please cite the original RFantibody paper:
```
[RFantibody citation - check original repo]
```

## License

This Colab adaptation follows the license of the original RFantibody repository.
