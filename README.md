# 🛠 AI-Based Machine Fault Diagnosis Model

This project focuses on building a machine fault diagnosis model using the Hitachi MIMII dataset.
We generated frequency-domain data using Fast Fourier Transform (FFT) and applied the Isolation Forest algorithm to detect anomalies.
To enhance interpretability, we utilized SHAP (SHapley Additive exPlanations) for model explanation.
The trained model showed high accuracy and robustness, demonstrating its potential as a practical fault diagnosis system for industrial machinery.



# 📂 Dataset Overview

We used the MIMII dataset provided by Hitachi, Ltd., which includes a total of 1,279 fan sound samples.
This dataset contains both normal and abnormal sounds from various industrial machines (valves, pumps, fans, slide rails), with multiple models per machine type.
To simulate real-world environments, background noise recorded in different factories was also included.



## 🔊 Feature Extraction (FFT - Fast Fourier Transform)
We extracted key sound characteristics using FFT, converting raw time-series data into the frequency domain to better capture vibration patterns and abnormalities.


![image](https://github.com/kim-hyona/Development-of-AI-based-Machine-Fault-Diagnosis-Model-Using-Acoustic-Data/assets/148624727/d936adfa-aa2b-4ac2-89a6-7a0d5c0a76a3)



📊 Audio Signal Visualization
1. Top Plot: Single Audio Signal (Time Domain)

This plot shows the waveform of the raw audio signal in the time domain.
X-axis: Time (in samples, typically seconds or milliseconds)
Y-axis: Amplitude
You can observe how the signal persists over time with varying amplitudes — a direct visualization of the original audio waveform.

2. Middle Plot: FFT of Audio Signal (Frequency Domain)

This plot displays the frequency components of the signal using Fast Fourier Transform (FFT).
X-axis: Frequency
Y-axis: Magnitude
Several distinct peaks on the left side indicate strong frequency components. The right side shows decreasing frequency strength — clearly illustrating dominant frequencies in the signal.

3. Bottom Plot: Mel Spectrogram

This plot visualizes how frequency content changes over time using a Mel-scaled spectrogram.
X-axis: Time (in seconds)
Y-axis: Frequency (Mel scale)
Color: Signal intensity (in decibels)
Brighter colors represent higher energy, while darker regions represent lower intensity.
The spectrogram is especially helpful for detecting patterns and transitions in audio over time.




# 🌲 Isolation Forest Model Training (with PCA & Z-Score Normalization)


![image](https://github.com/kim-hyona/Development-of-AI-based-Machine-Fault-Diagnosis-Model-Using-Acoustic-Data/assets/148624727/4682422f-88c8-40bc-acb2-93dd213a8a4d)

✅ Model Evaluation Results
Evaluation Score: The model achieved an outstanding score of 0.9992, likely representing accuracy or F1-score.
Best model_0 score: 0.9992
Best model_2 score: 0.9992

** These results indicate that both model_0 and model_2 performed with near-perfect scores on the evaluation metric, demonstrating the high effectiveness and stability of the trained models. **


# 🧠 SHAP Visualization

SHAP (SHapley Additive Explanations) provides a visual interpretation of how each feature contributes to model predictions.
We used KernelExplainer to calculate SHAP values for the Isolation Forest model.

The force plot visualizes the contribution of each feature to a single prediction.
The beeswarm plot summarizes the overall impact of all features across multiple predictions.
These visualizations help us understand the model’s decision-making process and identify which features have the most significant influence.


![image](https://github.com/kim-hyona/Development-of-AI-based-Machine-Fault-Diagnosis-Model-Using-Acoustic-Data/assets/148624727/3f750335-cae0-4ffb-a11c-a456ac03aca0)



## 📌 Key Features Influencing Model Predictions
Using SHAP analysis, we identified several features that significantly influence the model's anomaly detection. Here's a summary of their interpretability:

Feature 54: Strongly associated with abnormal patterns. Higher values increase the likelihood of being classified as an anomaly. Most SHAP values for this feature are distributed toward the negative side.
Feature 15: Exhibits a wide range of SHAP values in both positive and negative directions. Its value contributes variably to the model’s decision — meaning high values could lead to either normal or abnormal predictions depending on context.
Feature 27: Plays a key role in predictions, with SHAP values spread across both directions. However, high values are more often associated with positive SHAP scores, indicating a tendency for the model to classify such samples as normal.
These features served as important indicators in predicting fan failures.

# 📊 Interpretation of the SHAP Summary Plot
The SHAP summary plot provides the following insights:

Identification of Key Features
Features with the widest range of SHAP values (like Feature 54, 15, and 27) have the greatest impact on predictions.
Direction of Influence
Features with red dots concentrated on the right suggest that high feature values tend to increase the prediction outcome.
Features with blue dots concentrated on the left indicate that low values tend to decrease the prediction outcome.
Feature Importance
Features with points widely spread from the center line (SHAP = 0) have a higher level of contribution and variability in model predictions.
For instance, Feature 54 can be considered one of the most influential features in the model.

# 🧾 Conclusion
From the SHAP summary plot, we can draw the following conclusions:

Feature 54 is the most impactful, and higher values tend to increase the prediction probability of an anomaly.
Feature 15 and Feature 27 also play significant roles in model decisions.
To improve model performance, these important features should be further analyzed and optimized.
Understanding how specific feature values influence predictions enhances model interpretability and reliability.
This analysis enables a deeper understanding of model behavior and provides actionable insights for improvement.









