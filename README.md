
# Data-Driven Approach for Speaker Age Estimation from Spoken Sentences

Estimating speaker age from voice is a challenging task in speech processing. The code consider a data-driven approach for age estimation using a regression pipeline on a dataset that incorporates pre-provided features along with available audio recordings. Preprocessing steps, including noise reduction, feature extraction and selection, and outlier detection with DBSCAN, were applied to enhance performance. Several regression models—such as Ridge, Lasso, SVR, and Random Forest—were evaluated. Random Forest regression yielded the best results, which, however, highlighted that further efforts in feature engineering, selection, and model refinement could be necessary.  

<br><br>

### Problem description

The data set consisted of 3,624 samples (not available in the repository): 2,933 samples for the development set and 691 samples for the evaluation set. Each sample corresponded to an individual speaking a sentence. In the development set, the individual’s age was provided as the target label. In contrast, in the evaluation set, the age was unknown and had to be determined. Some features were already provided and audio recordings were also available to potentially extract new features. <br>
The graph representing the age (the target variable) distribution for the male and female genders revealed a significant imbalance in the occurrence of older and very young individuals compared to the central age range, which made the problem more challenging. 
<br>
![immagine](https://github.com/user-attachments/assets/292b581d-5ede-4874-972e-351be44c5350)



<br>

### Preprocessing
To accurately predict a speaker’s age, it was essential to first address data quality issues such as noise, outliers, missing values, duplicates, and incorrect data. Thus, preprocessing played an essential role. Moreover, the ethnicity attribute showed high variability and imbalance, with some groups appearing only in the development or only in the evaluation datasets. To prevent sparsity from one-hot encoding, ethnicities were grouped into broader macro-categories: Western, Sub-Saharan, Asian, and Others.


<br>

### FEUTURE EXTRACTION and SELECTION, 
In order to extract new features from the sample audios, the signals were trimmed and denoised.

<br>

![immagine](https://github.com/user-attachments/assets/dcb6ef82-384c-4d32-920a-89c449c83977)
<br>


To improve the predictive power of the regression pipeline, several new features were engineered from the audio samples. Feature scaling was applied to normalize duration-dependent attributes. A correlation analysis identified highly correlated features and in later stage models were tested with and without these features to assess their impact on performance. Principal Component Analysis (PCA) was used to reduce the feature space of specific groups of attributes while maintaining 90% of the variance.

<br>

### OUTLIERS DETECTION
To enhance model performance, the DBSCAN clustering algorithm was applied to detect potential noise and outliers in the dataset. Standardization using the mean and standard deviation from the development set was crucial for this process. Tuning DBSCAN proved challenging, as the results were highly variable and dependent on feature selection and the hyperparameters used. The figure below showcases the removal of 583 samples across different age intervals.

<br>

![immagine](https://github.com/user-attachments/assets/d025522f-af2a-4117-a496-b5a8458c84d0)


<br>

### Model selection

At this stage various regression models were compared and tuned, including Ridge, Lasso, Support Vector Machine, and Random Forest regression.To evaluate model performance, the Root Mean Square Error (RMSE) formula was used. Cross-validation was the most effective method for hyperparameter tuning on the development set.



### Results

To assess the performance of the data science pipeline, the models were fitted using the entire development dataset and then evaluated on the evaluation dataset.
<br>
![immagine](https://github.com/user-attachments/assets/58cbce4f-702c-49fa-80c1-81809c53034d)
<br>
Ultimately, the Random Forest regression model was selected as the best-performing model among those evaluated, resulting in a final RMSE of 9.746.

