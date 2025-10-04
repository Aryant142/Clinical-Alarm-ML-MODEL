AI for Clinical Alarm Fatigue Reduction
An unsupervised machine learning model to reduce clinical alarm fatigue in Intensive Care Units (ICUs) by identifying anomalous vital sign patterns.

1. Project Description
This project develops an AI-powered platform to address the critical issue of clinical alarm fatigue among nursing staff in ICUs. By applying an unsupervised anomaly detection model (Isolation Forest) to time-series vital sign data from the MIMIC-IV dataset, the system learns to identify a patient's normal physiological patterns. It then flags only statistically significant deviations, or "anomalies," rather than simple threshold breaches. The ultimate goal is to filter out the noise of non-actionable alerts, allowing nurses to focus their attention on clinically significant events, thereby reducing burnout and improving patient safety.

2. The Problem: Alert Fatigue
In critical care settings, patient monitoring equipment can generate hundreds of alarms per patient per day. Studies show that 85-99% of these alarms are false or non-actionable, leading to "alert fatigue"—a desensitization that can cause delayed responses to genuine, life-threatening events. This project tackles this problem by creating a smarter, context-aware alert system.

3. The Dataset
This project uses data from the MIMIC-IV (Medical Information Mart for Intensive Care IV) database, a large, publicly available, de-identified dataset of ICU patient records. The primary data used includes:

   vitalsign.csv: Time-series data of patient vital signs (heart rate, SpO2, blood pressure, etc.).

   diagnosis.csv: Patient diagnostic information (ICD codes) for contextual analysis.

4. Methodology
The project follows a standard machine learning workflow:

Data Cleaning & Preprocessing: The raw vitalsign data is cleaned by converting timestamps, handling non-numeric values, and imputing missing data using forward-fill.

Feature Engineering: Statistical features (mean, std, min, max) are calculated over a rolling 60-minute window for each vital sign to create a "snapshot" of the patient's state over time.

Unsupervised Anomaly Detection: An Isolation Forest model is trained on the engineered features. This model learns the characteristics of "normal" data for each patient.

Scoring: The trained model assigns an anomaly score to each time point, where a higher score indicates a pattern that is more unusual for that patient.

5. Results
The model successfully identifies clinically significant events as high-scoring anomalies. The visualization below shows a case study for a single patient, where a sharp spike in the anomaly score corresponds directly to a critical drop in the patient's oxygen saturation (SpO2), demonstrating the model's effectiveness.
