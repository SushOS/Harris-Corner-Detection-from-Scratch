# Harris-Corner-Detection-from-Scratch

## Introduction and Aim
The aim of this project is to implement the Harris Corner detection technique from scratch without using any built-in functions. The objective is to optimize parameters such as window size and threshold value for improved corner detection performance. Additionally, the project seeks to compare the performance of the implemented algorithm with the corner detection libraries available in OpenCV. By comparing visual results obtained from both approaches, with and without the library, this project aims to evaluate the effectiveness and accuracy of the custom implementation against the standard library functions.

## How to Proceed

### Convolution
The `convolve` function implements the convolution operation between an image and a given kernel. It pads the input image to handle border pixels and then slides the kernel over each pixel in the image, computing the dot product between the kernel and the corresponding image patch.

### Compute Gradients
The `compute_gradients` function calculates the gradients in the x and y directions using Sobel operators. It utilizes the `convolve` function to convolve the image with Sobel kernels to obtain gradient images in both directions.

### Gaussian Kernel and Blur
The `gaussian_kernel` function generates a Gaussian kernel of a specified size and standard deviation (sigma). The generated kernel is normalized to ensure that the sum of its elements equals one. The `gaussian_blur` function applies Gaussian blur to an input image using the generated Gaussian kernel. It convolves the image with the Gaussian kernel using the `convolve` function.

### Magnitude of Gradients
The `mag_grads` function computes the magnitude of gradients by taking the absolute value of each element in the gradient images obtained from the Sobel operators.

### Matrix Parameters
The `mat_params` function computes the parameters of the matrix M for each pixel in the image. These parameters include the squared gradients in x and y directions ( ix_2 , iy_2 ), and the product of gradients ( ixy , iyx ).

### Harris Corner Detection from Scratch
The `HCD_R` function computes the corner strength (R) using the Harris corner detection algorithm. It first performs Gaussian blur on the squared gradients and the product of gradients matrices (ix_2 , iy_2 , ixy , iyx), using the `gaussian_blur` function. Then, for each pixel in the image, it constructs the structure tensor M and computes the corner strength R using the formula provided by the Harris Corner Detection algorithm. The computed corner strengths are stored in the matrix R.

The `detect_corners` function identifies corners based on the corner strength matrix (R) and a specified threshold. It applies non-maximum suppression to find local maxima within a 4x4 window. If a pixel's corner strength is above the threshold and it is a local maximum within its window, it is considered a corner, and its coordinates are added to the list of detected corners.

### Harris Corner Detection using OpenCV
The `cv2.cornerHarris()` function is then used to detect corners in the blurred image. The function takes parameters such as the size of the neighbourhood, aperture parameter for the Sobel operator, and the Harris detector free parameter. After corner detection, dilation is applied to enhance the visibility of the corners. Finally, a threshold is applied to extract large corners, and circles are drawn at the detected corner locations.

<img width="346" alt="image" src="https://github.com/SushantRavva/Harris-Corner-Detection-from-Scratch/assets/113240987/d1017539-509c-4200-a53a-048e73b774f2">


## Comparison of Feature Detection (Scratch vs OpenCV)
The project includes a comparison between the custom implementation of Harris Corner Detection and the implementation available in OpenCV. Visual results obtained from both approaches will be compared to evaluate the effectiveness and accuracy of the custom implementation against the standard library functions.

<img width="858" alt="image" src="https://github.com/SushantRavva/Harris-Corner-Detection-from-Scratch/assets/113240987/a272ff6f-5f81-458d-ae84-454cb53d5c54">

