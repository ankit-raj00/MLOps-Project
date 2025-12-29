# 🚗 MLOps Project – Vehicle Insurance Data Pipeline

This repository implements a **production-aligned, end-to-end MLOps pipeline** for vehicle insurance data. The project focuses on building a **modular, scalable, and automated machine learning system**, covering the complete lifecycle from data ingestion to model deployment.

The emphasis is on **system design, reproducibility, automation, and cloud-native practices**, rather than isolated model training.

---

## ✨ Key Features & Implementations

* **End-to-End MLOps Pipeline**
  Data ingestion → validation → transformation → training → evaluation → deployment

* **Cloud-Native Data Storage**
  MongoDB Atlas used as the primary raw data source

* **Schema-Driven Data Validation**
  Strict validation using YAML-based schemas to ensure data quality

* **Artifact-Based Pipeline Design**
  Each pipeline stage produces versioned artifacts for traceability

* **Model Registry on AWS S3**
  Trained models are stored, versioned, and retrieved from S3

* **Automated CI/CD Pipeline**
  GitHub Actions with a self-hosted EC2 runner

* **Dockerized Deployment**
  Application packaged into Docker images for reproducible builds

* **AWS Infrastructure Integration**
  EC2 for compute, ECR for image storage, S3 for model artifacts

* **FastAPI-Based Prediction Service**
  Asynchronous API for serving predictions

* **Centralized Logging & Exception Handling**
  Production-style logging and error management

* **Modern Python Packaging**
  `pyproject.toml` + `setup.py` + `requirements.txt`

---

## 📁 Project Structure

```text
├── src/
│   ├── components/          # Core pipeline components
│   ├── configuration/       # MongoDB & AWS configuration
│   ├── constants/           # Global constants
│   ├── data_access/         # Data access layer
│   ├── entity/              # Config & artifact definitions
│   ├── aws_storage/         # S3 model registry logic
│   ├── logger/              # Logging utilities
│   ├── exception/           # Custom exceptions
│
├── notebooks/               # EDA & MongoDB notebooks
├── static/                  # Frontend assets
├── templates/               # HTML templates
├── app.py                   # FastAPI application
├── setup.py                 # Package configuration
├── pyproject.toml           # Modern packaging metadata
├── requirements.txt         # Dependencies
├── Dockerfile               # Container definition
├── .github/workflows/       # CI/CD pipelines
└── README.md
```

---

## ⚙️ Environment Setup

```bash
conda create -n vehicle python=3.10 -y
conda activate vehicle
pip install -r requirements.txt
```

Verify installed packages:

```bash
pip list
```

---

## 📊 Data Storage – MongoDB Atlas

* Cloud-hosted MongoDB (M0 cluster)
* Secure user authentication
* Network access configuration
* Data uploaded and verified via Jupyter notebooks

MongoDB acts as the **single source of truth** for raw data.

---

## 📥 Data Ingestion

* MongoDB connection handled via configuration layer
* Data fetched and transformed into Pandas DataFrames
* Config-driven ingestion logic
* Reproducible ingestion artifacts generated

Environment variable setup:

```bash
export MONGODB_URL="mongodb+srv://<username>:<password>..."
```

---

## 🔍 Data Validation

* Dataset schema defined using `config.schema.yaml`
* Column presence and datatype checks
* Early detection of malformed or missing data

---

## 🔄 Data Transformation

* Feature engineering pipelines
* Preprocessing logic
* Train-test split artifacts persisted

---

## 🧠 Model Training

* Configurable training pipeline
* Metric tracking
* Serialized model artifacts

---

## ☁️ Model Evaluation & Registry (AWS S3)

* Model evaluation against previously deployed versions
* Threshold-based model acceptance
* Approved models pushed to S3 model registry

---

## 🚀 Prediction Pipeline

* Separate inference workflow
* Model dynamically loaded from S3
* Asynchronous FastAPI endpoints

---

## 🐳 Dockerization

* Application containerized using Docker
* Consistent runtime across environments
* Optimized build using `.dockerignore`

---

## 🔄 CI/CD Pipeline

* GitHub Actions for automated builds
* Self-hosted runner on AWS EC2
* Docker images pushed to AWS ECR
* Automated deployment to EC2

---

## 🖥️ Deployment

* EC2 security group configured for port `5080`
* Application accessible at:

```text
http://<EC2_PUBLIC_IP>:5080
```

---

## 🔁 End-to-End Workflow Summary

1. Data Ingestion
2. Data Validation
3. Data Transformation
4. Model Training
5. Model Evaluation
6. Model Registry (S3)
7. Deployment (Docker + EC2)
8. CI/CD Automation

---

## 📌 Notes

* Environment variables used for credential management
* `.gitignore` excludes artifacts and secrets
* Python packaging follows modern stand
