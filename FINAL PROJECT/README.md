# Final Project : Vision-Guided Precision Landing of a Parrot Mambo Minidrone on a Mobile Line-Follower Platform Using Simulink

**Author:** Anushka Satav G  

**Masters Student in Robotics and Autonomous Systems (AI)**  

**Arizona State University, Tempe, AZ, USA**  

---

![Parrot Mambo Landing Demo](https://github.com/user-attachments/assets/134625fe-b997-42a7-aa94-ea749ca05c97)

---

## Keywords
- Parrot Mambo
- MATLAB
- Simulink
- HSV Color Segmentation
- Blob Analysis
- Real-time Image Processing
- Autonomous UAV Navigation
- Computer Vision
- RGB Line Detection
- Flight Control System
- Drone Precision Landing

---
## Key Learnings & Challenges 📌

### Problem Statement
Enable a Parrot Mambo Minidrone to autonomously detect, track, and land on a moving colored platform mounted on a line-follower robot using its onboard downward-facing camera and Simulink-based real-time image processing — with reliable performance under variable indoor lighting.

---

### Key Takeaways

- **Lighting sensitivity was a major challenge** for color detection. Initial RGB segmentation was unstable under shadows and glare.
- **Switched to HSV color space**, which provided better mask stability in variable lighting since hue and saturation are less affected by brightness changes.
- **Created and tested multiple threshold masks using images from different lighting conditions** (bright, dim, mid-shadow) to fine-tune detection performance.
- **Integrated HSV thresholds as functions inside Simulink’s image processing block**, improving real-time detection reliability.

![image](https://github.com/user-attachments/assets/c3beb745-ddb8-461f-a9a4-619afacd9093)

- **Used Median filtering and Blob Analysis** to clean noisy masks and reliably extract the platform’s centroid.
- **Stateflow was pivotal for managing autonomous flight states** (Hover → Cruise → Land) and ensuring safe, gradual descents only when alignment conditions held consistently.
- **Soft landing was the hardest part** — required carefully tuned position error thresholds, descent rates, and alignment stability timers to avoid overshooting or lateral drift.
- This project demonstrated how **tight coordination between perception and control loops** is crucial for vision-guided autonomy, even in simple UAV-ground interaction tasks.

---

## Abstract

This project implements a vision-guided autonomous landing system for the Parrot Mambo Minidrone using MATLAB and Simulink. The system detects a colored landing platform mounted on a moving ground vehicle (line-follower robot) and autonomously lands on it using real-time onboard image processing. HSV color segmentation and blob analysis are performed to identify and track the platform using the drone’s downward-facing camera. A unified Stateflow-based control logic governs all flight phases — hover, cruise, and descent — enabling dynamic path planning and precise soft landing without external supervision. The project successfully demonstrates the integration of real-time image-based feedback with onboard flight control for UAV-ground coordination tasks.

---

## Introduction

Unmanned Aerial Vehicles (UAVs) are increasingly used for tasks requiring real-time sensing and autonomous control. The Parrot Mambo Minidrone, with its programmable Simulink-compatible platform and integrated camera, provides an accessible solution for developing and testing vision-based navigation and control algorithms.

This project extends foundational drone control to a complex scenario: autonomously detecting and landing on a moving line-follower robot platform. The system processes live video feed in MATLAB/Simulink, performing color segmentation and blob analysis to locate the landing platform in real time. Positional errors between the platform centroid and image center guide horizontal motion adjustments, while a Stateflow-based controller manages all flight states and initiates descent once alignment and proximity conditions are met.

---

## Method

### 2.1 Drone Setup and Configuration
The Parrot Mambo Minidrone was interfaced with MATLAB via the Parrot Minidrone Support Package. Initial manual flight tests confirmed stable communication and functionality. The drone’s downward camera was calibrated for consistent indoor lighting conditions.

---

### 2.2 Image Processing and Platform Detection
An HSV color segmentation pipeline was developed using MATLAB’s Color Thresholder App to detect Red or Green landing platforms. Real-time video frames were processed in Simulink to:
- Apply HSV color thresholding  
- Generate binary masks  
- Filter noise via median filtering  
- Perform blob analysis to extract centroid positions  

The computed `x_error` and `y_error` values represented lateral deviations between the platform and image center.

---

### 2.3 Autonomous Tracking and Descent Control
A Stateflow chart managed the drone’s autonomous flight behavior:
- **Hover:** Stabilize after takeoff  
- **Cruise:** Track the platform’s centroid using proportional control on `x_error` and `y_error`, gradually reducing altitude  
- **Land:** Once alignment and altitude thresholds are met, stop horizontal motion and execute vertical descent  

The entire decision-making logic was embedded within the Stateflow chart, allowing fully autonomous onboard operation.

---

### 2.4 Simulink Model Integration and Testing
The image processing, path planning, and motion control subsystems were integrated into a unified Simulink model. Simulations were conducted in Simulink’s 3D Animation environment to validate tracking, descent timing, and control parameters. The validated model was then deployed on the Parrot Mambo for hardware testing in an indoor environment with a line-follower robot.

---

## Results and Discussion

### 3.1 Platform Detection and Tracking
The HSV segmentation and blob analysis pipeline reliably detected the platform under varied indoor lighting. Median filtering minimized noise, and the proportional control strategy ensured stable and responsive tracking without oscillations.

---

### 3.2 Flight Stability and Control
During cruise, the drone smoothly adjusted its position in response to visual feedback. State transitions between hover, cruise, and landing phases were clean and reliable, ensuring stable operation throughout.

---

### 3.3 Precision Landing Performance
Descent initiation occurred only after alignment was consistently maintained. Vertical descent was gradual and controlled, with minimal lateral drift. Across multiple test runs, the drone consistently landed near the platform’s center.

---

## Conclusion

This project successfully demonstrated real-time, vision-guided precision landing of a Parrot Mambo Minidrone on a moving platform using MATLAB and Simulink. The combination of HSV color segmentation, blob analysis, centroid error computation, and a Stateflow-based control system enabled fully autonomous onboard operation. The system’s modularity allows for future extensions in multi-UAV coordination, dynamic target tracking, and reinforcement learning-based flight control.

---

## References
1. [Parrot Minidrone Setup & Configuration](https://www.mathworks.com/help/simulink/setup-and-configuration-parrot.html)
2. [Color Detection and Landing Example](https://www.mathworks.com/help/simulink/supportpkg/parrot_ref/color-detection-and-landing-parrot-example.html)
3. [Getting Started with Parrot Minidrone Vision](https://www.mathworks.com/help/simulink/supportpkg/parrot_ref/getting-started-with-parrot-minidrone-vision.html)
4. [Demo Video](https://youtu.be/UlDknqrtAHM?feature=shared)
5. [Simulink Path Planning Example](https://www.mathworks.com/help/simulink/supportpkg/parrot_ref/path-planning-keyboard-example.html)
6. [Global Minidrone Challenge Resources](https://www.mathworks.com/academia/students/competitions/minidrones/global-drone-student-challenge.html)

---

## Author's Bio

**Anushka Satav G** is a master’s student at Arizona State University pursuing Robotics and Autonomous Systems (AI). She holds a Bachelor of Technology in Robotics and Automation from MIT World Peace University, Pune, India.  

She can be contacted at: [anushka.satav@asu.edu](mailto:anushka.satav@asu.edu)
