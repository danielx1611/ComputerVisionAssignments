# Camera Pose Estimation (OpenCV + Gradio)

## Setup
- Open in Google Colab.
- Run all code cells leading up to the driver code header to install packages and prepare core functions.
- Run the Central UI cell to start up the gradio UI needed to upload images and run the calibration scripts
- Run the Picker UI cell to upload images and mark the corners of the desired object

## How to Use
1. Print the OpenCV chessboard: https://docs.opencv.org/4.x/pattern.png  
2. Capture 15–20 images of the board from varied angles.
3. In the notebook UI:
   - Upload `.jpeg` images → program has them saved to `/content/images/`.
   - Click **Run Calibration**.
   - When done executing, go to the picker UI, upload `.jpeg` images, and select the corners of the square for the uploaded image, then click **Done**.
   - After marking images with the picker UI, switch the central UI to the **Homography/Poses** tab.
   - Click **Calculate Homography Matrices**.
   - After execution is complete, click **Run Homography Pose** and after it is finished executing, click **Run OpenCV Pose**.
4. Results:
   - `calibration.json` storing K (intrinsics), R, t (extrinsics), D (distortion), width, height.
   - Before/After images of planar object with corners of square marked.
   - 3D camera pose plot (one from explicit calculations, other from openCV).
   - Sample overlays with world axes (one set from explicit calculations, other from openCV).

## Code Structure
- **Initialization**: install necessary libraries and call required imports
- **Camera Calibration**: calibration, I/O with OpenCV FileStorage.
- **Utils**: utility functions for drawing figures/axes.
- **Camera Pose and Position Extraction**: core class for extracting camera intrinsics from homography data and computing camera pose
- **UI Tabs**: gradio ui setup and helper functions.
- **Interact**: run gradio ui for interaction with code via file upload and picker. Converting json result data to 3d camera plots and adding world axes to planar object images

## Homework Questions & answers
- Were R,t similar? Any noticeable translation scale issues?
<br> Rotation will be similar. However, t would be differnt in sizewize when inputing an incorrect scale value.
- Did RANSAC help? Sensitivity to point order? Try more points with some noisy ones.
<br> CV.RANSAC will help to ignore outliers which will give a more stable transformation.
- Effects of undistortion vs. using raw image with `distCoeffs`.
<br> Both can be solved but only should use one. When using undistorted images, use solvePNP. When using raw images, we should do distortion correction first.
- Numerical quirks: orthonormalization, det(R) sign.
<br> RR.T should be identity matrix. also, if det(R) is negative, should multiply -1 on third row to correct the rotation
