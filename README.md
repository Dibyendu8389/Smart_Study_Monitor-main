# Smart Study Monitor

A webcam-based study monitoring application that helps detect common distractions while a person is studying. It uses computer vision to detect:

- sleepy behavior (eyes closed for too long)
- face covering / hidden face
- phone usage

When a distraction is detected, the app shows a warning on screen and plays an alarm sound.

---

## Features

- Real-time webcam monitoring
- Face mesh detection for eye and face analysis
- YOLO object detection for cell phone detection
- Visual warnings on screen
- Audio alerts for sleep, face cover, and phone usage
- Works in a local desktop environment with a webcam

---

## Project Structure

```text
Smart_Study_Monitor-main/
├── app.py
├── alarm.mp3
├── faudio.mp3
├── paudio.mp3
├── yolov8n.pt
├── face_landmarker.task
├── hand_landmarker.task
└── README.md
```

### Main files

- `app.py` – Main application logic
- `yolov8n.pt` – YOLO model used for object detection
- `alarm.mp3`, `faudio.mp3`, `paudio.mp3` – sound files used for alerts

---

## Requirements

Before running the project, make sure you have:

- Windows 10 or 11
- A working webcam
- Speaker or audio output enabled
- Python 3.11 installed

Important:

- Python 3.14 may fail with `pygame` due to compatibility issues.
- The project was validated successfully with Python 3.11.

---

## Installation

### 1) Install Python 3.11

If you do not already have Python 3.11, install it from:

- https://www.python.org/downloads/release/python-3119/

or via winget:

```powershell
winget install --id Python.Python.3.11 -e --source winget
```

### 2) Open a terminal in the project folder

```powershell
cd "C:\path\to\Smart_Study_Monitor-main"
```

### 3) Create a virtual environment (recommended)

```powershell
py -3.11 -m venv .venv
.\.venv\Scripts\activate
```

### 4) Install dependencies

```powershell
py -3.11 -m pip install --upgrade pip
py -3.11 -m pip install opencv-python cvzone ultralytics pygame mediapipe
```

If you are using the virtual environment, this command is enough:

```powershell
python -m pip install --upgrade pip
python -m pip install opencv-python cvzone ultralytics pygame mediapipe
```

---

## How to Run

From the project folder:

```powershell
cd "C:\path\to\Smart_Study_Monitor-main"
py -3.11 app.py
```

If your virtual environment is active:

```powershell
python app.py
```

The camera window will open. Press `Q` to quit.

---

## What the App Does

The application continuously checks three conditions:

1. Sleep detection
   - Detects whether the user’s eyes remain closed for too long.
   - Shows a warning like “WAKE UP & STUDY!”

2. Face cover detection
   - Detects if the face is hidden or partially covered.
   - Shows a warning like “DONT COVER YOUR FACE!”

3. Phone detection
   - Uses YOLO to detect a mobile phone in the frame.
   - Shows a warning like “PUT THE PHONE AWAY!”

If one of these events is detected, the app plays an alarm sound.

---

## Troubleshooting

### ModuleNotFoundError: No module named 'cv2'

Install OpenCV:

```powershell
py -3.11 -m pip install opencv-python
```

### ModuleNotFoundError: No module named 'cvzone'

Install the missing package:

```powershell
py -3.11 -m pip install cvzone
```

### ModuleNotFoundError: No module named 'mediapipe'

Install MediaPipe:

```powershell
py -3.11 -m pip install mediapipe
```

### pygame compatibility issues

Use Python 3.11 instead of Python 3.14.

Example:

```powershell
py -3.11 app.py
```

### Webcam not opening

- Make sure the webcam is connected and not already used by another app.
- Check Windows privacy settings for camera access.
- Try closing other apps that may be using the camera.

### Audio not playing

Make sure:

- speakers are connected
- volume is on
- the following files exist in the project folder:
  - `alarm.mp3`
  - `faudio.mp3`
  - `paudio.mp3`

---

## Notes

- This project relies on GPU/CPU inference for face detection and object detection.
- The YOLO model file `yolov8n.pt` must remain in the project folder.
- The app is intended for local use and is most effective in a quiet environment with stable lighting.

---

## License

This project is provided as-is for educational or personal use. Please check the repository or original source for any license restrictions before commercial use.

---

## Quick Start

```powershell
cd "C:\path\to\Smart_Study_Monitor-main"
py -3.11 -m pip install --upgrade pip
py -3.11 -m pip install opencv-python cvzone ultralytics pygame mediapipe
py -3.11 app.py
```

If everything is set correctly, the webcam monitoring window should open and begin alerting when distractions are detected.
