# OSDA
NeuralFCA Gladkikh Roman

# Big homework description
For big homework I choose three datasets: 
* Iris Dataset [link](https://archive.ics.uci.edu/dataset/53/iris)
* 70k+ Job Applicants Data (Human Resource) [link](https://www.kaggle.com/datasets/ayushtankha/70k-job-applicants-data-human-resource)
* Wine [link](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html)

## First dataset: Iris Dataset
### Description
IRIS Dataset consists of 150 rows and 5 columns where the columns are namely sepal length in cm, sepal width in cm, petal length in cm, petal width in cm, and Species. There are 3 species namely Iris Setosa, Iris Versicolor, and Iris Virginica.
### Preprocessing
Here I faced with problem with the number of target values. NeuralFCA can only solve the binary classification problem, so I choose to predict one of the classes against all, for all 3 classes. Approximately the same results are obtained, in order to avoid repetitions, I left the code for only one class. I processed the signs using the binarization step = 1.5. After binarization, we get 12 features from 4. Then I selected the top 20 concepts and built NN using them. After learning, we have graph:
[[IRIS](https://github.com/RomanGladkikh/OSDA/blob/main/NeuralFCA/images/iris_fitted.png)]
### Results

Model | Accuracy | F1-score | 
--- | --- | --- |
KNeighborsClassifier | 0.956 | 0.955 | 
DecisionTree | 1.0 | 1.0 | 
RandomForest | 1.0 | 1.0 | 
LogisticRegression | 1.0 | 1.0 | 
**NeuralFCA** | 1.0 | 1.0 |

FCA exhibited perfect results on the "Iris" dataset with Accuracy and F1 Score all at 1.0. This indicates that FCA perfectly classified samples in this balanced dataset. In comparison, other machine learning modules also showed high performance on this dataset.
![alt text](https://github.com/RomanGladkikh/OSDA/blob/main/NeuralFCA/images/iris_fitted.png)

## Second dataset:  70k+ Job Applicants Data (Human Resource)
### Description
The dataset titled "Employability Classification of Over 70,000 Job Applicants" (but we will use only 1000 observations, for speed performance) contains a comprehensive collection of information regarding job applicants and their respective employability scores. From the survey results, we have a dataset with the following columns:
* Age: age of the applicant, >35 years old or <35 years old (categorical)
* EdLevel: education level of the applicant (Undergraduate, Master, PhD…) (categorical)
* Gender: gender of the applicant, (Man, Woman, or NonBinary) (categorical)
* MainBranch: whether the applicant is a profesional developer (categorical)
* YearsCode: how long the applicant has been coding (integer)
* YearsCodePro: how long the applicant has been coding in a professional context, (integer)
* PreviousSalary: the applicant's previous job salary (float)
* ComputerSkills: number of computer skills known by the applicant (integer)
* Employed: target variable, whether the applicant has been hired (categorical).
### Preprocessing
First of all, I deleted the columns ['HaveWorkedWith', 'Country'], in order to correctly apply OHE to categorical features (Otherwise, we will have too much features after using OHE (>1000)). For numeric features, I set a threshold based on the mean value in the column, so all values in a particular column were divided into 2 set (greater than the threshold and less than the threshold, respectively). After binarization, we get 21 features from 14. Then I selected the top 50 concepts and built NN using them. After learning, we have graph:
[[JOB](https://github.com/RomanGladkikh/OSDA/blob/main/NeuralFCA/images/job_fitted.png)]
### Results

Model | Accuracy | F1-score | 
--- | --- | --- |
KNeighborsClassifier | 0.783 | 0.782 | 
DecisionTree | 0.783 | 0.781 | 
RandomForest | 0.810 | 0.805 | 
LogisticRegression | 0.820 | 0.818 | 
**NeuralFCA** | **0.823** | **0.824** |

FCA exhibited wery good results on the "70k+ Job Applicants Data (Human Resource)" dataset with Accuracy and F1 Score 0.823 and 0.824. In comparison, other machine learning models showed worse results than NeuralFCA
![alt text](https://github.com/RomanGladkikh/OSDA/blob/main/NeuralFCA/images/job_fitted.png)

## Third dataset: Wine
### Description
Dataset contains information about the chemical composition of three types of wine. Target feature here is origin of wine, which contains of three classes.
### Preprocessing
Here I faced with the same problem as in Iris Dataset. NeuralFCA can only solve the binary classification problem, so I choose another approach: I delete the smallest class. I binarised data by using median threshold (similar to mean threshold in 70k+ Job Applicants Data (Human Resource)). Then I selected the top 50 concepts and built NN using them. After learning, we have graph:
[[Wine](https://github.com/RomanGladkikh/OSDA/blob/main/NeuralFCA/images/wine_fitted.png)]
### Results

Model | Accuracy | F1-score | 
--- | --- | --- |
KNeighborsClassifier | 0.871 | 0.870 | 
DecisionTree | 0.875 | 0.870 | 
RandomForest | 0.925 | 0.896 | 
LogisticRegression | 0.925 | 0.924 | 
**NeuralFCA** | **0.974** | **0.976** |

FCA exhibited wery good results on the "Wine" dataset with Accuracy and F1 Score 0.974 and 0.976. In comparison, other machine learning models showed much worse results than NeuralFCA
![alt text](https://github.com/RomanGladkikh/OSDA/blob/main/NeuralFCA/images/wine_fitted.png)
