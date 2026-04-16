
♻️ Smart Waste Segregation System (IPMV)
An automated waste classification system using Computer Vision (OpenCV) and Machine Learning (SVM) to categorize waste into 6 types: Paper, Cardboard, Plastic, Metal, Glass, and Trash.

📌 Project Overview
This project was developed as a study in Image Processing and Machine Vision (IPMV). It moves beyond standard deep learning by utilizing Hand-Crafted Feature Extraction. By manually selecting features like texture and edge density, we gain granular control over how the AI "sees" different waste materials.

🚀 Key Technical Features
Remote Vision Sensing: Utilizes an IP-linked mobile camera (via IP Webcam) to ensure high-resolution data acquisition, bypassing the limitations of standard laptop webcams.

7-Dimensional Feature Vector: * Color Analysis: BGR Mean values for basic color identification.

Saturation (HSV): Isolated saturation levels to distinguish dull materials (cardboard) from reflective ones (plastic/metal).

Texture Analysis (GLCM): Uses the Gray-Level Co-occurrence Matrix to calculate Contrast and Homogeneity, identifying the "feel" of a surface.

Structural Edge Density: Employs Canny Edge Detection to quantify the complexity of an object's outline.

SVM Classification: A Support Vector Machine brain optimized via GridSearchCV to find the ideal hyperplane for waste separation.

🛠️ System Architecture
The pipeline is structured into five distinct phases:

Data Acquisition: Connecting the remote sensor (phone) and defining the Region of Interest (ROI).

Feature Engineering: Converting raw image pixels into a mathematical CSV dataset.

Preprocessing: Normalizing data using StandardScaler to ensure all features (0-255 color vs 0-1 texture) carry equal weight.

Training & Optimization: Fitting the SVM and tuning hyperparameters (C, Gamma).

Live Inference: A real-time loop that captures, processes, and predicts waste types in under 0.1 seconds.

📦 Prerequisites
Bash
pip install opencv-python numpy scikit-learn scikit-image requests pandas
Mobile App: IP Webcam (Android) or iVCam (iOS).

📸 Usage Instructions
Setup Link: Start the server on your mobile app and update the url variable in the code with your IP (e.g., http://192.168.1.XX:8080/video).

Train Model: Execute Sections 1-4 to generate the waste_features.csv and train the SVM "brain."

Run Scanner: Execute Section 5.

Control: * Place object in the Green Box.

Press 'S' to Scan/Predict.

Press 'Q' to Quit.

📊 Performance & Evaluation
The system's accuracy is visualized through a Confusion Matrix.

By analyzing the grid, we identified that Paper and Cardboard were common points of confusion due to similar color profiles; this was mitigated by increasing the weight of the GLCM Homogeneity feature.

🎓 Academic Context
This project demonstrates core IPMV principles:

Spatial Domain Processing: ROI cropping and Edge Detection.

Statistical Texture Description: GLCM implementation.

Pattern Recognition: Supervised learning via Support Vector Machines.

Author: Abhinav N. Joshi

Field: Image Processing and Machine Vision (IPMV)

Year: 2026
