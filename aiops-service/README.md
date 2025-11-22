# AIOps Service — Beginner-Friendly Guide

This is a simplified and beginner-focused README.md for the AIOps service used in Express Web App v6.  
It includes setup instructions, usage, API testing, Prometheus metrics, and containerization.

## 1. Overview
The AIOps Service is a FastAPI-based microservice that:
- Predicts infrastructure risk (CPU, memory, latency)
- Estimates cloud cost (FinOps)
- Exposes Prometheus metrics
- Provides a local dashboard for demonstrations

---

## 2. Requirements
Install the following tools:

- Python 3.10+
- pip
- Docker (optional)
- curl (optional)

Check versions:
```
python3 --version
pip --version
docker --version
```

---

## 3. Install Dependencies
```
cd aiops-service
pip install -r requirements.txt
```

---

## 4. Run Locally
Start FastAPI:
```
uvicorn main:app --reload --host 0.0.0.0 --port 8080
```

Open dashboard:
```
http://127.0.0.1:8080
```

---

## 5. Test APIs

### Risk Prediction
```
curl -X POST http://127.0.0.1:8080/predict   -H "Content-Type: application/json"   -d '{"cpu": 80, "memory": 60, "latency_ms": 200}'
```

### FinOps Estimator
```
curl -X POST http://127.0.0.1:8080/finops   -H "Content-Type: application/json"   -d '{"cpu_millicores": 450, "memory_mb": 900}'
```

---

## 6. Prometheus Metrics
View all metrics:
```
curl http://127.0.0.1:8080/metrics
```

---

## 7. Docker Support
Build image:
```
docker build -t aiops-api:latest .
```

Run:
```
docker run -p 8080:8080 aiops-api:latest
```

---

## 8. Next Steps
This AIOps service will later be deployed to:
- Amazon EKS  
- With Helm, ArgoCD, Prometheus, Grafana  

Part of Express Web App v6 modernization.

---

## 9. Author
**Emmanuel Naweji**  
Cloud • DevOps • SRE • FinOps • AI Engineer  
PhD Candidate — AI/ML in Healthcare  
IBM • T2S • Kids Teck Inc. • EMLink

