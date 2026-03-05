# Clustering Analysis of Socioeconomic Data

## Overview
This project explores the use of unsupervised machine learning techniques to identify natural groupings within a socioeconomic dataset. The objective is to analyze patterns in demographic and economic variables and evaluate different clustering algorithms to determine which method best captures the underlying structure of the data.

The project was developed as part of the Machine Learning course in the Data Science and Artificial Intelligence degree at Universidad Politécnica de Madrid.

## Dataset
The dataset contains demographic and socioeconomic information about individuals. The main variables included in the analysis are:

- Age
- Education
- EducationNum
- MaritalStatus
- Relationship
- Gender
- CapitalGain
- HoursPerWeek

The dataset includes both categorical and numerical variables, which require different preprocessing techniques before applying clustering algorithms.

## Data Preprocessing
Before applying clustering techniques, several preprocessing steps were performed:

- Removal of duplicate records
- Exploratory analysis of variable distributions
- Identification of redundant variables
- Encoding categorical variables using OneHotEncoder
- Feature scaling using different scaling techniques

Several scaling strategies were tested in order to analyze their impact on clustering performance:

- StandardScaler
- MinMaxScaler
- MaxAbsScaler
- Normalizer
- RobustScaler

Finally, a custom scaling approach was implemented to better balance the influence of different variables:

- OneHot encoded variables were scaled using StandardScaler and adjusted by the number of categories
- Quantitative variables (Age, EducationNum, HoursPerWeek) were scaled using RobustScaler
- CapitalGain was scaled using MaxAbsScaler due to the presence of extreme values

This approach reduces the influence of outliers while maintaining a balanced representation of all features.

## Clustering Methods
Several clustering algorithms were implemented and compared to determine which method best represents the structure of the data.

### K-Means
K-Means clustering was applied using different numbers of clusters. The optimal number of clusters was determined using:

- Elbow Method (inertia)
- Silhouette score

The analysis concluded that the optimal configuration was **K-Means with 4 clusters**.

### Hierarchical Clustering
Hierarchical clustering was tested using different linkage methods:

- Single
- Complete
- Average
- Ward

Among these methods, **Ward linkage** produced the most compact and balanced clusters.

### DBSCAN
The DBSCAN algorithm was also evaluated using different values of epsilon and minimum samples. However, the resulting clusters were not well separated and the silhouette score was negative, indicating poor clustering performance for this dataset.

### Gaussian Mixture Models
Gaussian Mixture Models were also tested using different covariance types and numbers of components. The best model according to the BIC score used **4 components with full covariance**, but the resulting clusters were not clearly separated.

## Best Model
After comparing all clustering approaches, the model that produced the most interpretable and consistent results was:

**K-Means with 4 clusters**

This model achieved a silhouette score of approximately **0.21**, indicating moderate but meaningful separation between groups.

## Cluster Interpretation
The clusters obtained from the K-Means model can be interpreted as follows:

- **Cluster 2**  
  Younger individuals who work fewer hours per week. This group may represent students or individuals at the early stages of their careers.

- **Cluster 3**  
  Individuals with lower levels of education and higher average age, which may reflect generational differences in access to education.

- **Cluster 1**  
  Individuals with higher levels of education who work the largest number of hours per week. This group may correspond to highly qualified professionals or academic profiles.

- **Cluster 0**  
  Individuals with medium levels of education and moderate working hours, representing a typical working population.

## Technologies Used
The project was implemented in Python using the following libraries:

- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- Seaborn
- Jupyter Notebook

## Repository Structure

data/  
dataset.csv  

notebooks/  
codigo_proyecto_final_AA.ipynb  

reports/  
memoria_proyecto_final_AA.pdf  
presentacion_proyecto_aprendizaje.pdf  

README.md

## Authors
Héctor Fernández Cano  
Diego José García Callejas  

Data Science and Artificial Intelligence  
Universidad Politécnica de Madrid
