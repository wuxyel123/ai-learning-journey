# Docker for Reproducible ML Environments

## Summary

Docker is a tool that enables you to package your code, dependencies, and environment into isolated containers. In machine learning, this guarantees that models and pipelines behave the same way across systems—on your machine, on collaborators’ machines, or in production.

---

## 1. Why Docker for ML?

- Ensures **environment consistency** across teams and platforms.
    
- Encapsulates **dependencies** (Python version, libraries, drivers).
    
- Simplifies **deployment** (locally, in cloud, or with Kubernetes).
    
- Makes **experiments reproducible**: same data + same code + same environment.
    

---

## 2. Key Concepts

- **Docker Image**: A blueprint containing your app and environment.
    
- **Docker Container**: A running instance of an image.
    
- **Dockerfile**: A script defining how to build your image.
    
- **Volume**: A way to persist and share data between host and container.
    

---

## 3. Simple ML Docker Example

Create a basic directory structure:

```bash
project/
├── Dockerfile
├── requirements.txt
├── train.py
└── data/
```

### `requirements.txt`

```txt
numpy
pandas
scikit-learn
```

### `train.py`

```python
import numpy as np
from sklearn.linear_model import LinearRegression

X = np.random.rand(100, 1)
y = 2 * X + 1 + 0.1 * np.random.randn(100, 1)

model = LinearRegression()
model.fit(X, y)

print("Model trained. Coeff:", model.coef_, "Intercept:", model.intercept_)
```

### `Dockerfile`

```Dockerfile
FROM python:3.10

WORKDIR /app

COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["python", "train.py"]
```

---

## 4. Running Your Container

From the `project/` directory:

```bash
docker build -t ml-model .
docker run --rm ml-model
```

You should see model training output printed in the terminal.

---

## 5. Mounting Data and Output

You can mount a host directory into your container:

```bash
docker run --rm -v $(pwd)/data:/app/data ml-model
```

This makes data accessible at `/app/data` inside the container.

---

## 6. Optional Enhancements

- Add `ENTRYPOINT` and argument parsing to allow script customization.
    
- Use `docker-compose` to orchestrate multiple services (e.g., model + frontend).
    
- Use base images like `jupyter/scipy-notebook` for richer environments.
    
- Cache trained models to a mounted volume or upload to cloud storage.
    

---
