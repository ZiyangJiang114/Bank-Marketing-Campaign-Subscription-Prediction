# Bank-Marketing-Campaign-Subscription-Prediction
## Abstract
This project analyzes a bank marketing dataset from the UCI Machine Learning Repository, based on direct telephone campaigns conducted by a Portuguese banking institution. The goal of this practice is to develop classification models that can predict whether a client will subscribe to a term deposit product.

The analysis follows the CRISP-DM framework, including business understanding, data exploration, feature engineering, model development, and evaluation. Several classification models are compared, including Logistic Regression, K-Nearest Neighbors (KNN), Decision Tree, and Support Vector Machine (SVM).

The results show that while most models achieve high accuracy, their ability to correctly identify actual subscribers remains limited. This highlights the importance of selecting appropriate evaluation metrics and further improving model performance through hyperparameter tuning.

---
## Data Source
- **Dataset:** UCI Machine Learning Repository – Bank Marketing Dataset  
- **Reference Paper:** *Using Data Mining for Bank Direct Marketing: An Application of the CRISP-DM Methodology*  

The dataset contains information from **17 marketing campaigns** conducted between **2008 and 2010**, with over **79,000 client contacts**. The target variable represents whether a client subscribed to a term deposit.

---
## Methodology (CRISP-DM)

### Business Understanding

The objective of this taks is to improve the successful rate of direct marketing campaign by identifying clients who are more likely to subscribe to a term deposit and reduce unnecessary contact attempts.

---
### Data Understanding

The dataset contains both categorical and numerical features as input variable, grouped into 4 main categories:

- client demographics  
- contact information  
- campaign history  
- economic indicators  

There is only one output, which represents wether the client subscribed a term deposit.

---
### Data Preparation & Feature Engineering

After a careful data screening and analysis, the features of:

- 'duration' was removed because it is unusable for real-world prediction.
- 'housing','loan', and 'default' were removed due to their minimal variation in subscription rates, indicating low predicative value.
- 'pdays' conatins a special value(999) indicating that the client was contacted the first time. To properly represent this information, a new binary numerical featrue 'is_firstTime_Call' was created. The origional values of 999 were replaced with 0.
- 'y', target varaible, was converted from categorical values to a binary numerical format.

---

### Modeling

A baseline model (`DummyClassifier`) was introduced to establish a minimum benchmark.

Four classification models were trained and compared with their default set-up:

- Logistic Regression  
- KNN  
- Decision Tree  
- SVM  

The results showing:
- Logistic Regression provides the highest precison, and relatively quick training time. However, it has a low recall score.
- KNN is one of the fast model, it has a better balance between the precision and recall, and provides the highest F1 score, suggesting KNN with default settings provided the best overall balance.
- Decision Tree required less computation cost than logistic regression model, but it provides notable gap between train and test accuracy indicating overfitting.
- SVM was much slower than all other models. It provides a good traning and test accuracy showing good genralization performance.

---

### Model Optimization

To improve model performance, hyperparameter tuning was applied to all classifiers with **F1-score as the primary evaluation metric**, aiming to better balance precision and recall.

- **Logistic Regression:** Tuned regularization parameter `C` (best ≈ 23.05), resulting in slight improvement in recall with stable generalization.
- **KNN:** Used GridSearchCV to tune `n_neighbors` (best = 11), improving overall balance between precision and recall.
- **Decision Tree:** Tuned `max_depth` (best = 10) to reduce overfitting and improve generalization, leading to the strongest overall performance.
- **SVM:** Optimized step-by-step (kernel → `C` → `gamma`), achieving competitive performance but with significantly higher computational cost.

Overall, hyperparameter tuning improved model generalization and F1-score across all models, with the **Decision Tree providing the best balance between performance and efficiency**.

---








