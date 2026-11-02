# EXPERIMENT 4 – RECORD-IMAGE TRANSFORMATIONS
## Name : Raha Priya Dharshini M
## Reg no.:212224240124

## Aim
To perform various image transformations using OpenCV and Python, including translation, scaling, shearing, reflection, rotation and cropping.

## Procedure
1. Import the required libraries: OpenCV, NumPy and Matplotlib.
2. Read the input image (`myfoto.jpg`) using OpenCV.
3. Display the original image.
4. Perform image translation by shifting the image horizontally and vertically.
5. Perform image scaling by changing the width and height using scaling factors.
6. Apply image shearing using a transformation matrix.
7. Perform image reflection using the OpenCV flip function.
8. Rotate the image by 45 degrees around its centre.
9. Crop a selected portion of the original image using specified coordinates.
10. Display the output of each transformation.

## Code:
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread('myfoto.jpg')

if image is None:
    raise FileNotFoundError("myfoto.jpg not found")

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis('off')
plt.show()

tx, ty = 100, 50
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])
translated_image = cv2.warpAffine(
    image, M_translation, (image.shape[1], image.shape[0])
)

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))
plt.title("Translated Image")
plt.axis('off')
plt.show()

fx, fy = 5.0, 2.0
scaled_image = cv2.resize(
    image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR
)

plt.figure(figsize=(10, 6))
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))
plt.title("Scaled Image")
plt.axis('off')
plt.show()

shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])
sheared_image = cv2.warpAffine(
    image, shear_matrix, (image.shape[1], image.shape[0])
)

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))
plt.title("Sheared Image")
plt.axis('off')
plt.show()

reflected_image = cv2.flip(image, 2)

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))
plt.title("Reflected Image")
plt.axis('off')
plt.show()

(height, width) = image.shape[:2]
angle = 45
center = (width // 2, height // 2)

M_rotation = cv2.getRotationMatrix2D(center, angle, 1)
rotated_image = cv2.warpAffine(
    image, M_rotation, (width, height)
)

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))
plt.title("Rotated Image")
plt.axis('off')
plt.show()

x, y, w, h = 100, 100, 200, 150
cropped_image = image[y:y+h, x:x+w]

plt.figure(figsize=(8, 6))
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))
plt.title("Cropped Image")
plt.axis('off')
plt.show()
```

## Output Screenshots

### 1. Original Image
<img width="1322" height="546" alt="image" src="https://github.com/user-attachments/assets/b4cb4969-0dfc-4182-a847-e2766e1820de" />


### 2. Translated Image
<img width="1367" height="555" alt="image" src="https://github.com/user-attachments/assets/f7a81f52-d596-4437-ae88-20f2ee8c6846" />


### 3. Scaled Image
<img width="1357" height="420" alt="image" src="https://github.com/user-attachments/assets/4a947e41-8b0b-4471-9707-93af1affe297" />


### 4. Sheared Image
<img width="1343" height="567" alt="image" src="https://github.com/user-attachments/assets/fe02e280-7c6e-4ab0-bdfa-80128eef429b" />


### 5. Reflected Image
<img width="1357" height="548" alt="image" src="https://github.com/user-attachments/assets/8e44d762-ee04-4bdd-804c-3ef94163497f" />


### 6. Rotated Image
<img width="1355" height="550" alt="image" src="https://github.com/user-attachments/assets/bd98d7c3-54b8-421c-8e33-f909aca0a1dc" />


### 7. Cropped Image
<img width="1366" height="552" alt="image" src="https://github.com/user-attachments/assets/b72bbfe7-c31c-4784-b7ba-b13f2903f302" />


## Result
Thus, various image transformations such as translation, scaling, shearing, reflection, rotation and cropping were successfully performed using OpenCV and Python.
