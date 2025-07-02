## Decision Trees & Random Forests

### 1. Decision Trees

- **Definition**: A flowchart-like structure where each internal node represents a test on a feature, each branch represents an outcome, and each leaf node represents a predicted class or value.
    
- **Splitting Criteria**:
    
    - **Classification**: Gini impurity or entropy (information gain)
        
    - **Regression**: Mean squared error (MSE)
        
- **Advantages**:
    
    - Easy to interpret and visualize
        
    - Handles both numerical and categorical data
        
    - No feature scaling required
        
- **Drawbacks**:
    
    - Prone to overfitting
        
    - Small changes in data can lead to a completely different tree
        

```python
from sklearn.datasets import load_iris
from sklearn.tree import DecisionTreeClassifier, plot_tree
import matplotlib.pyplot as plt

X, y = load_iris(return_X_y=True)
model = DecisionTreeClassifier(max_depth=3)
model.fit(X, y)

plt.figure(figsize=(12, 6))
plot_tree(model, filled=True, feature_names=load_iris().feature_names, class_names=load_iris().target_names)
plt.show()
```

---

### 2. Random Forests

- **Definition**: An ensemble of decision trees trained on different data subsets and/or feature subsets. Final prediction is made by averaging (regression) or majority voting (classification).
    
- **Benefits**:
    
    - Reduces overfitting by averaging multiple trees
        
    - Handles high dimensionality and feature correlations well
        
    - Offers feature importance estimates
        

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

rf_model = RandomForestClassifier(n_estimators=100, random_state=42)
rf_model.fit(X_train, y_train)
y_pred = rf_model.predict(X_test)

print(classification_report(y_test, y_pred))
```

---

### 3. Feature Importance

```python
import pandas as pd
import seaborn as sns

importances = rf_model.feature_importances_
features = load_iris().feature_names

sns.barplot(x=importances, y=features)
plt.title("Feature Importances")
plt.show()
```

---

