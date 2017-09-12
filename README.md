# **Finding Lane Lines on the Road** 

---

The goals of this project is: **Make a pipeline that finds lane lines on the road**

---

### 1. pipeline.

My pipeline to solve this problem consisted of 5 steps. In order:

* select a region of interest (in particular I selected a rectangle removing the 60% of the height);
* grayscale the image;
* select only pixels with a value between 200 and 255;
* apply a Gaussian filter;
* apply a Canny edge detector to select all the edges;
* apply a Hough transform to detect only the lines;

to draw only the two correct lines on every images, I computed the angular coefficients of every piece of line detected by the Hough algorithm; I separated in positive(for the left line) and negative(for the right line); and I selected only the coeffs in a particular range(between 0.55 and 0.8 in absolute value).
After that I averaged the two collection of angular coefficients and computed an approximate line, using two points (the bottom point and the upper point in the image).

Every step of the pipeline is visualized in the notebook.


### 2. shortcomings

One shortcoming is that I assume that my lines are always in a particular range of angular coefficients and this could be not always true; a second shortcoming is that, when the street is almost white and there is a curve, my pipeline has some problem to detect the right lines: probably the edge detection and the color threshold generate this problem.  


### 3. improvements

Using a Regression method to compute the final lines could help to obtain a more robust and general result.
