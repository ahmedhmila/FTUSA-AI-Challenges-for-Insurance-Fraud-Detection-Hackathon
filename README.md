# FTUSA-AI-Challenges-for-Insurance-Fraud-Detection-Hackathon

## Table of Contents
1. [Introduction](#introduction)
2. [Approach Explanation](#approach-explanation)
3. [Data Loading and Preprocessing](#data-loading-and-preprocessing)
4. [Principal Component Analysis (PCA)](#principal-component-analysis-pca)
5. [Model Training](#model-training)
6. [Model Evaluation](#model-evaluation)
7. [ROC Curve](#roc-curve)
8. [Application to Raw Data](#application-to-raw-data)
9. [Alternative Approach: Analysis of Schemes](#alternative-approach-analysis-of-schemes)
10. [Presentation Slides](#presentation-slides)
11. [Conclusion](#conclusion)
12. [Future Work](#future-work)



## Introduction

This repository contains Jupyter Notebooks developed during the FTUSA Hackathon at the 17th Carthage Insurance Meeting. The projects focus on leveraging data analysis, data cleaning, and machine learning to tackle key challenges in the insurance industry.

In the Jupyter notebook, located under `Notebooks/ftusa.ipynb`, I present a comprehensive approach to building a fraud detection model using Principal Component Analysis (PCA) and RandomForestClassifier. The notebook is organized into several sections, each focusing on a different aspect of the model development process.



## Approach Explanation



The dataset I worked with was corrupted and it was challenging to discern relationships in the data. Traditional supervised learning approaches were less effective as the fraud cases weren't labeled and there were no apparent indicators of fraud.



To overcome these challenges, I adopted a unique approach. I assumed that every case is fraudulent unless proven otherwise. This approach is akin to anomaly detection, where the aim is to identify the 'normal' or 'non-fraudulent' cases and label anything that deviates from this norm as potential fraud.



This approach is particularly suitable for this task because it does not rely on having clear indicators of fraud, but rather on being able to model the 'normal' behavior accurately. Any transaction that does not fit this model is then considered a potential fraud case. This approach is robust to the challenges posed by the corrupted data and the lack of clear fraud indicators.



I used PCA for dimensionality reduction and RandomForestClassifier as the model, which aligns well with this approach. PCA helps to highlight the most important features in the data, which can help in modeling the 'normal' behavior, while RandomForestClassifier is a powerful classifier that can model complex relationships in the data. The combination of these techniques has proven to be effective, as evidenced by the high accuracy, F1 score, and AUC value achieved by the model.



## Data Loading and Preprocessing



I started by loading the dataset, which contains various features related to transactions. The aim is to predict whether a transaction is fraudulent or not. I preprocessed the data to handle missing values, convert categorical variables into numerical ones, and scale the features to ensure that they all have the same range of values.



## Principal Component Analysis (PCA)



After preprocessing, I applied PCA to the data to reduce its dimensionality. PCA is a technique that transforms the features into a new set of uncorrelated features, which are a linear combination of the original features. These new features, or principal components, are ordered by the amount of variance they can explain in the original data.



## Model Training



I split the transformed data into a training set and a test set. I trained the RandomForestClassifier model on the training set. RandomForestClassifier is an ensemble learning method that operates by constructing multiple decision trees during training and outputting the class that is the mode of the classes of the individual trees.



## Model Evaluation



I evaluated the trained model on the test set. The performance of the model is assessed using two metrics: accuracy and F1 score. 



The model achieved an accuracy of 0.996, indicating that it correctly predicted the fraud status of about 99.6% of the transactions in the test set. The model also achieved an F1 score of 0.969, indicating a good balance between precision and recall.

![Heatmap of Processed Data](/report_images/PreHeatMap.png)



## ROC Curve



I also generated a Receiver Operating Characteristic (ROC) curve and calculated the Area Under the Curve (AUC). The ROC curve is a plot that illustrates the diagnostic ability of a binary classifier as its discrimination threshold is varied. The AUC provides an aggregate measure of performance across all possible classification thresholds.



The ROC curve is plotted using matplotlib, with the AUC displayed in the legend. In this run of the notebook, the model achieved an AUC of 0.9999, indicating an excellent performance across all classification thresholds.

![ROC Curve for Processed Data](/report_images/RoCPre.png)



## Application to Raw Data



The robustness of the model was further tested by applying it to raw data in a separate notebook located under `Notebooks/ftusa - Raw Data.ipynb`. The model performed exceptionally well, achieving an accuracy of 0.9975606624727179, an F1 score of 0.9799366420274551, and an AUC of 0.9986964399775787.



 These metrics indicate that the model was able to accurately identify fraudulent transactions with a high degree of precision and recall, even when applied to raw, unprocessed data. This is a testament to the robustness of the model and its ability to generalize well to unseen data.

![Heatmap of Raw Data](/report_images/RawDataHeatMap.png)



## Alternative Approach: Analysis of Schemes

In an alternative approach, we delved into the schemes of the data. This approach involved extracting samples from the data for analysis. The idea was to identify patterns or relationships in the data that could be used to build a predictive model.

The schemes were visualized and can be seen in the image below:





![Schemes](/report_images/Schemes.jpg)





However, this approach faced a significant hurdle. The data was heavily corrupted, which made it challenging to discern any meaningful patterns or relationships. The corruption was so severe that it was not feasible to build a reliable model based on this data.

This experience underscores the importance of data quality in model building. Even the most sophisticated models cannot produce reliable results if the underlying data is corrupted or of poor quality. In such cases, it may be necessary to clean the data, impute missing values, or even collect new data.

Despite the challenges faced in this approach, it was a valuable learning experience. It highlighted the importance of data exploration and quality control in the model building process. It also served as a reminder of the challenges that can arise when working with real-world data, and the need for robust data preprocessing and cleaning techniques.

![Examples Schemes](/report_images/scExp.png)
![More Examples Schemes](/report_images/SCE.png)


This alternative approach and its challenges are documented in detail in the `Notebooks/Schemes.ipynb` notebook.

## Presentation Slides

The presentation slides for this project can be found at the following link:

[Canva Presentation Slides](<https://www.canva.com/design/DAGFp8s75Pw/RBmjOIlgBmzsQk7czq3tew/edit?utm_content=DAGFp8s75Pw&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton>)

You can obtain this link from the `CanvaLinx.txt` file.

## Conclusion

Throughout this project, we explored various approaches to building a fraud detection model. The primary approach, which involved using PCA and RandomForestClassifier, yielded impressive results, with high accuracy, F1 score, and AUC values. The model's robustness was further confirmed by its high performance when applied to raw data.

The heatmaps provided a visual representation of the correlation between different features in the dataset, aiding in feature selection and engineering. The ROC curve for the processed data further underscored the model's performance, indicating its ability to distinguish between fraudulent and non-fraudulent transactions with high accuracy.

An alternative approach involved analyzing the schemes of the data. However, due to severe data corruption, it was not feasible to build a reliable model based on this data. This experience highlighted the importance of data quality in model building and the need for robust data preprocessing and cleaning techniques.

In conclusion, this project demonstrated the effectiveness of PCA and RandomForestClassifier for fraud detection, the importance of data quality, and the challenges that can arise when working with real-world data. It serves as a comprehensive guide to building a fraud detection model and can be easily adapted to different datasets or used as a basis for further experimentation with different models or feature engineering techniques

## Future Work
In future, we could explore other machine learning models and techniques to improve the performance of our fraud detection system. Additionally, we could also look into more sophisticated data cleaning and preprocessing methods to handle corrupted data.
