# Dataset Collection Tool
This script was developed to capture images to meet the custom dataset requirement.
It uses OpenCV to capture images from a webcam and organizes them into class-specific folders.
The tool was used to create a dataset with the following object categories:
- Phone
- Book
- Calculator
- Clock
- Headphones


## WORKING
- Creates folders for all the object classes
- A menu appears, allowing the user select which object they wants to capture and the webcam feed opens in a window 
- Press **s** to save the image and **q** or **esc** to exit 
- The image is preprocessed
  - Centre cropped to a square 
  - Resized into 224 x 224 pixels
- Every image is saved in its corresponding folder
  - Example: dataset/phone/phone_001.jpg and so on.


## PURPOSE
The goal of this tool was to dataset creation for image classification. Taking and transferring every image using a phone camera was quite tiring, so this tool was created to speed up the collection process and reduce the overall workload.


