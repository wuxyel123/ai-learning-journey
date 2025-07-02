## k-NN and Support Vector Machines (SVM)

### 1. k-Nearest Neighbors (k-NN)

**Concept**:

- A non-parametric, instance-based learning algorithm.
    
- Classification is based on the majority label among the k closest data points.
    

**Steps**:

1. Store the training data.
    
2. For a new input, compute distances (e.g., Euclidean) to all training points.
    
3. Pick the k closest points.
    
4. Return the most common label among them.
    

**Hyperparameters**:

- `k`: number of neighbors.
    
- Distance metric: Euclidean, Manhattan, etc.
    
- Weights: uniform or distance-weighted.
    

**Code (scikit-learn)**:

```python
from sklearn.datasets import load_iris
from sklearn.neighbors import KNeighborsClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

X, y = load_iris(return_X_y=True)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.3, random_state=42)

knn = KNeighborsClassifier(n_neighbors=3)
knn.fit(X_train, y_train)
y_pred = knn.predict(X_test)

print("Accuracy:", accuracy_score(y_test, y_pred))
```

---

### 2. Support Vector Machines (SVM)

**Concept**:

- A powerful algorithm for binary (and multiclass) classification.
    
- Finds the optimal hyperplane that maximizes the margin between classes.
    
- Can use kernel trick to separate non-linearly separable data.
    

**Types**:

- Linear SVM
    
- Nonlinear SVM with RBF or polynomial kernels
    

**Hyperparameters**:

- `C`: regularization (smaller = larger margin, more tolerance to misclassification)
    
- `kernel`: linear, rbf, poly
    
- `gamma`: influences decision boundary curvature
    

**Code (scikit-learn)**:

```python
from sklearn.svm import SVC

svm = SVC(kernel='rbf', C=1.0, gamma='scale')
svm.fit(X_train, y_train)
y_pred_svm = svm.predict(X_test)

print("SVM Accuracy:", accuracy_score(y_test, y_pred_svm))
```

---

### 3. When to Use What?

|Feature|k-NN|SVM|
|---|---|---|
|Model complexity|Simple|Complex|
|Memory usage|High (stores all data)|Low|
|Speed (inference)|Slow|Fast|
|Handles non-linear|No|Yes (with kernels)|
|Sensitive to outliers|Yes|Less|

---
