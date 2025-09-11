# Camera Pose Estimation (OpenCV + Gradio)

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

## Homework Questions & answers
- Were R,t similar? Any noticeable translation scale issues?
\n Rotation will be similar. However, t would be differnt in sizewize when inputing an incorrect scale value.
- Did RANSAC help? Sensitivity to point order? Try more points with some noisy ones.
\n CV.RANSAC will help to ignore outliers which will give a more stable transformation.
- Effects of undistortion vs. using raw image with `distCoeffs`.
\n Both can be solved but only should use one. When using undistorted images, use solvePNP. When using raw images, we should do distortion correction first.
- Numerical quirks: orthonormalization, det(R) sign.
\n RR.T should be identity matrix. also, if det(R) is negative, should multiply -1 on third row to correct the rotation