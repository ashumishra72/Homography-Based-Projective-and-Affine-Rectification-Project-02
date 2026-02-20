Homography-Based Projective and Affine Rectification

Author: Ashutosh Kumar

Overview

Images of planar structures such as buildings often suffer from perspective distortion due to camera projection. As a result, parallel lines may appear to converge, angles are not preserved, and direct measurement of real-world dimensions becomes unreliable.

This project addresses these challenges by applying homography-based geometric rectification techniques to a single image of a planar surface. The method removes projective distortion, affine distortion, and finally introduces scale to recover metric information without requiring explicit camera calibration.

The complete pipeline consists of:

Projective to affine rectification using vanishing points

Affine to metric (similarity) rectification using orthogonality constraints

Real-world distance measurement using homography estimation

Objectives

Remove projective (perspective) distortion from a single planar image

Restore parallelism through vanishing line estimation

Eliminate affine distortion using orthogonality constraints

Perform metric rectification to preserve angles

Estimate a homography between image and world coordinates

Recover real-world distances from a single image

Methodology

The proposed approach follows a three-stage rectification pipeline, where each stage removes a specific geometric distortion.

1. Image Acquisition and Preprocessing

A single image containing a planar surface is selected

The image exhibits perspective distortion due to camera projection

The image is loaded into MATLAB

Conversion to grayscale is performed if necessary to simplify processing while preserving geometry

2. Projective to Affine Rectification

This stage removes projective distortion, ensuring that parallel lines in the real world appear parallel in the image.

2.1 Point Selection on a Planar Rectangle

Four corner points of a rectangular structure on the plane are manually selected

Although distorted in the image, opposite sides are parallel in the real world

Points are represented in homogeneous coordinates

2.2 Line and Vanishing Point Computation

Lines are computed using cross products of point pairs

Parallel lines intersect at vanishing points in the image

Two vanishing points are computed and normalized

2.3 Vanishing Line Estimation

The vanishing line is obtained as the cross product of the two vanishing points

This line represents the image of the line at infinity for the plane

2.4 Affine Rectification

A projective homography maps the vanishing line to infinity

Applying this homography removes projective distortion

The output is an affine-rectified image where parallelism is preserved

3. Affine to Metric (Similarity) Rectification

Although affine rectification preserves parallelism, angles and lengths remain distorted. This stage enforces metric constraints.

3.1 Selection of Orthogonal Line Pairs

Two pairs of lines known to be perpendicular in the real world are selected

Each line is defined using two manually selected points

3.2 Metric Rectification

Orthogonality constraints are formulated mathematically

The constraint system is solved using Singular Value Decomposition (SVD)

Cholesky decomposition is applied to recover the affine correction matrix

A metric rectification homography is constructed and applied

The resulting image preserves angles and shape up to a scale factor

4. Real-World Measurement Using Homography

The final stage introduces scale, enabling accurate real-world measurements.

4.1 Point Correspondence Selection

Four points are selected from the metric-rectified image

Corresponding real-world coordinates are defined using known physical dimensions

4.2 Homography Estimation

A projective transformation between image and world coordinates is computed

The Direct Linear Transform (DLT) algorithm is used

The resulting linear system is solved using SVD

4.3 Distance Measurement

Image points are mapped to world coordinates using the inverse homography

Coordinates are normalized

Euclidean distances are computed directly in real-world units

Mathematical Background
Line at Infinity

In homogeneous coordinates, the line at infinity is represented as:

𝑙
∞
=
[
0
 
0
 
1
]
𝑇
l
∞
	​

=[0 0 1]
T

Due to perspective projection, this maps to a finite vanishing line in the image:

𝐿
∞
=
[
𝑙
1
 
𝑙
2
 
𝑙
3
]
𝑇
L
∞
	​

=[l
1
	​

 l
2
	​

 l
3
	​

]
T

A projective homography maps this vanishing line to infinity, removing projective distortion.

Results: Homography Matrix Estimation

Planar homographies were estimated to map points between image coordinates and world coordinates. Four point correspondences were selected interactively for each case.

Estimated Homographies

H₁

[
2878.0764
	
−
8085.2967
	
4219.5707


1298.4275
	
−
3757.7002
	
2064.1627


1.5696
	
−
3.2491
	
1.0000
]
	​

2878.0764
1298.4275
1.5696
	​

−8085.2967
−3757.7002
−3.2491
	​

4219.5707
2064.1627
1.0000
	​

	​


H₂

[
194.2654
	
495.9643
	
1410.2287


404.4570
	
144.0774
	
375.2287


0.1374
	
0.3183
	
1.0000
]
	​

194.2654
404.4570
0.1374
	​

495.9643
144.0774
0.3183
	​

1410.2287
375.2287
1.0000
	​

	​


H₃

[
2878.0764
	
−
8085.2967
	
4219.5707


1298.4275
	
−
3757.7002
	
2064.1627


1.5696
	
−
3.2491
	
1.0000
]
	​

2878.0764
1298.4275
1.5696
	​

−8085.2967
−3757.7002
−3.2491
	​

4219.5707
2064.1627
1.0000
	​

	​


These homographies encode rotation, translation, scale, and perspective distortion in a single 
3
×
3
3×3 matrix defined up to scale.

Tools and Requirements

MATLAB (R2021a or later recommended)

Image Processing Toolbox

Manual point selection using MATLAB graphical tools

Conclusion

This project demonstrates that reliable metric information can be recovered from a single image of a planar scene without explicit camera calibration. By successively removing projective and affine distortions and estimating a homography to world coordinates, accurate real-world measurements become possible. The results confirm the effectiveness of homography-based rectification techniques for planar geometry analysis.

Author

Ashutosh Kumar
