# USB-camera-using-raspberrypi3
To get live feed us from USB camera using raspberrypi3 

Installation of usbcamera on pi3

1)Update and upgrade:

sudo apt-get update
sudo apt-get upgrade

2)Install v4l-utils:
Package for providing utilities for video devices which is essential for working with USB cameras

sudo apt-get install v4l-utils

3)Install fswebcam or guvcview: for capturing images from a webcam

sudo apt-get install fswebcam
sudo apt-get install guvcview

4)Install opencv:

sudo apt-get install python3-opencv

5}Install Python Dependencies:

sudo apt-get install python3-pip
pip3 install numpy opencv-python

6) Camera test: Plug in your USB camera and test it using v4l2-ctl for listing devices

v4l2-ctl --list-devices
or

 fswebcam to capture an image:
  
  fswebcam test_image.jpg

7) Run this code having:

import cv2
# Open the default camera
cap = cv2.VideoCapture(0)
if not cap.isOpened():
    print("Cannot open camera")
    exit()

while True:
    # Capture frame-by-frame
    ret, frame = cap.read()
    if not ret:
        print("Can't receive frame (stream end?). Exiting ...")
        break

    # Display the resulting frame
    cv2.imshow('frame', frame)
    if cv2.waitKey(1) == ord('q'):
        break
# When everything done, release the capture
cap.release()
cv2.destroyAllWindows()

8)Run this command to capture video feed from camera:
 
 python3 capture.py
