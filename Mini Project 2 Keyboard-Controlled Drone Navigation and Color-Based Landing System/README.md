# Keyboard-Controlled Drone Navigation and Color-Based Landing System

Author: Anushka Gangadhar Satav

Masters Student in Robotics and Autonomous Systems (AI), Arizona State University, Tempe, Arizona, USA  

Email: [anushka.satav@asu.edu](mailto:anushka.satav@asu.edu) 

![videodemo2](https://github.com/user-attachments/assets/fb691e31-f84c-4127-87b7-ee89b8159a57)

## Keywords
- Parrot Mambo  
- MATLAB  
- Color Threshold  
- Color Detection  
- Real-time Image Processing  
- UAV Navigation  
- Keyboard Control  
- Drone Soft Landing  

## Abstract
Unmanned aerial vehicles (UAVs), such as the Parrot Mambo mini drone, are increasingly vital for tasks involving autonomous navigation, object detection, and precise maneuvering. 
This project focuses on developing a keyboard-controlled navigation system coupled with a color-based landing mechanism for the Parrot Mambo drone.
The primary goal was to enable the drone to hover and navigate toward a designated colored block—specified as Red, Green, Blue, or Yellow—using keyboard inputs, followed by a slow and controlled landing upon detecting the target color. 
Real-time image data from the drone’s onboard camera was processed in MATLAB using advanced color segmentation techniques based on the RGB color model. 
To ensure robust detection under varying lighting conditions, thresholding methods were refined, and morphological operations were applied to minimize noise and enhance accuracy.
The system successfully demonstrated manual navigation via keyboard commands and autonomous landing triggered by color recognition, ensuring a smooth descent without abrupt stops or crashes. 
This work highlights the integration of computer vision and UAV control, offering a foundation for applications in robotics, automation, and surveillance.
Potential future improvements include adapting the system for dynamic environments and incorporating machine learning for enhanced object recognition, paving the way for practical uses such as search-and-rescue operations or industrial monitoring.


---

## 1. Introduction
Drones have gained significant attention in recent years due to their versatility and applications in various fields, including aerial photography, surveillance, and automation. The Parrot Mambo, a compact and beginner-friendly drone, serves as an excellent platform for learning and experimentation. With its downward-facing camera, onboard sensors, and stable flight capabilities, it provides a foundation for developing computer vision algorithms.

This project focuses on utilizing the Parrot Mambo drone for color-based object detection and controlled landing, demonstrating its potential for vision-based tasks. The primary objective of this project is to detect objects of specific colors—Red, Green, Blue, and Yellow—using the Parrot Mambo's camera feed and process the data in MATLAB.

By leveraging image processing techniques, we extract meaningful color information from captured images, allowing the drone to recognize and track objects. The combination of color segmentation, thresholding, and morphological operations ensures accurate and efficient object detection. Additionally, the drone was controlled manually via keyboard inputs to navigate toward a specific color block. Upon successful color identification, the drone executed a slow descent and landed smoothly.

With its auto take-off and landing features, FPV mode, and onboard stabilization sensors, the Parrot Mambo drone provides a reliable platform for real-time image processing. This project aims to develop a color detection system that not only recognizes objects but also enables interactive drone control based on keyboard navigation.

---

## 2. Method
This section details the step-by-step approach to designing and implementing a keyboard-controlled navigation and color-based landing system for the Parrot Mambo Mini drone using MATLAB and Simulink. The objective was to enable the drone to hover and navigate via keyboard commands, detect specific-colored blocks (Red, Green, Blue, or Yellow), and execute a slow, controlled landing upon successful detection.

The methodology integrates hardware setup, image processing, flight control modifications, and testing phases. The process leverages a pre-existing MATLAB example, *"Path Planning Using Keyboard Control for Parrot Mini drone"* as a foundation, with custom modifications to meet the project requirements. Below is a detailed breakdown of the methodology.

### 2.1 Setting up the Parrot Mambo Mini drone
The experiment began with configuring the Parrot Mambo Mini drone for stable flight and connectivity with MATLAB. The drone’s firmware was updated to ensure compatibility with MATLAB’s Hardware Support Package for Parrot Minidrones. A Bluetooth connection was established between the drone and the host computer running MATLAB R2023b (or the latest available version as of February 2025). Initial flight tests were conducted in a controlled indoor environment to verify basic functionality, such as take-off, hovering, and landing, using MATLAB’s built-in `parrot drone` examples.

The drone’s onboard camera was calibrated to capture clear images under the lab’s lighting conditions, accounting for potential variations in brightness and shadows. The Simulink template for the Parrot Mini drone was loaded, which contained predefined blocks for image processing and flight control.


![WhatsApp Image 2025-02-22 at 20 43 18_bb45304c](https://github.com/user-attachments/assets/b653b7d6-3441-4811-b5fb-c9f828c124d7)

### 2.2 Image Processing and Color Detection Implementation
To begin the process, Simulink was launched, and the Parrot Mini drone template was selected to establish the framework for the image processing model. Once the template was loaded, the image processing block was thoroughly analyzed to understand its structure and workflow. This step was crucial to ensure that the model was correctly configured for integration with the drone’s camera system.

Following the guidelines provided in the MATLAB Image Processing Guide, a vision-based algorithm was developed and implemented within the image processing block. The algorithm was designed to detect and process color information from the captured images. The following key steps were implemented:

- **Color Segmentation:** MATLAB’s Color Thresholder App was used to tune RGB thresholds for detecting the target colors.
- **Mask Generation:** A binary mask was generated for each frame, isolating the target color while minimizing interference from ambient lighting.
- **Function Integration:** The color detection algorithm was encapsulated into a MATLAB function, which was then imported into the Simulink model as an image processing block.


![Picture1](https://github.com/user-attachments/assets/701e35b0-c582-4a40-a3b4-6bd8d8f11eca)


### 2.3 Modifying Flight Controller for Autonomous Operation
The flight control logic was modified to integrate the color detection signal into the navigation and landing decision-making process. The drone was manually navigated over a colored block using keyboard controls. Once the detected color matched the predefined target, the drone initiated a controlled descent.

To ensure a smooth landing, adjustments were made to prevent abrupt stopping or sudden altitude drops. The modifications included refining the throttle control and descent trajectory to allow a gradual landing procedure.

---

## 3. Conclusion
This project successfully demonstrated a keyboard-controlled navigation and color-based landing system for the Parrot Mambo Mini drone. 
By integrating real-time image processing with UAV control, the system enabled precise maneuvering and soft landings based on color detection. 
Future improvements could include the addition of dynamic object tracking, machine learning-based classification, and enhanced adaptability to varying environmental conditions.

![1](https://github.com/user-attachments/assets/34c81f20-f4eb-479e-8ff0-898b2a3e473c)

---

## References
- MATLAB Documentation on Parrot Minidrones  
- Image Processing and Computer Vision Toolbox  
- UAV Path Planning and Flight Control in MATLAB  

For any queries, contact: **[anushka.satav@asu.edu](mailto:anushka.satav@asu.edu)**
