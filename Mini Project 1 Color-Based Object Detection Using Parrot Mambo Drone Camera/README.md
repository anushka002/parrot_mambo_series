# Color-Based Object Detection Using Parrot Mambo Drone Camera

**Author:** Anushka Satav G 

**Masters Student in Robotics and Autonomous Systems (AI)**

**Arizona State University, Tempe, AZ, USA**

---
![Demo 1](https://github.com/user-attachments/assets/22020549-48d6-4dfe-9658-e8772a628fb7)
---

## Keywords
- Parrot Mambo
- MATLAB
- Color Threshold
- Color Detection
- Real-time Image Processing

---
## Abstract

Drones have become an essential tool for autonomous navigation, surveillance, and object detection in various applications. In this project, we utilized the Parrot Mambo drone, a lightweight and programmable quadcopter, to detect objects based on their color properties. The primary objective was to identify and track objects of specific colors—Red, Green, Blue, and Yellow—using the drone’s onboard camera. To achieve this, we leveraged MATLAB for image processing and object recognition. The drone captured real-time images, which were then processed using color segmentation techniques in MATLAB. The RGB color model was used to filter and isolate objects of the targeted colors, and a thresholding approach was applied to enhance detection accuracy. Additionally, basic morphological operations were implemented to reduce noise and improve the reliability of object identification. Through this approach, we successfully detected and highlighted the desired objects within the drone’s field of view. This project demonstrates the potential of computer vision and UAV-based object tracking for applications in robotics, automation, and smart surveillance. Future enhancements could include integrating machine learning algorithms for more robust detection and extending the system for real-world applications like autonomous search-and-rescue missions and industrial inspections.

---

## Introduction

Drones have gained significant attention in recent years due to their versatility and applications in various fields, including aerial photography, surveillance, and automation. 
The Parrot Mambo, a compact and beginner-friendly drone, serves as an excellent platform for learning and experimentation. With its downward-facing camera, onboard sensors, and stable flight capabilities, it provides a foundation for developing computer vision algorithms. 
This project focuses on utilizing the Parrot Mambo drone for color-based object detection, demonstrating its potential for vision-based tasks. 

The primary objective of this project is to detect objects of specific colors—Red, Green, Blue, and Yellow—using the Parrot Mambo's camera feed and process the data in MATLAB. 
By leveraging image processing techniques, we extract meaningful color information from captured images, allowing the drone to recognize and track objects. 
The combination of color segmentation, thresholding, and morphological operations ensures accurate and efficient object detection.

The project aims to develop a color detection system in real-time using Parrot Mambo drone's camera to identify red, green, blue, and yellow blocks from approximately 3 feet height. 
Upon successful color detection, the drone should respond by spinning its motors at minimal gain, demonstrating object recognition capabilities.

---

## Method

In this section, we outline the methodology used to enable the Parrot Mambo Mini drone to detect specific colours—Red, Green, Blue, and Yellow—using MATLAB and Simulink. 
The process involved multiple steps, including setting up the drone, utilizing MATLAB’s Color Thresholding App to create functions for detecting specific colours, and integrating these functions into Simulink’s image processing block.

### 2.1 Setting up the Parrot Mambo Mini drone
The drone was initially tested using example scripts from the MATLAB documentation. These scripts ensured proper connectivity and functionality. 
The Simulink template for the Parrot Mini drone was loaded, which contained predefined blocks for image processing and flight control.

![Parrot Mambo](https://github.com/user-attachments/assets/c75ea043-e7cd-4f99-86cc-fe95d257b89f)

---

### 2.2 Image Processing and Color Detection Implementation
Simulink was launched, and the Parrot Mini drone template was selected to establish the framework for the Image processing model. 
Once the template was loaded, the image processing block was thoroughly analyzed to understand its structure and workflow. 
The algorithm was designed to detect and process color information from the captured images.

---

### 2.3 Developing Color Detection Functions
MATLAB’s Color Thresholding App was used to generate functions for detecting specific colors. The images captured from the drone camera were used as input to train the thresholding algorithm.
Functions were exported to detect red, green, blue, and yellow colors separately.

---

### 2.4 Integrating Color Detection into Simulink 
The image processing block was updated to incorporate the generated functions for color detection. 
This integration allowed the system to process color information from the captured images.

---

### 2.5 Modifying Flight Controller for Autonomous Operation
The flight control logic was modified to ensure that the drone’s rotors would only activate when a specific color was detected by the camera. 
For example, when the blue detection function was activated, the drone would initiate movement only upon identifying a blue block.

---

## Results and Discussion

### 3.1 Image Processing Model- Development and Testing
Testing was performed first on static test images before moving to real-time video processing. The RGB thresholds were calibrated for each color with the following parameters:
- Red: R(205-255), G(0-140), B(0-140)
- Green: R(50-160), G(177-255), B(151-255)
- Blue: R(0-127), G(128-177), B(150-255)
- Yellow: R(235-255), G(216-255), B(124-216)

![color threshold BLUE](https://github.com/user-attachments/assets/de2d45a7-c2e7-40ac-9daf-271a78be0caf)

---

### 3.2 Testing on Parrot Mambo Mini Drone
Field testing with the Parrot Mambo drone revealed:
- Color detection successful only in consistent lighting
- Real-time processing performance: Acceptable with minimal lag
- Effective detection range: 1.5 - 2.5 feet optimal
- Best performance was achieved in controlled indoor lighting
- Motor response was reliable

![Picture2](https://github.com/user-attachments/assets/16d4b146-eb27-45f8-a2b3-3ac2d429d200)

---

## Conclusion

This project successfully demonstrated the implementation of a colour detection system using the Parrot Mambo drone's onboard camera and MATLAB/Simulink integration. Through the development and testing process, we achieved our primary objective of detecting specific-coloured objects (Red, Green, Blue, and Yellow) at a height of approximately 3 feet, with the drone responding through controlled motor movements upon successful detection.

Key findings:
1. RGB-based colour detection proved effective, though with limitations in varying lighting conditions.
2. Real-time processing and drone response were successfully implemented with minimal latency.
3. The integration of MATLAB’s Color Thresholder App with Simulink provided a robust platform.
4. Environmental factors, particularly lighting, were critical for system reliability.

---

## References
1. [MATLAB Parrot Mambo Documentation](https://www.mathworks.com/help/simulink/setup-and-configuration-parrot.html)
2. [Color Detection and Landing Parrot Example](https://www.mathworks.com/help/simulink/supportpkg/parrot_ref/color-detection-and-landing-parrot-example.html)
3. [Getting Started with Parrot Mini Drone Vision](https://www.mathworks.com/help/simulink/supportpkg/parrot_ref/getting-started-with-parrot-minidrone-vision.html)
4. [Video Link](https://github.com/user-attachments/assets/9515b37e-1e93-4d06-8ff7-d0def2713e78)

---

## Author's Bio

Anushka Satav is a master’s student at Arizona State University pursuing Robotics and Autonomous Systems (AI). 
She has completed her Bachelor of Technology in Robotics and Automation at MIT World Peace University, Pune, India. 
She can be contacted at: [anushka.satav@asu.edu](mailto:anushka.satav@asu.edu)
