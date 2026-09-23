# -License-Plate-Detection-using-OpenCV-and-Haar-Cascade-Classifier
# Name: SHARVESHWARAN M
# Register Number: 212224240150
# Aim
To implement a License Plate Detection system using OpenCV and Haar Cascade Classifier, draw bounding boxes, crop the detected region, and blur the license plate to improve privacy. The detection accuracy is improved by tuning Haar Cascade parameters.

# Software Used
Python 3.7 or above

OpenCV (opencv-python)

NumPy

Matplotlib

Jupyter Notebook (Anaconda)

Haar Cascade File: haarcascade_russian_plate_number.xml

# Algorithm
Import necessary libraries such as OpenCV and Matplotlib

Read the input vehicle image

Convert the original image to grayscale for faster computation

Load the Haar Cascade classifier for license plate detection

Detect license plate using detectMultiScale function

Draw rectangle around detected area

Crop the detected region using numpy slicing with (x, y, w, h) values

Apply median blurring on the cropped region

Replace the original region with blurred version

Display final result using Matplotlib

# Program
```

import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread('car.png')
def display(img):
    fig = plt.figure(figsize=(12, 10))
    ax = fig.add_subplot(111)
    ax.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
    plt.show()
def detect_plate(img):
    img_copy = img.copy()

    gray = cv2.cvtColor(img_copy, cv2.COLOR_BGR2GRAY)

    plates = plate_cascade.detectMultiScale(
        gray,
        scaleFactor=1.1,
        minNeighbors=4
    )

    for (x, y, w, h) in plates:
        cv2.rectangle(
            img_copy,
            (x, y),
            (x + w, y + h),
            (0, 255, 0),
            3
        )

    return img_copy




def detect_and_blur_plate(img):
    img_copy = img.copy()

    gray = cv2.cvtColor(img_copy, cv2.COLOR_BGR2GRAY)

    plates = plate_cascade.detectMultiScale(
        gray,
        scaleFactor=1.1,
        minNeighbors=4
    )

    for (x, y, w, h) in plates:
        roi = img_copy[y:y+h, x:x+w]

        blurred_roi = cv2.medianBlur(roi, 15)

        img_copy[y:y+h, x:x+w] = blurred_roi

    return img_copy
```
<img width="771" height="1003" alt="image" src="https://github.com/user-attachments/assets/0b3902e6-e4e2-4d0a-b85b-33e58d97e04e" />
<img width="712" height="890" alt="image" src="https://github.com/user-attachments/assets/f1587bc5-29dd-448b-9ba4-76a1f090c240" />
<img width="666" height="866" alt="image" src="https://github.com/user-attachments/assets/bf1c6b04-f7b0-413c-9624-9a6b930a1e4b" />


# Modification Done
Parameter tuning was performed by adjusting scaleFactor and minNeighbors values in detectMultiScale to improve accuracy and reduce false detections. Median blur was applied to protect license plate information.

# Result
The License Plate Detection system was successfully implemented using OpenCV and Haar Cascade. The detected license plate region was blurred using median filtering. The modified values improved overall detection performance and output quality.

# Conclusion
This workshop demonstrates how classical computer vision methods like Haar Cascades can be used for real-time applications such as automated toll systems, smart parking, and traffic surveillance. Proper preprocessing and parameter tuning significantly improve detection results.
