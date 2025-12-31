# Real-Time Face Detection with OpenCV

**Live face detection using webcam and OpenCV**

## Quick Start
1. Open `Face_Detection_project-Python.ipynb`
2. Run all cells
3. Press **ESC** to stop

## How It Works
1. Capture webcam frames
2. Convert to grayscale
3. Detect faces 
4. Draw green rectangles
5. Display live output

## Parameters
| Parameter | Value | Purpose |
|-----------|-------|---------|
| scaleFactor | 1.1 | Scale reduction |
| minNeighbors | 5 | Accuracy |
| minSize | (30,30) | Min face size |

## Applications
- 🔒 Security systems
- 📋 Attendance systems
- 🔑 Face unlock
- 🤖 AI & Robotics

## Complete Code
import cv2

facecap = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')

if facecap.empty():
    print("Error: Haarcascade not loaded.")
    exit()

videocap = cv2.VideoCapture(0)

if not videocap.isOpened():
    print("Camera not detected")
    exit()

while True:
    ret, videodata = videocap.read()

    if not ret:
        print("Failed to grab frame")
        break

    gray = cv2.cvtColor(videodata, cv2.COLOR_BGR2GRAY)

    faces = facecap.detectMultiScale(gray, scaleFactor=1.1, minNeighbors=5, minSize=(30, 30))

    for (x, y, w, h) in faces:
        cv2.rectangle(videodata, (x, y), (x+w, y+h), (0, 255, 0), 2)

    cv2.imshow('Video live', videodata)

    # Press ESC to exit
    if cv2.waitKey(10) & 0xFF == 27:
        break

videocap.release()
cv2.destroyAllWindows()


## Requirements
opencv-python

notebook
