# Autonomous Line Following and Precision Landing Using Parrot Mambo Minidrone

Author: Anushka Gangadhar Satav  
Masters Student in Robotics and Autonomous Systems (AI), Arizona State University, Tempe, Arizona, USA  
Email: [anushka.satav@asu.edu](mailto:anushka.satav@asu.edu)

![videodemo3](https://github.com/user-attachments/assets/placeholder-for-demo.gif)

## Keywords
- Parrot Mambo  
- MATLAB  
- Simulink  
- Color Detection  
- RGB Line Following  
- Stateflow  
- Image Processing  
- Autonomous Landing  
- UAV Navigation  

---

## Abstract
Unmanned aerial vehicles (UAVs), such as the Parrot Mambo Minidrone, are rapidly evolving as platforms for research in real-time navigation, vision-based control, and autonomous robotics. This project focuses on programming the Parrot Mambo to autonomously follow a Red, Green, or Blue (R/G/B) line and perform a precision landing using only its onboard downward-facing camera and MATLAB-Simulink.

The system is built using Simulink’s model-based design combined with MATLAB’s color thresholding capabilities. A vision-based algorithm was developed to detect the colored path in real-time, calculate its position relative to the drone, and generate appropriate control signals. The drone continuously adjusts its trajectory using a custom Stateflow chart that interprets directional cues from the processed image. Upon detecting a specific visual condition indicating the end of the path, the drone transitions into a controlled descent phase and lands autonomously.

This project demonstrates the integration of computer vision and autonomous control in Simulink, offering a foundation for more complex UAV systems. The approach is modular and adaptable to multi-color tracking, multi-objective navigation, and reinforcement learning extensions.

---

## 1. Introduction
The ability for a UAV to navigate autonomously using visual feedback is fundamental to many applications in robotics, surveillance, and industrial automation. The Parrot Mambo Minidrone, with its lightweight form factor and integrated downward-facing camera, offers a suitable platform for developing and validating such capabilities.

In this project, the drone is tasked with following a predefined color-coded line (red, green, or blue) printed on the floor. Using Simulink, a model is developed to process the live video stream from the onboard camera, apply RGB-based segmentation, and convert the binary mask into meaningful directional data. Simultaneously, a custom-designed Stateflow chart interprets this data to make real-time steering decisions. A bounding-box symmetry check is used to identify the end of the path, after which the drone enters a soft landing phase.

The complete system is simulated in the 3D animation environment and tested in a controlled indoor setting. This report outlines the methodology, results, and future potential of this line-following and autonomous landing framework.

---

## 2. Method

### 2.1 Drone Setup and Initial Configuration
The experiment began by configuring the Parrot Mambo Minidrone using MATLAB’s Hardware Support Package. Connectivity was established over Bluetooth, and the drone’s firmware was verified for compatibility with the 2023b release. The default Simulink flight control model was loaded and tested to validate manual takeoff, hover, and landing operations. 

The onboard camera was calibrated to optimize contrast and exposure settings for line detection under fluorescent indoor lighting. A custom simulation environment was prepared for dry runs before real hardware deployment.

---

### 2.2 Image Processing Pipeline for Line Detection
The Simulink model features a dedicated image processing subsystem that takes camera input and generates control-relevant outputs. The steps are as follows:

- **Color Segmentation**: MATLAB’s Color Thresholder App was used to define RGB thresholds for detecting the Red, Green, and Blue paths. Each threshold was tuned manually under real-world lighting and exported as a MATLAB function.

- **Mask Generation and Filtering**: Each frame was converted into a binary image, where white pixels represent the target color. A median filter was applied to reduce visual noise.

- **Left-Right Split Analysis**: The frame was split vertically into two regions. A sum of white pixels in each region was calculated to infer direction.

- **Symmetry Detection for Landing**: The widths of detected blobs in the left and right halves were compared. If both sides were similar (within a threshold), a flag (`LAND_LOGIC`) was set high.

- **Simulink Integration**: The processing functions and logic blocks were compiled into a subsystem inside the Simulink model.

---

### 2.3 Stateflow-Based Navigation and Landing Control
A finite-state controller was implemented in Simulink using Stateflow to manage the flight phases of the drone:

- **Hover**: Initial stabilization state.
- **Cruise**: Line-following state using directional cues from the image processor.
- **Rotate**: Engaged when the line is lost, attempting re-orientation.
- **LAND**: Initiated upon detecting the endpoint condition (symmetry), triggering a controlled descent.

The Stateflow chart received the `LAND_LOGIC` signal as input and controlled vertical velocity (`zout`) during the landing state.

---

### 2.4 Simulink Integration and Deployment
All subsystems—image processing, control logic, and state machine—were integrated in a unified Simulink model. The final setup included:

- Vision data processing  
- Path tracking logic  
- Navigation state transitions  
- Landing controller  

Simulation was first conducted using the Simulink 3D Animation block set. Following successful trials, the code was auto-generated and deployed to the drone. The drone was tested on printed colored paths in a 2m x 2m test area.
![image](https://github.com/user-attachments/assets/de3a1ddc-7c42-4a5b-8c23-e6a79cee7fe3)

*Figure 1. Integrated Simulink model architecture for autonomous tracking and landing*

---

## 3. Conclusion
This project successfully demonstrated a fully autonomous drone system capable of following a colored path and landing without user intervention. The implementation utilized MATLAB for thresholding and Simulink for system modeling, testing, and deployment. The use of Stateflow allowed robust state transitions and decision-making under visual conditions.

Key takeaways include the importance of consistent lighting in image processing, the effectiveness of centroid and symmetry-based landing logic, and the utility of Simulink as a rapid prototyping tool for robotics. This work serves as a strong foundation for future research involving dynamic path following, multi-line detection, or neural network-based vision inference.

![final project 3 gif](https://github.com/user-attachments/assets/b153f38f-f477-4c13-b845-d48f4e4db1b1)


---

## References
- MATLAB Simulink Support Package for Parrot Minidrones  
- Color Thresholder App Documentation  
- UAV Navigation Using Stateflow in Simulink  
- Simulink 3D Animation Toolbox for UAV Simulation  

For queries, contact: **[anushka.satav@asu.edu](mailto:anushka.satav@asu.edu)**
