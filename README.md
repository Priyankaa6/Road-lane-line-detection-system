# Road-lane-line-detection-system
Detecting Lane lines is one of the most fundamental concepts for building a Self Driving Car. In this repository, I have used OpenCV to detect lane lines in a sample video sample obtained from a camera places on a car.

You need OpenCV to run this project on your local machine and it can be installed simply by a single command - <br>
```pip install opencv-python```

![Demo](https://i.ibb.co/1bQcV0Y/Working.gif)

## How to run
1. Download/Clone the repo.
2. Make sure you have OpenCV installed for Python.(I recommend installing it on top of Anaconda Distribution)
3. Execute the **Main.py** script
```
python Main.py
```

## Intuition behind Concepts

Every image is essentially a numpy array at the end of the day, with values containing pixel intensities, 0 denoting complete black(dark) and 1 denoting complete white(bright), considering a grayscale image.

### 1. Gaussian Blur
Used to reduce noise and smoothen out the image. We generally use a kernel of some specific size(say 5x5) and a deviation

![Gradient](https://i.ibb.co/zNNtJYp/Gradient.png)

The above image shows a **Strong gradient** on the left and a **Weak Gradient** on the right.

Gradient : Change in brightness over a series of pixels.
### 2. Canny Edge Detection
As the name suggests, it is an algorithm to detect edges in our image.
A change in intensity of pixels will give us an edge.



### 3. Hough Transform
After we have successfully detected edges in our image, it's time to detect lane lines in our image, for which we can use the Hough transform.

Before that, we need to find the **Region on interest** in our image. For that, we use Matplotlib to get a fair enough idea about the coordinate values of the image. <br>

Once we are done, we create a mask with a polygon over it as shown :
![Mask](https://i.ibb.co/DrLNSJR/Mask.png)

0000 represents the black pixels and 11111111 represents the white pixels, denoting the polygon. Now, we apply the **bitwise_and** in the original image and the mask to obtain the **masked_image**, which essentially will contain only the region on interest.

![Masked Image](https://i.ibb.co/LJFykXC/Masked-Image.png)  
### Ultimate Result <br>
![Final Masked Image](https://i.ibb.co/711SBhW/Final-Masked-Image.png)

Finally, now when we have only the Region of interest in our image, we will use Hough Transform to detect Straight lines in our image. 

#### Ultimate Goal - Try to find a line that best describes our points.

