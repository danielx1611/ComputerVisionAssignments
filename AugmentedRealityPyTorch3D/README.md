# Augmented Reality PyTorch3D Assignment 4

## Setup
- Open in Google Colab.
- Run all code cells in order.

## How to Use
1. Run all code cells in order.
2. Results:
   - `calibration.json` storing K (intrinsics), R, t (extrinsics), D (distortion), width, height.
   - Before/After images of planar object with corners of square marked and cow mesh rendered over real world image.

## Code Structure
- **PyTorch3D Initialization**: install necessary libraries and call required imports for PyTorch3D.
- **Imports**: import general libraries and some PyTorch3D setup libraries.
- **Download cow object mesh and convert it to PyTorch3D mesh**: Self explanatory.
- **PyTorch3D Specific Imports**: more imports specifically for PyTorch3D functionalities.
- **Calibration**: calibration, I/O with OpenCV FileStorage.
- **Generate PyTorch3D Renders**: main driver code, runs PyTorch3D functions and produces final result images with cow rendered over real world images.
