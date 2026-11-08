# NebulaHeart 3D

A real-time, webcam-controlled 3D particle visualization built with Python. MediaPipe tracks one hand, and the detected gesture changes 1,500 particles into a rotating nebula, Saturn, an “I LOVE YOU” message, or a heart. Hand position also moves the formed objects around the scene.

## Features

- Four gesture-controlled particle formations:
  - **Default / open hand** — blue rotating cosmic particles
  - **Index finger raised** — an orange planet with golden rings
  - **Peace sign** — a cyan “I LOVE YOU” formation
  - **Fist** — a pink heart
- Real-time hand tracking through the default webcam
- 3D rendering with Pygame and PyOpenGL
- Camera preview with detected hand landmarks and the active mode

## Requirements

- Python 3.11 (recommended; the project notes specify this version)
- A webcam
- A graphics environment that supports Pygame and OpenGL

## Setup

Create and activate a virtual environment. For example, with Conda:

```bash
conda create -n space_gesture python=3.11 -y
conda activate space_gesture
```

Install the dependencies:

```bash
pip install opencv-python mediapipe pygame PyOpenGL numpy==1.26.4
```

The NumPy version is pinned to 1.26.4, as specified in the project notes for compatibility with the OpenGL setup.

## Run

From the repository directory, start the application:

```bash
python index.py
```

On macOS, if the camera or GUI does not start correctly, try:

```bash
pythonw index.py
```

Allow the application to access your camera when prompted. The app opens a 3D visualization window and a separate **Hand Sensor Monitor** camera preview.

## Gesture controls

| Gesture | Formation | Appearance |
| --- | --- | --- |
| Default (including an open hand) | Cosmic particles | Blue particles rotating in place |
| Index finger raised, other fingers folded | Saturn | Orange sphere with golden rings |
| Peace sign (index and middle fingers raised) | “I LOVE YOU” | Cyan text made from particles |
| Fist | Heart | Pink heart made from particles |

The planet, text, and heart formations follow the detected hand position. The cosmic mode remains centered. Gesture detection is based on the relative vertical positions of the four non-thumb fingertips.

## Exit

- Press **Esc** or close the Pygame window to quit.
- Alternatively, focus the camera preview and press **q**.

## Project files

- `index.py` — gesture detection, camera processing, particle formations, and 3D rendering.
- `catatan.py` — project setup and technical notes (in Indonesian).

## Troubleshooting

- **No camera image:** Check that a webcam is connected and that the app has camera permission. The program opens camera device `0`.
- **The camera preview appears, but gestures do not switch modes:** Keep one hand clearly visible and well lit; the tracker is configured for one hand.
- **GUI or OpenGL startup problems on macOS:** Try launching with `pythonw index.py` and ensure your Python/Pygame installation has access to a graphical session.
- **Dependency compatibility problems:** Use Python 3.11 and the NumPy version pinned in the install command.
