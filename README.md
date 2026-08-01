# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

##  Program

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.
import cv2
import numpy as np
import matplotlib.pyplot as plt
# Step 1: Load the image
image = cv2.imread('/content/SPIDERMAN.jpg')  # Load the image from file
# Display the original image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  # Convert BGR to RGB for correct display
plt.title("Original Image")  
plt.axis('off')


<img width="554" height="554" alt="SPIDERMAN" src="https://github.com/user-attachments/assets/3ffde396-44fa-419c-90d0-d475461f280c" />


### Step 2:
Read the input image in color mode.
# Step 2: Image Translation
tx, ty = 100, 50  # Translation factors (shift by 100 pixels horizontally and 50 vertically)
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  # Translation matrix: 
# [1, 0, tx] - Horizontal shift by tx
# [0, 1, ty] - Vertical shift by ty
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))  
plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  # Display the translated image
plt.title("Translated Image")  
plt.axis('off')
<img width="721" height="523" alt="Screenshot 2026-08-01 112515" src="https://github.com/user-attachments/assets/96464144-4f10-4554-9727-9d450b3516f6" />
### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

# Step 3: Image Scaling
fx, fy = 5.0, 2.0  # Scaling factors (1.5x scaling for both width and height)
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)
# resize: Resize the image by scaling factors fx, fy
# INTER_LINEAR: Uses bilinear interpolation for resizing
plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))  # Display the scaled image
plt.title("Scaled Image")  # Set title
plt.axis('off')

<img width="682" height="347" alt="Screenshot 2026-08-01 112728" src="https://github.com/user-attachments/assets/d9d9e890-1888-4703-b8bd-86d7d1e28867" />

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  
# Step 4: Image Shearing
shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  # Shearing matrix
# The matrix shears the image by a factor of 0.5 in both x and y directions
# [1, 0.5, 0] - Shear along the x-axis (horizontal)
# [0.5, 1, 0] - Shear along the y-axis (vertical)
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))
plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  # Display the sheared image
plt.title("Sheared Image")  # Set title
plt.axis('off')
<img width="726" height="530" alt="Screenshot 2026-08-01 112814" src="https://github.com/user-attachments/assets/d4895123-752a-4867-8fbf-199dc21678a1" />

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  
# Step 5: Image Reflection
reflected_image = cv2.flip(image, 2)  # Flip the image horizontally (1 means horizontal flip)
# flip: 1 means horizontal flip, 0 would be vertical flip, -1 would flip both axes
plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB))  # Display the reflected image
plt.title("Reflected Image")  # Set title
plt.axis('off')

<img width="712" height="533" alt="Screenshot 2026-08-01 112911" src="https://github.com/user-attachments/assets/e7f2b57d-675f-49ae-9696-11c75a1f3dd9" />

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  
# Step 6: Image Rotation
(height, width) = image.shape[:2]  # Get the image height and width
angle = 45  # Rotation angle in degrees (rotate by 45 degrees)
center = (width // 2, height // 2)  # Set the center of rotation to the image center
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  # Get the rotation matrix
# getRotationMatrix2D: Takes the center of rotation, angle, and scale factor (1 means no scaling)
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  # Apply rotation
plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  # Display the rotated image
plt.title("Rotated Image")  # Set title
plt.axis('off')
<img width="713" height="537" alt="Screenshot 2026-08-01 113017" src="https://github.com/user-attachments/assets/8831fa29-1bb4-4fcb-9bba-537cb330d386" />

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

x, y, w, h = 100, 100, 200, 150  # Define the top-left corner (x, y) and the width (w) and height (h) of the crop
# Cropping the image from coordinates (x, y) to (x+w, y+h)
cropped_image = image[y:y+h, x:x+w]
# The crop is performed by slicing the image array in the y and x directions
plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB))  # Display the cropped image
plt.title("Cropped Image")  # Set title
plt.axis('off')

<img width="712" height="532" alt="Screenshot 2026-08-01 113205" src="https://github.com/user-attachments/assets/15cd7928-09fc-4354-9a9e-c9ee9339a579" />


### Developed By:JOHN PALL M
**Name:** ____________________________  

### Register No:212224040140
____________________________  

---

##  Output
<img width="554" height="554" alt="SPIDERMAN" src="https://github.com/user-attachments/assets/e9b5e1c9-7e13-4211-8d78-57ba6cc2064b" />
<img width="712" height="532" alt="Screenshot 2026-08-01 113205" src="https://github.com/user-attachments/assets/df090b2e-8b03-4ed6-a924-d21874efea37" />
<img width="713" height="537" alt="Screenshot 2026-08-01 113017" src="https://github.com/user-attachments/assets/b05c2c0d-a96a-40cf-b7a9-ca4b30d7b647" />
<img width="712" height="533" alt="Screenshot 2026-08-01 112911" src="https://github.com/user-attachments/assets/404bc560-9591-4c1f-8ad0-bcd591041387" />
<img width="726" height="530" alt="Screenshot 2026-08-01 112814" src="https://github.com/user-attachments/assets/2ac112dc-c803-42b7-8eae-b0059407a49f" />
<img width="687" height="345" alt="Screenshot 2026-08-01 112721" src="https://github.com/user-attachments/assets/5184ccaa-4eb0-4de8-9998-0a9f690a6aef" />
<img width="721" height="523" alt="Screenshot 2026-08-01 112515" src="https://github.com/user-attachments/assets/9ee316fb-e7ad-4eaa-a44c-3eb27ef23595" />

### Image Translation
- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
