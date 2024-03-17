# Google Professional Data Analytics Certificate Capstone Project
## Salifort Employee Retention
The goal of this project is to create a prediction model that would be able to accurately predict which Salifort employees leave. 
The best model would be one that minimizes False Negatives, i.e. high recall score.

## Models Created
The following models were trained on the same training data set:
- Logistics Regression (LR)
- Decision Tree Classifier (DTC)
- Random Forest Classifier (RFC)
- XGBClassifier (XGBC)
- XGBClassifier with `objective='binary:logistic'` (XGBB) 

## Training Results
| **Model** |	**Accuracy** | **Precision** |	**Recall** |	**F1**	| **Time (s)** |
| ----- | -------- | --------- | ------- | ---- | -------- |
| **LR** |	76.508 | 39.886 |	81.423 |	53.522	| 3.8 |
| **DTC** |	98.193 | 98.214 |	90.795 |	94.334	| 4.6 |
| **RFC** |	98.165 | 98.653 |	90.209 |	94.209	| 307 |
| **XGBC** |	98.026 | 97.513 |	90.460 |	93.821	| 68 |
| **XGBB** |	98.096 | 97.793 |	90.628 |	94.030	| 90 |

The decision tree model (DTC) has the best Recall score during training, and has a very low training time.

## Validation Results
| **Model** |	**Accuracy** | **Precision** |	**Recall** |	**F1**	| **Time (s)** |
| ----- | -------- | --------- | ------- | ---- | -------- |
| **DTC** |	98.499 | 98.396 |	92.462 |	95.337	| 0.008815 |
| **RFC** |	98.582 | 98.663	 |	92.714 |	95.596	| 0.653749 |
| **XGBC** |	98.040 | 96.306	 |	91.709 |	93.951	| 0.853912 |
| **XGBB** |	98.499 | 98.656	 |	92.211 |	95.325	| 1.810806 |

The decision tree model (DTC) has the quickest time, but the random forest model has the best Recall score but it has the highest training time which would not be scalable.    

## Final Results
The Decision Tree model was selected since it can achieve a high Recall/F1 Score with one of the lowest training times, making it the best-performing scalable model.
The model's test scores were:
- Accuracy: 98.624%
- Precision: 99.191%
- Recall: 92.462%
- F1: 95.709%

The top 5 Features involved in making the decisions for the model are shown in the table below with their importance score (between 0 and 1).
|**Features**|**Importance Score**|
| ---------- | ------------------ |
| satisfaction_level	| 0.492273 |
| last_evaluation	| 0.170641 |
| number_project	| 0.128495 |
| company_tenure	| 0.128010 |
| average_montly_hours | 0.079744 |

### Next Steps  

The accuracy and precision scores are very good, but the Recall score could be improved. To do this we could try the following:
- Conduct feature engineering.
  *Note: This is the most realistic next step 
- Get more data where `left = 1` since most of the data is where `left = 0` to improve the class imbalance.
- Get more data on the employees such as demographic data and data regarding their role.
- Remove department-related columns since all the models did not use them to make predictions.
