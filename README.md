# Edge-AI-Smart-Ear-Using-DSP-for-Industrial-Safety
Smart Ear is an Edge-AI based Smart Listening system for industrial predictive maintenance and safety, designed to detect abnormal machine sounds in real time.

# Overview
SmartEar is a real-time predictive maintenance system that uses Edge AI and acoustic signal analysis to detect machine faults. The system captures live audio and processes it through a DSP pipeline (Filtering → FFT → MFCC) to extract meaningful features for classification.

A lightweight on-device model running on ESP32 classifies machine states as GOOD or BROKEN with high accuracy, enabling instant fault detection without cloud dependency. The system demonstrates clear feature separation and reliable fault transition detection in real-time.

SmartEar offers a low-cost and scalable solution for industrial monitoring, making it suitable for applications such as motors, pumps, and rotating machinery.

# Tools and Techniques
ESP-32 Microcontroller
Sound Sensor Module(INMP441)
Edge Impulse Studio
Programming Environment(Arduino IDE)

# Working
SmartEar operates as a real-time Edge-AI pipeline that converts machine sound into fault predictions directly on the device.

An I2S microphone interfaced with the ESP32 continuously captures machine audio, which is segmented into short overlapping frames to preserve temporal variations. The captured data is processed in Edge Impulse Studio, where a DSP pipeline (Filtering → FFT → MFCC) extracts meaningful acoustic features from raw audio.

These features are used to train a lightweight classification model on labeled data (GOOD and BROKEN). The trained model is then deployed on the ESP32, enabling real-time, on-device inference without cloud dependency.

During operation, incoming audio is continuously analyzed and classified. To ensure reliability in noisy environments, predictions are observed over time, allowing the system to detect consistent fault patterns instead of reacting to transient disturbances.

By combining Edge Impulse (DSP + model training) with ESP32-based Edge AI deployment, SmartEar delivers a low-cost, scalable, and low-latency predictive maintenance solution.

# Result 
The SmartEar system successfully demonstrated real-time acoustic fault detection using Edge AI on ESP32. The MFCC feature extraction process produced clear separability between GOOD and BROKEN machine conditions, as observed in the feature explorer visualization.

The trained model achieved high-confidence classification, where prediction probabilities remained close to 1.00 for GOOD during normal operation and transitioned sharply to ~0.98–1.00 for BROKEN during faulty conditions. The prediction timeline confirmed a distinct and consistent shift from normal to abnormal behavior.

Experimental testing showed that the system reliably detects faults in real time while maintaining stability in noisy environments. The complete pipeline runs efficiently on-device, validating its suitability for low-latency, offline industrial monitoring and predictive maintenance applications.

# Future Scope
The current system can be extended to support multi-class fault classification, enabling identification of specific fault types such as bearing wear, misalignment, and imbalance. Adaptive thresholding and online learning techniques can be incorporated to improve long-term reliability under varying operating conditions.

While this implementation utilizes Edge Impulse Studio for DSP processing and model development, future work can focus on building a custom AI model and DSP pipeline from scratch, allowing greater control over optimization, feature engineering, and model performance.

Further improvements may include integration of advanced lightweight deep learning models and combining additional sensor data (e.g., vibration or temperature) for multi-modal fault detection.

Scalability can also be enhanced through edge–cloud integration, enabling centralized monitoring and analytics across multiple machines.
