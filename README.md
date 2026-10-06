# AI-Driven SOC Home Lab with Wazuh, Machine Learning & SOAR

## 📌 Overview

This project presents an AI-driven Security Operations Center (SOC) home lab designed to demonstrate security monitoring, threat detection, machine learning-based threat classification, and automated incident response.

The architecture integrates **Wazuh** for centralized security monitoring and log collection, **Machine Learning** models for threat analysis and classification, and **SOAR** for automating response workflows.

The project was developed in a controlled virtualized lab environment to simulate real-world cybersecurity attacks and evaluate the effectiveness of machine learning models in SOC operations.

---

## 🎯 Objectives

* Build a modular SOC environment using open-source cybersecurity technologies.
* Collect and monitor endpoint security events using Wazuh.
* Generate security alerts through controlled attack simulations.
* Preprocess Wazuh security alerts for machine learning.
* Classify threats using Random Forest, XGBoost, and SVM.
* Analyze sequential log patterns using LSTM.
* Evaluate ML models using accuracy, precision, recall, F1-score, and confusion matrices.
* Provide an ML API for integrating trained models with the SOC pipeline.
* Automate security response using SOAR workflows.

---

## 🏗️ Architecture

```text
                         ┌─────────────────────┐
                         │   Kali Linux VM     │
                         │  Attack Simulation  │
                         └──────────┬──────────┘
                                    │
                                    │ Security Events
                                    ▼
                         ┌─────────────────────┐
                         │   Windows VM        │
                         │  Wazuh Agent        │
                         └──────────┬──────────┘
                                    │
                                    │ Logs / Alerts
                                    ▼
                         ┌─────────────────────┐
                         │   Wazuh Manager     │
                         │   SIEM Monitoring   │
                         └──────────┬──────────┘
                                    │
                                    │ Wazuh Alerts
                                    ▼
                         ┌─────────────────────┐
                         │ Data Preprocessing  │
                         │ & Feature Engineering│
                         └──────────┬──────────┘
                                    │
                                    ▼
              ┌─────────────────────────────────────┐
              │       Machine Learning Layer        │
              │                                     │
              │ Random Forest │ XGBoost │ SVM │ LSTM│
              └──────────────────┬──────────────────┘
                                 │
                                 │ Threat Classification
                                 ▼
                         ┌─────────────────────┐
                         │     ML API          │
                         │  Flask REST API     │
                         └──────────┬──────────┘
                                    │
                                    ▼
                         ┌─────────────────────┐
                         │       SOAR          │
                         │ Automated Response  │
                         └──────────┬──────────┘
                                    │
                    ┌───────────────┼───────────────┐
                    ▼               ▼               ▼
               Alert Admin      Block IP       Isolate Host
```

---

## 🔧 Technologies Used

### Security Monitoring

* Wazuh
* Wazuh Agent
* SIEM
* Wireshark

### Machine Learning

* Python
* Pandas
* NumPy
* Scikit-learn
* XGBoost
* TensorFlow / Keras

### Machine Learning Models

* Random Forest
* Support Vector Machine (SVM)
* XGBoost
* Long Short-Term Memory (LSTM)
* Ensemble Model

### API / Integration

* Flask
* Flask-CORS
* REST API

### Virtualization

* VirtualBox
* Windows VM
* Kali Linux VM
* Wazuh Server VM

---

## 🧪 Lab Environment

The experimental environment consists of a host Windows system with multiple virtual machines.

### Host Machine

* CPU: Intel Core i5
* RAM: 16 GB
* Storage: 512 GB SSD
* OS: Windows 11

### Virtual Machines

| Machine      | Purpose                                  |
| ------------ | ---------------------------------------- |
| Wazuh Server | Security monitoring and alert management |
| Windows VM   | Monitored endpoint                       |
| Kali Linux   | Controlled attack simulation             |

The project uses a controlled and isolated virtualized environment for security testing.

---

## 🔍 Attack Simulation

Security events were generated through controlled attack simulations from the Kali Linux environment against the Windows endpoint.

The project demonstrated scenarios including:

* Port scanning
* Stealth scanning
* Brute-force attacks
* DoS/DDoS-style traffic
* Malware/payload simulation

These activities generated security events that were detected by Wazuh and subsequently used in the machine learning pipeline.

---

## 📊 Data Pipeline

The overall processing pipeline is:

```text
Security Activity
       ↓
Wazuh Agent
       ↓
Wazuh Manager
       ↓
Security Alerts
       ↓
Data Extraction
       ↓
Data Preprocessing
       ↓
Feature Engineering
       ↓
Machine Learning
       ↓
Threat Classification
       ↓
SOAR Automation
       ↓
Incident Response
```

---

## 🧠 Machine Learning Pipeline

The dataset contains Wazuh security events collected from the controlled SOC lab.

Important features include:

* Event ID
* Alert Level
* Timestamp
* Source IP
* Destination IP
* Rule Description
* Attack Type
* Log Source
* Event Count
* Time Difference

Categorical features were encoded and missing values were handled during preprocessing.

Temporal and sequence-based features were also considered for LSTM-based intrusion detection.

---

## 📈 Model Performance

The models were evaluated using accuracy, precision, recall, and F1-score.

| Model         | Use Case              | Accuracy | Precision | Recall | F1-Score |
| ------------- | --------------------- | -------: | --------: | -----: | -------: |
| Random Forest | Threat Classification |    88.5% |      0.89 |   0.88 |    0.885 |
| XGBoost       | Threat Classification |    87.5% |      0.88 |   0.87 |    0.875 |
| SVM           | Threat Classification |    88.5% |      0.88 |   0.89 |    0.885 |
| LSTM          | Intrusion Detection   |   88.49% |      0.89 |   0.88 |   0.8849 |
| Ensemble      | Threat Classification |    88.5% |      0.89 |   0.88 |    0.885 |

---

## 📊 Evaluation Metrics

The following metrics were used to evaluate the models:

* Accuracy
* Precision
* Recall
* F1-Score
* Confusion Matrix
* ROC/AUC

These metrics were used to compare the performance of different machine learning models for cybersecurity threat detection.

---

## ⚙️ Project Workflow

### 1. Log Collection

Wazuh agents collect security events from monitored endpoints.

### 2. Alert Generation

Controlled attacks generate security alerts in Wazuh.

### 3. Data Preparation

Relevant fields are extracted from Wazuh alerts and transformed into a structured dataset.

### 4. Feature Engineering

Relevant security and temporal features are selected for ML processing.

### 5. Model Training

Multiple machine learning models are trained and evaluated.

### 6. Threat Detection

The trained model analyzes incoming security events and classifies potential threats.

### 7. API Integration

The trained ML model can be exposed through a Flask REST API for integration with the SOC pipeline.

### 8. Automated Response

Threat intelligence generated by the ML layer can be passed to a SOAR platform for automated response workflows.

---

## 📁 Repository Structure

```text
├── data/          # Dataset and data documentation
├── ml/            # Machine learning source code
├── wazuh/         # Wazuh configuration and integration
├── soar/          # SOAR workflows
├── notebooks/     # ML experimentation notebooks
├── screenshots/   # Project screenshots and results
├── docs/          # Project documentation
├── requirements.txt
├── .gitignore
└── README.md
```

---

## 🚀 Installation

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/AI-Driven-SOC-Wazuh-ML-SOAR.git
cd AI-Driven-SOC-Wazuh-ML-SOAR
```

Create a Python virtual environment:

```bash
python -m venv venv
```

Activate the environment.

### Windows

```bash
venv\Scripts\activate
```

### Linux

```bash
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

---

## ▶️ Machine Learning Usage

Train the model:

```bash
python ml/train.py
```

Run prediction:

```bash
python ml/predict.py
```

Run the API:

```bash
python ml/api.py
```

> Update these commands according to the actual filenames and implementation in the repository.

---

## 🔐 Security & Privacy

This repository is intended for educational and research purposes.

No credentials, API keys, passwords, private security logs, or sensitive organizational information should be committed to the repository.

Sensitive configuration values should be stored using environment variables.

Example:

```text
WAZUH_API_USERNAME=
WAZUH_API_PASSWORD=
WAZUH_MANAGER_IP=
```

---

## ⚠️ Disclaimer

All attack simulations in this project were performed in a controlled and isolated virtual lab environment for educational and research purposes.

Do not use the attack techniques or payloads against systems without explicit authorization.

---

## 🔮 Future Scope

Potential future improvements include:

* Adaptive ML model retraining
* Integration with external threat intelligence feeds
* NLP-based alert analysis
* Automated incident summarization
* Advanced SOAR playbooks
* Host isolation automation
* Honeypot integration
* Federated learning
* Cloud-based SOC deployment
* SOC-as-a-Service architecture

---

## 👨‍💻 Author

**Chethan M**


---

## 📚 Documentation

The detailed project report is available in the `docs/` directory.

For additional implementation details, refer to the source code, notebooks, configuration files, and project documentation included in this repository.
