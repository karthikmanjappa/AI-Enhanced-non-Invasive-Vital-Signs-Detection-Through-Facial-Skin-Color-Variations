# AI-Enhanced-non-Invasive-Vital-Signs-Detection-Through-Facial-Skin-Color-Variations
## Introduction
#### The demand for non-invasive, real-time health monitoring solutions has led to the development of innovative techniques that utilize everyday hardware and simple signal processing methods. One such approach is the detection of vital signs—such as heart rate and respiratory rate—by analyzing facial skin color variations using a standard webcam and a Raspberry Pi. This method relies on changes in skin tone caused by blood flow beneath the skin surface, which can be captured through video and analyzed without the need for complex machine learning or computer vision models.In this system, a webcam captures live video of a subject’s face, and the Raspberry Pi processes the frames to extract a Region of Interest (ROI)—typically the forehead or cheeks—where skin tone changes are most visible. The video signal from the ROI is then analyzed using traditional image and signal processing techniques. Techniques such as Fast Fourier Transform (FFT) are applied to the time-series data of pixel intensity changes to extract periodic signals corresponding to the heartbeat and breathing rate. Additionally, Histogram of Oriented Gradients (HOG) is used to enhance facial feature detection and stabilize the ROI for consistent analysis.This approach provides a low-cost, portable, and contactless solution for vital sign monitoring. It avoids the complexities of machine learning models while maintaining reliable performance through carefully designed signal processing pipelines. It is especially useful for remote or low-resource healthcare environments, home monitoring systems, and educational or research projects focused on biomedical signal processing.
## KeyWords
#### Non-Invasive Vital Signs Detection,Facial Skin Color Variations,Raspberry Pi,Webcam-Based Monitoring,Region of Interest (ROI),Heart Rate Detection,Respiratory Rate Detection,Fast Fourier Transform (FFT),Histogram of Oriented Gradients (HOG),Real-Time Health Monitoring,Signal Processing,Contactless Physiological Monitoring,Remote Patient Monito ,Biomedical Signal Analysis,Low-Cost Health Technology.
## Problem Statement
#### In the healthcare domain, continuous monitoring of vital signs such as Heart Rate (HR) and Oxygen Saturation (SpO₂) is crucial, especially for elderly patients and those in remote locations. Traditional methods often involve contact-based sensors, which may cause discomfort, require maintenance, and are not always suitable for long-term use. To address these challenges, a non-contact, user-friendly system is proposed. This system follows Human-Computer Interaction (HCI) guidelines and leverages a webcam to detect the user's face, extract the region of interest (ROI), and process physiological signals from facial skin color variations. By using signal processing techniques, the system estimates HR and SpO₂ in real-time without physical contact.
## Objective
#### To implement a non-invasive method for measuring Heart Rate (HR) and Oxygen Saturation Level (SpO₂) using facial skin color variations captured via a webcam.
#### To extract and analyze signals using image and signal processing techniques such as ROI detection, Fast Fourier Transform (FFT), and Histogram of Oriented Gradients (HOG).
#### To design a user-friendly graphical user interface (GUI) that allows users to easily interact with the system, view their real-time vitals, and operate the system without technical expertise.
## Literature Survey
#### ![image](https://github.com/user-attachments/assets/524a1d21-cf35-4394-a117-b3b25a40d3c1)
#### ![image](https://github.com/user-attachments/assets/291d8687-6a32-4cca-8c8d-02ba9944930e)
## System Design
#### A user-friendly desktop application is developed using PyQt5, a Python GUI framework. This interface allows users to start/stop video capture, view real-time vitals, and interact with the system effortlessly. The GUI also displays graphs for visualizing the processed signals, enhancing user understanding and engagement.
## Data Acquisition
#### Visual input is obtained using a standard webcam or pre-recorded video files. This step provides a continuous stream of facial data, which is the foundation for subsequent analysis. The webcam must be positioned such that the user's face is clearly visible, ideally in front of the camera with stable lighting.
## Face Detection
#### The system uses the SSD (Single Shot Multibox Detector) algorithm for robust and real-time face detection. SSD is a deep learning-based method that balances speed and accuracy, making it suitable for deployment on resource-constrained devices like Raspberry Pi. It accurately identifies the face even under varying lighting conditions or head positions.
## Region of Interest (ROI) Extraction
#### Once the face is detected, the system isolates a specific Region of Interest (ROI)—typically the forehead. This area is chosen because it shows the most consistent color variation due to blood flow and has minimal obstruction from facial features (e.g., eyes, mouth).
## Pulse Signal Calculation
#### From the ROI, the system calculates the average color intensity (usually from the green channel in the RGB video frames) over time. These variations form a raw signal known as the Photoplethysmogram (PPG), which reflects changes in blood volume with each heartbeat.
#### The PPG signal is then analyzed further using Fast Fourier Transform (FFT) to identify dominant frequency components, enabling the extraction of heart rate. Further processing techniques can estimate SpO₂ by comparing intensity variations across different color channels (like red and blue).
## Explanation of The Algorithms and Techniques
## 1. Viola-Jones Algorithm (for Face Detection)
#### Purpose: To detect human faces in images or video in real time.
## How it works:
#### Haar-like features: It uses simple features based on differences in pixel intensities (e.g., edges, lines).
#### Integral Image: Speeds up the calculation of these features for all areas in the image.
#### AdaBoost: Selects the most important features and builds a strong classifier from weak ones.
#### Cascade Classifier: Applies the face detection in multiple stages, quickly eliminating non-face regions and zooming in on possible face areas.
#### Use in your system: It can be used to quickly detect and locate the face in webcam frames before further processing.
## 2. Region of Interest (ROI)
#### Purpose: To focus on a specific part of the image—usually the forehead in vital sign detection.
#### How it works:
#### After detecting the face, a specific rectangular portion (like the forehead) is selected.
#### This region is where skin color changes due to blood flow are most visible and least obstructed (by facial hair or movement).
#### ROI reduces the amount of data processed and improves accuracy and speed.
#### Use in your system: ROI provides the data source for extracting the heart rate and SpO₂ signal by tracking color changes over time.
## 3. Fast Fourier Transform (FFT)
#### Purpose: To convert a time-domain signal (like skin color variation over time) into the frequency domain.
#### How it works:
#### Takes the PPG signal from the ROI (color intensity over time).
#### Applies FFT to find the dominant frequencies in the signal.
#### The peak frequency corresponds to the heart rate (e.g., a peak at 1.2 Hz = 72 beats per minute).
#### Use in your system: FFT is used to extract heart rate by identifying the strongest periodic signal (pulse) in the facial color variation.
## 4. Bandpass Filter / Butterworth Filter
#### Purpose: To filter out unwanted noise and keep only the frequency range relevant to vital signs.
#### Bandpass Filter:
#### Allows only a specific range of frequencies to pass.
#### For example, for heart rate, it may allow frequencies between 0.7 Hz to 4 Hz (which corresponds to 42–240 bpm) and remove everything else.
## Butterworth Filter:
#### A type of bandpass filter known for its smooth frequency response (no ripples).
#### Preferred in biomedical applications because it avoids distortion in the signal.
#### Use in your system: It smooths the raw PPG signal by removing noise (like head movements or lighting fluctuations) and keeps only the useful frequencies for accurate heart rate and SpO₂ estimation.
## Output
#### ![Screenshot 12](https://github.com/user-attachments/assets/944e7072-e7d0-4a6b-93af-fd31b0c0b9f2)
## Conclusion
#### This project successfully demonstrates a non-contact method for monitoring vital signs such as Heart Rate (HR) and Oxygen Saturation(SpO₂)using facial skin color variations captured through a webcam. By implementing signal processing techniques like Fast Fourier Transform (FFT) and Butterworth Bandpass Filtering,the system accurately extracts physiological signals from the facial Region of Interest (ROI)—specifically the forehead.
#### The use of a Raspberry Pi, combined with OpenCV and PyQt5, ensures the system remains cost-effective, portable, and user-friendly. The graphical user interface (GUI) designed using PyQt5 allows for seamless interaction,real-time monitoring, and visual feedback for users, following HCI (Human-Computer Interaction) principles.By avoiding complex machine learning models and relying solely on efficient signal processing methods, the system provides a lightweight, reliable, and accessible solution for vital sign monitoring. It holds great potential for use in remote health monitoring, home care, and resource-constrained medical environments, supporting the broader goal of making healthcare more affordable and non-intrusive.







