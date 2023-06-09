## Task 1:
- Paper reading
<hr>

## Task 2:
- Scaled mean shape
- Rotated both mean shape and deformation vectors
<hr>

## Task 3:
- Got tracklet data from the devkit labels
- Obtained 3D projections of the bounding boxes using the Mobili formula
  - This is the translation element corresponding to the car (6 elements for each of the 6 cars)
<hr>

## Task 4:
- Rotated the mean shape and deformation vectors according to the `ry` field from the tracklets
  - Then, added the translation element from the previous task to the mean shape
  - Then, projected the 3D mean shape wireframe to 2D using the camera intrinsics matrix and divided x and y coordinates with z coordinate (concepts of homogeneous coordinates)
  - Plotted the corresponding wireframes onto the images of the 6 cars (from the left_colour_images)
<hr>

## Task 5:
- From file of predicted keypoint locations in 2D outputted by the hourglass network, rescaled their locations to adjust from 64 x 64 img (hourglass network takes imgs with this dimension) to the original image dimensions so that the predicted keypoints can be visualized on the actual car
<hr>

## Task 6:
- At this point, we use ceres to further improve the predictions
- First, we get the weights matrix corresponding to the predicted keypoints
- Then, we create a file containing all the required info for the ceres pose optimizer
- The optimizer generates a rotation and translation matrix for each of the 6 cars, which improves the pose estimates
- The wireframes are then corrected and the image coordinates are generated using the process used in Task 4
<hr>