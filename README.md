📌 Project Summary
| Item          | Description                                                             |
| ------------- | ----------------------------------------------------------------------- |
| Project Title | Homography-Based Projective and Affine Rectification                    |
| Goal          | Recover metric information from a single image of a planar surface      |
| Input         | Single perspective-distorted image                                      |
| Output        | Affine-rectified image, metric-rectified image, real-world measurements |
| Tools         | MATLAB                                                                  |
| Key Technique | Planar Homography      

|
🎯 Objectives
| No. | Objective                                                |
| --- | -------------------------------------------------------- |
| 1   | Remove projective (perspective) distortion               |
| 2   | Restore parallelism using vanishing points               |
| 3   | Remove affine distortion using orthogonality constraints |
| 4   | Perform metric (similarity) rectification                |
| 5   | Estimate homography between image and world coordinates  |
| 6   | Measure real-world distances from a single image         |

🧪 Methodology Overview


| Stage   | Rectification Type  | Purpose                       |
| ------- | ------------------- | ----------------------------- |
| Stage 1 | Projective → Affine | Restore parallel lines        |
| Stage 2 | Affine → Metric     | Preserve angles and shapes    |
| Stage 3 | Metric → World      | Enable real-world measurement |
🖼️ Stage 1: Image Acquisition & Preprocessing

📐 Stage 2: Projective to Affine Rectification


| Step                 | Description                      |
| -------------------- | -------------------------------- |
| Image Selection      | Single image of a planar surface |
| Distortion           | Perspective distortion present   |
| Preprocessing        | Load image in MATLAB             |
| Grayscale Conversion | Applied if required              |

📏 Stage 3: Affine to Metric Rectification

| Step             | Description                              |
| ---------------- | ---------------------------------------- |
| Point Selection  | Four corner points of a planar rectangle |
| Representation   | Homogeneous coordinates                  |
| Line Computation | Cross product of point pairs             |
| Parallel Lines   | Used to compute vanishing points         |

🌍 Stage 4: Real-World Measurement Using Homography

| Concept               | Expression                               |
| --------------------- | ---------------------------------------- |
| Line at Infinity      | ( l_\infty = [0\ 0\ 1]^T )               |
| Vanishing Line        | ( L_\infty = [l_1\ l_2\ l_3]^T )         |
| Projective Homography | Maps vanishing line to infinity          |
| Distance Formula      | ( d = \sqrt{(X_1-X_2)^2 + (Y_1-Y_2)^2} ) |

📊 Results: Estimated Homographies
| Homography | Description                    |
| ---------- | ------------------------------ |
| H₁         | World → Image mapping (Case 1) |
| H₂         | World → Image mapping (Case 2) |
| H₃         | World → Image mapping (Case 3) |


| Item         | Requirement              |
| ------------ | ------------------------ |
| Software     | MATLAB                   |
| Version      | R2021a or later          |
| Toolboxes    | Image Processing Toolbox |
| Input Method | Manual point selection   |


| Outcome            | Description                               |
| ------------------ | ----------------------------------------- |
| Distortion Removal | Projective and affine distortions removed |
| Geometry           | Parallelism and angles restored           |
| Measurement        | Real-world distances recovered            |
| Calibration        | No camera calibration required            |

| Name           |
| -------------- |
| Ashutosh Kumar |
