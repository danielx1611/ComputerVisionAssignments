# Camera Calibration (OpenCV + Gradio)

## Setup
- Open in Google Colab.
- Run all code cells leading up to the to install packages and prepare core functions.
- Run the Gradio UI cell to start up the gradio UI needed to upload images and run the calibration scripts

## How to Use
1. Print the OpenCV chessboard: https://docs.opencv.org/4.x/pattern.png  
2. Capture 15–20 images of the board from varied angles.
3. In the notebook UI:
   - Upload `.jpeg` images → program has them saved to `/content/images/`.
   - Click **Run Calibration**.
   - When done executing, Click **Visualize Results**.
4. Results:
   - `calibration.json` storing K (intrinsics), R, t (extrinsics), D (distortion), width, height.
   - 3D camera pose plot.
   - Sample overlays with world axes.

## Code Structure
- **Initialization**: install necessary libraries and call required imports
- **Camera Calibration**: calibration, I/O with OpenCV FileStorage.
- **Visualization**: converting json result data to 3d camera plots and adding world axes to chessboard images
- **Gradio UI**: gradio ui setup and helper functions.
- **Interact**: run gradio ui for interaction with code via file upload.
