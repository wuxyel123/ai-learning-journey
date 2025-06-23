##  Linear & Logistic Regression

---

### 1. Linear Regression

Linear regression models the relationship between a dependent variable yy and one or more independent variables XX by fitting a line (or hyperplane).

**Equation**:

y=Xβ+ϵy = X\beta + \epsilon

#### scikit-learn Example

```python
from sklearn.linear_model import LinearRegression
from sklearn.datasets import make_regression
from sklearn.metrics import mean_squared_error

X, y = make_regression(n_samples=100, n_features=1, noise=10, random_state=42)
model = LinearRegression()
model.fit(X, y)
y_pred = model.predict(X)
print("MSE:", mean_squared_error(y, y_pred))
```

---

### 2. Logistic Regression

Logistic regression is used for binary classification. It models the probability that y=1y = 1 using the sigmoid function:

σ(z)=11+e−z\sigma(z) = \frac{1}{1 + e^{-z}}

#### scikit-learn Example

```python
from sklearn.linear_model import LogisticRegression
from sklearn.datasets import make_classification
from sklearn.metrics import accuracy_score, confusion_matrix

X, y = make_classification(n_samples=100, n_features=2, n_classes=2, random_state=42)
clf = LogisticRegression()
clf.fit(X, y)
y_pred = clf.predict(X)
print("Accuracy:", accuracy_score(y, y_pred))
print("Confusion Matrix:\n", confusion_matrix(y, y_pred))
```

---

### 3. Model Evaluation

- **Linear Regression**: MSE, R^2
    
- **Logistic Regression**: Accuracy, confusion matrix, precision, recall, ROC AUC
    

Use `.score(X, y)` to quickly evaluate a model:

```python
print("Linear score:", model.score(X, y))
print("Logistic score:", clf.score(X, y))
```

---

### 4. Pipelines and Preprocessing

Create a streamlined ML pipeline:

```python
from sklearn.pipeline import Pipeline
from sklearn.preprocessing import StandardScaler

pipe = Pipeline([
    ("scaler", StandardScaler()),
    ("model", LogisticRegression())
])
pipe.fit(X, y)
```

---
