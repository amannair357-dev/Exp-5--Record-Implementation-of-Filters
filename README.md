# Exp-5--Record-Implementation-of-Filters

## Image Smoothing and Sharpening Using OpenCV

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `image.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---

##  Developed By

- **Name:** Aman Nair  
- **Register No:** 212225240008


~~~python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read image
img = cv2.imread('low_qua_img.jpg')

if img is None:
    print("Image not found!")
else:
    # Convert BGR to RGB
    img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # Averaging filter
    avg = cv2.blur(img, (5, 5))

    # Weighted averaging filter
    kernel = np.array([[1, 2, 1],
                       [2, 4, 2],
                       [1, 2, 1]], dtype=np.float32) / 16
    weighted = cv2.filter2D(img, -1, kernel)

    # Gaussian filter
    gaussian = cv2.GaussianBlur(img, (5, 5), 0)

    # Median filter
    median = cv2.medianBlur(img, 5)

    # Laplacian sharpening
    lap_kernel = np.array([[0, -1, 0],
                           [-1, 5, -1],
                           [0, -1, 0]])
    sharpened = cv2.filter2D(img, -1, lap_kernel)

    # Laplacian operator
    gray = cv2.cvtColor(img, cv2.COLOR_RGB2GRAY)
    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian = cv2.convertScaleAbs(laplacian)

    # Display all images
    titles = ['Original Image', 'Averaging', 'Weighted Averaging',
              'Gaussian', 'Median', 'Laplacian Sharpening',
              'Laplacian Operator']

    images = [img, avg, weighted, gaussian, median,
              sharpened, laplacian]

    plt.figure(figsize=(12, 9))

    for i in range(len(images)):
        plt.subplot(3, 3, i + 1)
        plt.imshow(images[i], cmap='gray' if i == 6 else None)
        plt.title(titles[i])
        plt.axis('off')

    plt.tight_layout()
    plt.show()
~~~

---

##  Output

### Smoothing Filters

- Averaging filter produces blurred image  
- Weighted averaging provides smoother result with less distortion  
- Gaussian filter preserves edges better while reducing noise  
- Median filter removes salt-and-pepper noise effectively  

###  Sharpening Filters

- Laplacian kernel enhances edges and fine details  
- Laplacian operator detects edges clearly in grayscale  

<img width="1737" height="761" alt="Screenshot 2026-10-28 084536" src="https://github.com/user-attachments/assets/50e429e6-7a0f-4383-985b-362e85b3a3de" />


---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
