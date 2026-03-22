## Name : Madhan c
## Reg NO : 212224240081

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

## Program and Output:
## Name :AJAYRAJA RATHINAM T
## Reg no :212224240006

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

#Load face image
faceImage = cv2.imread("a.png")
plt.imshow(faceImage[:,:,::-1]); plt.title("Face")
print("Face shape:", faceImage.shape)

glassJPG = cv2.imread("b.png")
plt.imshow(glassJPG[:,:,::-1]); plt.title("glassJPG")
print("Glass shape:", glassJPG.shape)

glassBGR = glassJPG[:,:,0:3]
glassGray = cv2.cvtColor(glassBGR, cv2.COLOR_BGR2GRAY)
_, glassMask1 = cv2.threshold(glassGray, 240, 255, cv2.THRESH_BINARY_INV)  # detect non-white

plt.figure(figsize=[15,15])
#Show sunglasses color channels
plt.subplot(121)
plt.imshow(glassBGR[:,:,::-1])  # BGR → RGB
plt.title('Sunglass Color channels')

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Load images
faceImage = cv2.imread("a.png")
glassPNG  = cv2.imread("b.png", cv2.IMREAD_UNCHANGED)

if faceImage is None or glassPNG is None:
    print("Error loading images")
    exit()

face_h, face_w, _ = faceImage.shape

# Resize glasses (slightly smaller looks more natural)
new_w = int(face_w * 0.38)
new_h = int(new_w * glassPNG.shape[0] / glassPNG.shape[1])
glass_resized = cv2.resize(glassPNG, (new_w, new_h))

# Split channels
glass_rgb = glass_resized[:, :, :3]
alpha = glass_resized[:, :, 3] / 375.0

x = int(face_w * 0.32)
y = int(face_h * 0.22)

roi = faceImage[y:y+new_h, x:x+new_w]

for c in range(3):
    roi[:, :, c] = (alpha * glass_rgb[:, :, c] +
                    (1 - alpha) * roi[:, :, c])

faceImage[y:y+new_h, x:x+new_w] = roi

plt.figure(figsize=(6,8))
plt.imshow(cv2.cvtColor(faceImage, cv2.COLOR_BGR2RGB))
plt.axis("off")
plt.show()

```
## OUTPUT
<img width="375" height="460" alt="image" src="https://github.com/user-attachments/assets/f0be95db-f418-4171-bde1-d3a223a778e4" />
<img width="715" height="816" alt="image" src="https://github.com/user-attachments/assets/0f396f55-439d-4c21-9173-ef143c0b8613" />






