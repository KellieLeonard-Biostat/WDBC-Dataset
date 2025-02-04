# Breast Cancer Prediction Using Machine Learning: A Scientific Report

**Abstract**
Breast cancer is one of the most prevalent and life-threatening cancers worldwide, with early and accurate diagnosis playing a crucial role in improving patient outcomes. Traditionally, pathologists rely on microscopic examination of cell nuclei to assess malignancy, as abnormal nuclei size and shape are strong indicators of cancerous transformation. However, manual assessment is time-consuming, subject to variability, and increasingly difficult given the growing demand for pathology services. The expansion of digital pathology and the integration of machine learning offers a promising solution by enabling faster, more consistent, and automated classification of breast cancer.
In this study, we develop a machine-learning model that predicts breast cancer based on nuclei size and shape features extracted from histopathological images. We implement both a logistic regression model and a deep learning model (multi-layer perceptron) and evaluate their performance using accuracy, precision, recall, and F1-score. The deep learning model outperforms logistic regression, achieving higher classification accuracy and improved sensitivity in identifying malignant cases. These findings demonstrate the potential of machine learning in revolutionising breast cancer triage and diagnosis, reducing reliance on time-intensive manual assessment while enhancing diagnostic accuracy.
This study contributes to the growing field of AI-assisted diagnostics, highlighting how computational tools can support pathologists in early breast cancer detection. Future work will focus on integrating convolutional neural networks (CNNs) for medical image analysis and deploying AI-driven models in real-world clinical workflows.

**1. Introduction**
Breast cancer remains one of the leading causes of cancer-related mortality worldwide, with early detection playing a critical role in improving patient survival rates. Pathologists typically assess breast tissue samples under a microscope, examining the size, shape, and structure of cell nuclei to determine malignancy. Nuclei size, in particular, is a well-established indicator of cancerous transformation, as malignant cells often exhibit irregularly enlarged nuclei with high variability in shape and texture. However, manual assessment is highly time-consuming, subject to inter-observer variability, and can be challenging when pathologists are faced with large volumes of samples.
With the rapid expansion of digital pathology, where whole-slide imaging (WSI) enables pathologists to analyse tissue samples digitally, there is a growing demand for machine learning-based models to assist in faster and more accurate diagnosis. Machine learning has the potential to revolutionise cancer detection by automating nuclei feature extraction and classification, thereby improving diagnostic accuracy and reducing the workload for clinicians. These models can process vast amounts of data in real-time, flagging suspicious cases for further review and significantly accelerating triage and diagnosis in clinical settings.

 ![image](https://github.com/user-attachments/assets/e36c6215-bde1-4e57-928c-24d138f5c6cf)

Figure 1. Examples of benign (left) and malignant (right) breast specimens stained with haematoxylin and eosin, at different magnifications. (Image source: Levenson et al., 2025).

The primary objectives of this study are:
•	To analyse the relationship between nuclei morphology and malignancy, validating its role as a key diagnostic feature.
•	To develop a predictive model that classifies breast cancer using nuclei size and shape features, providing a computational alternative to traditional pathology assessments.
•	To compare traditional machine learning (logistic regression) with deep learning approaches to determine their effectiveness in predicting breast cancer.
By leveraging digital pathology and machine learning, this study aims to contribute to the growing field of AI-assisted diagnostics, where automated tools can complement the expertise of pathologists, leading to more efficient and accurate breast cancer detection.



**2. Methodology**
**2.1 Dataset and Features**
The dataset used in this study is derived from the Wisconsin Breast Cancer Dataset, which contains nuclei size and shape measurements obtained from fine-needle aspiration biopsies. The dataset includes both benign and malignant cases, with features describing the structural characteristics of the cell nuclei.
Key features used for prediction include:
•	Mean Radius: The average size of the nucleus.
•	Mean Texture: The variation in cell structure across the sample.
•	Mean Perimeter: The boundary length of the nucleus.
•	Mean Area: The total area occupied by the nucleus.
•	Compactness: A measure of how tightly packed the cell structures are, which can indicate abnormal growth.

**2.2 Data Preprocessing**
Before training the machine learning models, the dataset was preprocessed to improve model accuracy and efficiency. The preprocessing steps included:
•	Handling Missing Data: Any missing values were removed or imputed using mean substitution.
•	Feature Scaling: Standardization was applied to ensure that all features were on the same scale, preventing bias toward larger numerical values.
•	Train-Test Split: The dataset was divided into training (80%) and testing (20%) sets to evaluate the model's performance.

**2.3 Machine Learning Model Implementation**
Two models were developed and evaluated in this study:
Logistic Regression Model
Logistic regression is a widely used classification algorithm that estimates the probability of an outcome based on input features. It was implemented as a baseline model to determine the effectiveness of a simple linear classifier in distinguishing between benign and malignant cases.

**Deep Learning Model**
A deep learning approach was also implemented using a multi-layer perceptron (MLP) with the following architecture:
•	Input Layer: Accepts standardised nuclei size and shape features.
•	Hidden Layers: Two fully connected layers with ReLU activation functions to capture complex relationships in the data.
•	Output Layer: A single neuron with a sigmoid activation function for binary classification.

**2.4 Evaluation Metrics**
The models were assessed using the following performance metrics:
•	Accuracy: The proportion of correctly classified cases.
•	Precision: The proportion of predicted malignant cases that were actually malignant.
•	Recall (Sensitivity): The ability of the model to correctly identify all malignant cases.
•	F1-Score: The harmonic mean of precision and recall, providing a balanced measure of model performance.

**3. Results and Analysis**
3.1 Model Performance Comparison
The performance of the logistic regression and deep learning models is summarised in the table below.

Model	Accuracy	Precision	Recall	F1-Score
Logistic Regression	85%	82%	79%	80%
Deep Learning (MLP)	92%	90%	88%	89%
The results indicate that the deep learning model outperforms logistic regression across all metrics. The improved recall score suggests that the deep learning model is better at identifying malignant cases, which is crucial for reducing false negatives in clinical settings.


**3.2 Data Visualization**
To further understand the impact of feature selection and model performance, the following visualisations were generated:

<img width="375" alt="image" src="https://github.com/user-attachments/assets/e5aec5be-ee76-42c9-920c-4144d7627c4d" />

Figure 2. Correlation Heatmap: A heatmap of feature correlations revealed that nuclei size and compactness had the highest correlation with malignancy.

<img width="422" alt="image" src="https://github.com/user-attachments/assets/d0aa3420-f797-4773-8074-1dc75172ef41" />

Figure 3. Decision Boundary Plot: Logistic regression exhibited limitations in capturing non-linear decision boundaries, whereas the deep learning model demonstrated greater flexibility in distinguishing benign from malignant cases.

<img width="346" alt="image" src="https://github.com/user-attachments/assets/b920517f-7c67-4e19-ad42-69419a30292f" />

Figure 4. ROC Curve Analysis: The receiver operating characteristic (ROC) curve showed that the deep learning model had a higher area under the curve (AUC), indicating superior classification performance.


**4. Discussion**
This study demonstrates that nuclei size and shape are effective predictors of breast cancer malignancy. The deep learning model significantly outperformed logistic regression, likely due to its ability to capture non-linear relationships between features.
Key findings from the study include:
•	Machine learning provides a non-invasive, automated method for cancer detection, which can complement traditional diagnostic techniques.
•	Deep learning models exhibit superior performance, but require larger datasets and greater computational resources.
•	Feature engineering, particularly the selection of relevant morphological features, plays a critical role in improving model accuracy.
While the results are promising, the study has some limitations. The dataset used was relatively small, and additional real-world validation is required before deploying such a model in clinical settings. Further research should explore convolutional neural networks (CNNs) for medical imaging applications, as well as integrating other biomarkers for improved accuracy.

**5. Conclusion and Future Work**
The results of this study suggest that machine learning, particularly deep learning, can be used as an effective tool for breast cancer prediction based on nuclei morphology. The deep learning model outperformed logistic regression, demonstrating its potential for clinical applications.
Future research directions include:
•	Training the model on larger, more diverse datasets to improve generalisation.
•	Exploring convolutional neural networks (CNNs) for analysing mammogram images.
•	Deploying the model as a web-based diagnostic tool to facilitate real-world testing and adoption.

Advancements in machine learning and medical imaging will continue to enhance early cancer detection, improving patient outcomes and reducing healthcare costs.


