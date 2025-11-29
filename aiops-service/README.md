# AIOps Service — Beginner-Friendly Guide

This is a simplified and beginner-focused README.md for the AIOps service used in Express Web App v6. It includes setup instructions, usage, API testing, Prometheus metrics, and containerization.

---

## 1. Overview
The AIOps Service is a FastAPI-based microservice that:
* **Predicts infrastructure risk** (CPU, memory, latency)
* **Estimates cloud cost** (FinOps)
* **Exposes Prometheus metrics**
* Provides a local dashboard for demonstrations

---

## 2. Requirements
Install the following tools:
* Python 3.10+
* pip
* Docker (optional)
* curl (optional)

Check versions:
```bash
python3 --version
pip --version
docker --version
```

## 3. Setup and Install Dependencies

### 3.1 Create Virtual Environment (Best Practice)
**It is highly recommended to use a virtual environment** to isolate project dependencies.

```bash
cd aiops-service
# Create the environment named 'venv'
python3 -m venv venv
# Activate the environment
source venv/bin/activate
```
### 3.2. Install Dependencies
**Once the virtual environment is active, install the required packages:**
```bash
pip install -r requirements.txt
```

## 4. Run Locally
**Start FastAPI:**
```bash
uvicorn main:app --reload --host 0.0.0.0 --port 8080
```
Open dashboard: 
```txt
[http://127.0.0.1:8080](http://127.0.0.1:8080)
```

## 5. Test APIs
**Risk Prediction:**
```bash
curl -X POST [http://127.0.0.1:8080/predict](http://127.0.0.1:8080/predict) \
  -H "Content-Type: application/json" \
  -d '{"cpu": 80, "memory": 60, "latency_ms": 200}'
```

**FinOps Estimator:**
```bash
curl -X POST [http://127.0.0.1:8080/finops](http://127.0.0.1:8080/finops) \
  -H "Content-Type: application/json" \
  -d '{"cpu_millicores": 450, "memory_mb": 900}'
```

## 6. Cleanup
When you are finished, deactivate the virtual environment and clean up the created files.
```bash
# Deactivate the virtual environment
deactivate

# Remove the virtual environment and cache files
rm -rf venv/
rm -rf __pycache__/
```
