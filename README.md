# Image Smoothing and Sharpening Using OpenCV

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

## Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

## Algorithm

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

## Program

### Developed By

- **Name:** Vikamuhan Reddy
- **Register No:** 212223240181  

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
img = cv2.imread('image.jpg')

if img is None:
    print("Image not found!")
else:
    # Convert BGR to RGB
    original = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

    # 1. Averaging Filter
    averaging = cv2.blur(img, (5, 5))

    # 2. Weighted Averaging Filter
    kernel = np.array([[1, 2, 1],
                       [2, 4, 2],
                       [1, 2, 1]], dtype=np.float32) / 16

    weighted = cv2.filter2D(img, -1, kernel)

    # 3. Gaussian Filter
    gaussian = cv2.GaussianBlur(img, (5, 5), 0)

    # 4. Median Filter
    median = cv2.medianBlur(img, 5)

    # 5. Laplacian Sharpening using Kernel
    lap_kernel = np.array([[0, -1, 0],
                           [-1, 5, -1],
                           [0, -1, 0]])

    lap_sharp = cv2.filter2D(img, -1, lap_kernel)

    # 6. Laplacian Operator
    gray = cv2.cvtColor(img, cv2.COLOR_BGR2GRAY)
    laplacian = cv2.Laplacian(gray, cv2.CV_64F)
    laplacian = cv2.convertScaleAbs(laplacian)

    # Function to display images
    def show(title, image, cmap=None):
        if cmap:
            plt.imshow(image, cmap=cmap)
        else:
            plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
        plt.title(title)
        plt.axis('off')

    # Display Original and Smoothing Filters
    plt.figure(figsize=(12, 8))

    plt.subplot(2, 3, 1)
    show("Original Image", img)

    plt.subplot(2, 3, 2)
    show("Averaging Filter", averaging)

    plt.subplot(2, 3, 3)
    show("Weighted Averaging", weighted)

    plt.subplot(2, 3, 4)
    show("Gaussian Filter", gaussian)

    plt.subplot(2, 3, 5)
    show("Median Filter", median)

    plt.tight_layout()
    plt.show()

    # Display Sharpening Filters
    plt.figure(figsize=(10, 5))

    plt.subplot(1, 3, 1)
    show("Original Image", img)

    plt.subplot(1, 3, 2)
    show("Laplacian Kernel", lap_sharp)

    plt.subplot(1, 3, 3)
    show("Laplacian Operator", laplacian, cmap='gray')

    plt.tight_layout()
    plt.show()
```

##  Output

### Smoothing Filters
<img width="1088" height="597" alt="image" src="https://github.com/user-attachments/assets/edd2658a-9a95-47cf-a546-d2a4f12e69de" />


###  Sharpening Filters

<img width="1020" height="243" alt="image" src="https://github.com/user-attachments/assets/ae9f953b-dddf-404a-a8d6-1b98a075ca3c" />


---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
