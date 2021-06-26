# Iris Segmentation
Iris based security system using techniques of iris segmentation by Canny edge detection and Hough transformation implemented in OpenCV Python.

Iris segmentation is the first step and also the key step of the whole iris recognition. Its
objective is to separate the usable iris pattern from other parts of the eye and the noise as
well. It is obvious that the accuracy of the iris segmentation will have great impact on the
result of future processing. It’s the process of detecting the pupillary and limbi boundaries of
an iris in the image. This would help in extracting features of the iris, excluding the
surrounding of the pupil.

If the iris regions were not correctly segmented, there would possibly exist four kinds of
noises in segmented iris regions: eyelashes, eyelids, reflections and pupil, which will result in
poor recognition performance.

## Methodology

In this proposed method for performing iris segmentation we use Hough Transform, and
Canny Edge Detection techniques. The first is a curve fitting technique and the second is a
newly proposed technique ensuring a good combination between contour fitting and curve
evolution-based approach for performing iris segmentation in a challenging database.

In order to extract the edges we shall be using Hough transform which detects the circles. In
order to perform Hough transform we need to perform edge extraction because Hough
transforms work only on edge extracted images. In order to perform Edge extraction we shall
use canny edge detector algorithm.

### Canny Edge Detector Algorithm:

1. Removing noise using a 5x5 gaussian filter with standard deviation 1.4

2. Use first derivative filter to calculate GX and GY. Mostly Sobel or Sommel filters are
used

3. Magnitude and direction of the gradient is calculated

4. Non maximum suppression- in this if a pixel is not a maximum it is suppressed. The
following 4 criteria are checked over each pixel to determine if that pixel is maximum or not:

• 22.5 to 67.5 degrees: If the gradient orientation is in this range means the edge lies
from the top right corner to bottom left

• 67.5 to 112.5 degrees: The gradient is from top to bottom. This means the edge is
from left to right. So you check gradient magnitudes against the pixels right above
and below.

• 112.5 to 157.5 degrees: The gradient is the other diagonal.

• 0-22.5 or 157.5-180 degrees: The gradient is horizontal. So the edge is vertical. So
you check the pixels to the left and right.

5. Thresholding with hysteresis: in this we check if the current pixel is an edge or not, if not
check the next pixel. If it is an edge we check the two pixels in the direction of the edge if
either of them:

• Have the direction in the same bin as the central pixel

• Gradient magnitude is greater than the lower threshold

• They are the maximum compared to their neighbours (non-maximum suppression for
these pixels), then you can mark these pixels as an edge pixel

• Loop until there are no changes in the image Once the image stops changing, you've
got your canny edges 

After determining the edges, location of the iris is found using Hough transform.

### Hough Transformation Algorithm:

1. Initialize pupil radius and iris radius the given database.

2. Scale the image.

3. Gaussian filtering.

4. Edge map creation using canny edge detection.

5. Circular Hough transform for limbic boundary detection

6. Circular Hough transform for pupillary boundary detection inside located iris.

7. Linear Hough transform for eyelid detection.

8. Display the segmented image.

The iris data base is used to implement and test the model for iris recognition technique. Iris
recognition identifies people by utilizing the particular iris pattern properties and contrasting
it with database’s reference.

In program coding, we set threshold value if the match percentages is less than threshold
value then the result will be appeared as Iris images are not matching so access is denied. If
the matched percentage is greater than threshold value the result will be appeared as access is
granted.

Match factor can be calculated as Match factor = (matched_data/total_data)*100


