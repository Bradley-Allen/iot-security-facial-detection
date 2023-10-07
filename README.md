# IoT Security System with Facial Detection
Made using:
- Python
- XML (to store ML data)
- Haar Cascades
- Raspberry Pi 3 Model B
- Reed Switch
- Desktop Camera

## Description
When a door or window is opened, the reed switch attached will send an electrical signal to the Raspberry Pi, which turns on the camera and attempts to detect any faces. If faces are detected and there is a known face detected, no notification will be send, however
 if an unknown face without detecting a known face or no faces are detected before the timeout, a notification will be sent using PushBullet API to the registered phone.

## Technical Walkthrough
- Prior to setting up hardware, facial data is encoded into a .pickle file using **encode_faces.py** using **haarcascade_frontalface_default.xml** as data points
- Raspberry Pi is hooked up to reed switches, using defined pins and executes **pi_face_recognition.py**
- Camera is inserted into USB port on Pi
- As driver program runs, any signal on pins detect door opening, which will automatically turn on camera and use .pickle file to detect any known faces
- If known face is detected, system resets and listens for signal again
- If unknown face (without a known face) or no face is detected before timeout, the program sends a notification through WiFi connection using PushBullet API to a registered device (in driver file), then system resets and listens for signal again
