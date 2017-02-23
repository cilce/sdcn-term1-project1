#**Finding Lane Lines on the Road** 

###1. The pipeline

The lane detection pipeline in this solution is as follows:

1. The image is converted to grayscale
2. Gaussian smoothing with a kernel of size 5 is applied to reduce the noise 
3. Canny transform is applied. The parameters for Canny is calculated in a dynamic way, by taking the mean of the pixels, and multiplying by constants (the suggestion from a web source is followed here, for better results, the constants might need to be calculated in a different way)
4. The region of interest is selected on the image according to the camera position on the vehicle.
5. Hough transform is applied with empirical parameter choice. In addition to the standard hough transform, the individual lines on each side are averaged(their midpoint and slope, with the weight of their length), and passed through a historical mean of the last 40 frames in order to make the noise less visible. (This changes are part of the "draw_lines" function) 
6. The highlighted lanes are merged with the actual image.


###2. Potential shortcomings of the current pipeline

- According to the experiments ran on the videos, in some cases the calculated slope and endpoints diverge from the actual lane. This might be solved by optimising the parameters passed the Canny and Hough transforms.

###3. Possible improvements to the pipeline

- Optimise the Canny and Hough parameters (potentially in a dynamic way)
- A fixed number of historical frames used while calculating the new lines in order to reduce the noise. This can be optimised (A better fixed number can be found, or a dynamic way can be introduced.)


