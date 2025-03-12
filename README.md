# Breast Cancer Diagnosis: Predictive Models Based on Nuclei Features

**Introduction**
Breast cancer remains one of the most prevalent and deadly cancers worldwide, underscoring the critical importance of early detection in improving patient outcomes. Advances in diagnostic tools, including the application of machine learning models, have significantly enhanced our ability to distinguish between benign and malignant breast tumours with accuracy and speed.

This report delves into the Wisconsin Diagnostic Breast Cancer (WDBC) dataset, which is derived from Fine Needle Aspiration (FNA) samples of breast tissue. It focuses on cell nuclei characteristics such as size, shape, texture, and other morphological properties. These features provide crucial insights into the distinction between benign and malignant tumours. By analysing these features, this report explores how machine learning models could effectively classify tumours, highlighting the potential for computational tools to aid in early breast cancer diagnosis.

 ![image](https://github.com/user-attachments/assets/a09abf34-0a95-47b2-8124-efd004564f2f)

Figure 1. Examples of benign (left) and malignant (right) breast specimens stained with haematoxylin and eosin, at different magnifications. (Image source: Levenson et al., 2025).

**Objective**
The main goal of this analysis is to demonstrate how cell nuclei features contribute to predicting the malignancy of breast tumours. We aim to show their relevance in distinguishing malignant tumours from benign ones by examining features such as nucleus size, shape, and texture.

**Data Overview**
The dataset used in this analysis is the WDBC dataset, which consists of 569 samples. Each sample corresponds to a tumour with 30 features related to the tumour's characteristics, including mean and standard deviation values for metrics like radius, texture, smoothness, symmetry, and concavity. The final column represents the target, benign (B) or malignant (M).

**Key Features Analysed:**
•	Radius Mean: The average distance from the centre of the nucleus to its perimeter.
•	Area Mean: The average area of the nucleus.
•	Smoothness Mean: Measure of the nucleus’s smoothness or roughness.
•	Symmetry Mean: Symmetry of the nucleus.
•	Concavity Mean: The degree of indentation of the nucleus.
•	Compactness Mean: Ratio of the nucleus's perimeter to its area.

**Methodology**
**Data Preprocessing**
1.	Data Cleaning: The dataset is first inspected for missing or null values. Missing data is either imputed or removed, ensuring the dataset is clean for analysis.
2.	Feature Selection: Features directly associated with cell nuclei characteristics are selected for analysis.
3.	Label Encoding: The target variable (target) is encoded numerically (Malignant = 1, Benign = 0) for machine learning models.
 
**Exploratory Data Analysis (EDA)**
EDA begins by visualising the distribution of benign vs. malignant diagnoses and examining the feature distributions to identify potential outliers and trends.

**Key EDA Insights**
Class Distribution: 
The dataset reveals an imbalanced class distribution, with a higher number of benign tumours (B) compared to malignant tumours (M). Specifically, out of the 569 samples, 357 (62.7%) are benign, while 212 (37.3%) are malignant. The higher prevalence of benign tumours in the dataset is reflective of real-world clinical scenarios, where most breast abnormalities are non-cancerous.

<img width="286" alt="image" src="https://github.com/user-attachments/assets/4e4b0120-0751-4c3f-a86f-4f8727d64df1" />

Figure 2. A bar chart comparing the number of benign and malignant tumours clearly illustrates the disparity in diagnostic distribution. This visual reinforces the need for careful handling of the imbalance to ensure the model accurately identifies malignant tumours without overemphasising the benign cases.

**Feature Distributions:** 
The feature radius_mean exhibits significant variability across the dataset, particularly when comparing benign and malignant tumours. The wide variability in radius_mean is critical because it reflects key biological differences between benign and malignant tumours:
•	Malignant Tumours: Larger, irregular nuclei are a hallmark of malignancy due to rapid and uncontrolled cellular growth.
•	Benign Tumours: Smaller, more uniform nuclei indicate controlled cell growth and division.

<img width="282" alt="image" src="https://github.com/user-attachments/assets/eaaa3016-57ee-43b9-8724-82302c709bf0" />

Figure 3. Box plot illustrates the difference between the radius_mean of malignant vs benign FNA samples. 

**Observations from Box Plots:**
•	Radius Mean (radius_mean):
o	Malignant tumours tend to have consistently higher radius_mean values, indicating larger nuclei compared to benign tumours.
o	The box plot reveals that the interquartile range (IQR) for malignant tumours is shifted significantly higher than that for benign tumours, suggesting this feature's potential as a key marker for malignancy.
o	There are some overlapping outliers, but the overall median values between the two classes remain distinct.


**Implications for Model Development:**
The distinct distributions observed in the box plots make radius_mean highly effective as discriminative features for machine learning models. Their ability to separate the two classes suggests that these features can serve as robust indicators in diagnostic settings.

**Feature Analysis**
**1. Nucleus Size (Radius and Area)**
Observation: 
•	Malignant tumours tend to have larger and more irregularly shaped nuclei compared to benign tumours. Larger nuclei are often associated with rapid cell division, a hallmark of malignancy. 
•	The interquartile range (IQR) for malignant tumours is also broader, indicating variability in tumour aggressiveness. In contrast, benign tumours display smaller and more consistent values.

**Biological Significance:**
1.	Larger Nuclei in Malignant Tumours:
o	Malignant tumours often show larger nuclei due to rapid, unchecked cell division and genetic instability. These larger sizes indicate an aggressive phenotype and help differentiate malignant cells from benign ones.
o	Larger nuclei may also reflect chromosomal abnormalities and high mitotic activity, further supporting their diagnostic value.
2.	Smaller, Regular Nuclei in Benign Tumours:
o	Benign tumours are characterised by smaller and more uniform nuclei, indicating normal or slightly altered cellular processes that lack the aggressive traits of malignancy.

<img width="290" alt="image" src="https://github.com/user-attachments/assets/adc48c97-7523-40bb-83ae-b1132437aa3d" />

Figure 4. The scatter plot shows the relationship between radius_mean and area_mean for benign vs. malignant tumours. Here, both tumour types form a strong positive correlation, with malignant tumours forming a distinctive cluster at the higher end of the spectrum. 

**Implications for Machine Learning:**
In machine learning models, radius_mean and area_mean emerge as highly discriminative features due to their strong association with malignancy. Their inclusion in feature selection boosts model performance by providing clear, biologically meaningful distinctions between the two tumour types.
By integrating these insights, these features improve diagnostic accuracy and enhance the interpretability of machine learning models, allowing healthcare professionals to rely on these predictions for more informed decision-making.

**2. Nucleus Shape (Smoothness)**
Observation: 
•	This feature measures the uniformity of the nucleus boundary. Lower values indicate smoother, more regular contours, whereas higher values signify irregular, jagged boundaries.
•	Benign tumours typically exhibit lower smoothness_mean values, reflecting their regular and well-defined nuclear boundaries.
•	Malignant tumours, on the other hand, show higher smoothness_mean values due to their irregular and uneven nuclear shapes, a hallmark of uncontrolled cell division and genetic instability.

**Biological Significance:**
•	Irregular Shapes in Malignant Tumours:
o	Malignant tumours often display jagged and irregular nuclear shapes due to rapid, uncoordinated cell division. This results in higher smoothness and concavity metrics.
•	Regular Shapes in Benign Tumours:
o	Benign tumours are characterised by smooth and relatively uniform nuclear shapes, indicating slower and more controlled cell growth. These features suggest that the cells retain their normal structure and function despite being part of a tumour.

<img width="288" alt="image" src="https://github.com/user-attachments/assets/4f3f2767-9525-4366-bb86-92b70a6949e9" />

Figure 5. A scatter plot comparing smoothness_mean shows distinct clustering, with benign tumours forming a tight group with lower values and malignant tumours spread over a wider range, indicating higher irregularity.

**Implications for Machine Learning:**
The smoothness_mean is a critical feature for identifying malignancy in machine learning models, contributions include:
•	Discriminative Power: This feature is a strong predictor, as distributions show minimal overlap between benign and malignant tumours.
•	Improved Interpretability: Models incorporating smoothness provide biologically meaningful insights, aiding in transparent and interpretable predictions.

**3. Nucleus Texture (Compactness)**
Compactness Mean (compactness_mean):
•	Compactness is calculated as (Perimeter2)/Area−1.0, quantifying a nuclear boundary's deviation from a perfect circle.
•	Benign tumours tend to have lower compactness_mean values, indicating nuclei that are closer to circular in shape, with smooth and uniform boundaries.
•	Malignant tumours exhibit higher compactness_mean values, reflecting irregular and distorted nuclei with jagged, uneven edges.

**Biological Significance:**
1.	Lower Compactness in Benign Tumours:
o	The nuclei in benign tumours are typically more uniform in shape, resembling circles or ellipses, with fewer irregularities in their boundaries. This regularity suggests slower and more controlled cell growth.
2.	Higher Compactness in Malignant Tumours:
o	Malignant cells exhibit disrupted nuclear shapes, often deviating significantly from a circle. This irregularity is due to rapid and uncontrolled cell division, genetic mutations, and structural abnormalities.

<img width="288" alt="image" src="https://github.com/user-attachments/assets/c3de1f2f-c051-4a01-b3ea-6e8b95f36438" />

Figure 6. The violin plot of compactness_mean shows a noticeable separation between benign and malignant tumours. Malignant tumours have higher medians and wider interquartile ranges, emphasising their irregularity and variability. Density plots for compactness_mean reveal distinct peaks for benign and malignant tumours, with malignant tumours skewed toward higher values.

**Implications for Machine Learning:**
•	Predictive Value:
o	Compactness is a highly discriminative feature for distinguishing benign from malignant tumours. Including it in machine learning models improves classification accuracy.
•	Combining Features:
o	Compactness provides a more holistic view of nuclear geometry when paired with other metrics such as radius and area, enabling better predictions and model interpretability.

**Statistical Analysis**
**Correlation Analysis**
A Pearson correlation matrix was computed for all numerical features to examine pairwise relationships:
Highly Correlated Features:
Several features displayed strong positive correlations with one another, particularly those related to cell size and perimeter. For example:
•	radius_mean, perimeter_mean, and area_mean exhibited correlation coefficients close to 0.9 or higher. This is expected as these features are all derived from the geometry of cell nuclei.
•	Features related to texture and compactness, such as compactness_mean, concavity_mean, and concave points_mean, also showed moderate to strong correlations (coefficients ranging from 0.6 to 0.8).
•	These correlations indicate potential multicollinearity, where some features provide overlapping information, which can negatively impact machine learning models if not addressed.


**Weakly Correlated Features:**
•	Features such as symmetry_mean and fractal_dimension_mean had relatively low correlations with other features, suggesting they provide unique information.
•	However, their low correlation with the target variable may limit their usefulness in distinguishing between benign and malignant tumours.

**Correlation with the Target Variable**
The correlation of individual features with the diagnosis label (benign vs. malignant) was analysed:
•	Strong Correlations:
o	Features related to size and irregularity, such as radius_mean (0.73), perimeter_mean (0.78), and area_mean (0.71), exhibited the highest positive correlations with malignancy. This indicates that larger and more irregularly shaped nuclei are strongly associated with malignant tumours.
o	Texture-related features like concave points_mean (0.77) and compactness_mean (0.65) also demonstrated strong positive correlations, highlighting the role of surface irregularity in malignancy classification.
•	Weak Correlations:
o	Features such as symmetry_mean and fractal_dimension_mean showed weak correlations (0.2 or less) with the target variable. While these features may not contribute significantly on their own, they could still play a role in a multivariate model.
•	Negative Correlations:
o	Some features, though rare, exhibited slight negative correlations. For instance, a lower value in smoothness_mean often corresponded to malignancy, reflecting the lack of uniformity in malignant cell nuclei.

**Multicollinearity**
•	Implications of High Correlations:
o	Strong correlations between certain features, such as radius_mean and area_mean, indicate potential redundancy. Including all these features in a predictive model may lead to multicollinearity, which can:
	Inflate the variance of regression coefficients, making them unstable.
	Misleading feature importance metrics in machine learning models.
o	Dimensionality reduction techniques, such as Principal Component Analysis (PCA), or regularisation methods, like LASSO or Ridge regression, can help address this issue.
•	Feature Selection:
o	While highly correlated features provide redundant information, they may still be valuable for interpretation. For example, retaining radius_mean (a proxy for size) and removing either area_mean or perimeter_mean could simplify the model without sacrificing much predictive power.

**Correlation Between Subgroups**
•	Within Benign Tumours:
o	Benign tumours showed tighter clusters of correlated features, such as smoothness_mean and symmetry_mean. This reflects the more uniform and regular characteristics of benign nuclei.
•	=Within Malignant Tumours:
o	Malignant tumours exhibited more dispersed correlations, especially among features related to texture and irregularity (e.g., concavity_mean and compactness_mean). This underscores the heterogeneity typical of malignant tumours.

**Heatmap Visualization**
A heatmap visualisation of the correlation matrix provided a clear view of relationships:
•	Strongly correlated feature pairs (e.g., radius_mean and area_mean) were easily identifiable as high-intensity clusters on the heatmap.
•	This visualisation highlighted key groupings and outliers, aiding in the selection of features for further analysis.

<img width="314" alt="image" src="https://github.com/user-attachments/assets/1e496252-7743-444e-b889-57aff53555f1" />

Figure 7. Correlation heatmap demonstrating variability in correlated feature pairs.


**Implications for Predictive Modelling**

•	Feature Engineering: Highly correlated features may need to be combined or reduced to avoid redundancy. For instance, aggregating size-related features into a single composite score could streamline the model.

•	Dimensionality Reduction: PCA or other methods can reduce the impact of multicollinearity by transforming correlated features into uncorrelated components while preserving variance.

•	Model Performance:
     
    o	Tree-based models like Random Forests and Gradient Boosting are less sensitive to multicollinearity and can handle correlated features effectively.

    o	For linear models, feature selection or regularisation techniques are critical to mitigate the impact of multicollinearity.




**Conclusion**
The analysis of cell nuclei features in the Wisconsin Diagnostic Breast Cancer dataset reveals that nucleus size, shape, smoothness, and concavity are significant indicators for differentiating malignant from benign tumours. By applying machine learning models, we achieve a classification system capable of accurately predicting malignancy.

Key findings suggest that features like radius_mean, area_mean, smoothness_mean, and concavity_mean play a crucial role in predicting tumour malignancy. These findings can be instrumental in developing tools for early breast cancer detection, aiding healthcare professionals in making informed, data-driven decisions.
 
**Future Work**
•	Data Augmentation: Exploring additional datasets with a more diverse set of patient backgrounds and larger datsets to improve model generalisation and accuracy. 

•	Deep Learning: Utilising deep learning models, such as convolutional neural networks (CNNs), to classify tumours based on image data, potentially improving performance in image-based diagnostics.
 




