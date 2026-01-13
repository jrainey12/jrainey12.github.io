---
layout: page
title: DartsCV
description: Automated Darts Scoring System
main_title: <h1 align=center>DartsCV</h1><hr>
main_description: <h2 align=center> Automated Darts Scoring with Computer Vision</h2><hr>
img: assets/img/5.jpg
importance: 3
category: fun
---

<style>
h2   {
     color: #429435;
     font-size:180%;
     }
</style>

DartsCV is an experimental computer vision project that explores the automation of dart scoring using low-cost embedded hardware and OpenCV.
The system employs two Raspberry Pi boards, each equipped with a camera, to track dart impacts on a standard dartboard. Through image processing and geometric calibration, the software estimates the impact position of each dart and calculates the score automatically.

The project demonstrates the feasibility of applying real-time vision algorithms to a casual gaming setup using minimal hardware.
The project was initially completed in 2020 and disasembled in 2021, but has been reopen to rebuild it and make improvements using updated hardware and techniques.

<br>
## System Design
---

The current setup consists of:

- Two Raspberry Pi units with Pi Cameras (or alternatively, USB webcams)

- A Python backend utilizing OpenCV, NumPy, and scikit-image for image capture and processing

- A Qt5-based graphical interface for game management and visualization

- Paramiko for SSH-based communication between devices

One Raspberry Pi handles the main user interface, while the second assists with synchronized camera capture. Images from both cameras are used to triangulate the dart’s impact location on the board.

<br>
## Features
---

- Automated scoring for X01 (standard darts game)

- Support for multi-camera input (Pi Cameras or USB webcams)

- Modular code structure for integrating new dart games

- Remote UI via SSH with X11 forwarding

<br>

## Tech Stack
---

**Languages & Frameworks:** Python, OpenCV, Qt5

**Hardware:** 2x Raspberry Pi, Pi Cameras / USB Webcams

**Libraries:** NumPy, scikit-image, Paramiko

<br>
## Current Challenges
---

- Improving dart detection and segmentation

- Handling variations in impact angle and lighting

- Enhancing camera calibration for 3D triangulation

- Improved camera mounting using custom 3D printed mounts. 

<br>
##  Looking Ahead
---

Future plans include:

- Implementation on a single Rasberry Pi (Pi 5 with two cameras)

- Fully autonomous operation with a local display and touchscreen controls

- Dedicated lighting controlled by Pi, used for illumination, feedback and more complex interactions.

- Statistical analysis: hit accuracy, consistency, groupings, average score per round, etc. with visuallations.
- Broader support for multiple darts games

View on [GitHub](https://github.com/james-rainey/darts_cv).
