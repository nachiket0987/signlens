<div align="center">

# 🤟 SignLens
**End-to-End Deep Learning Pipeline for Real-Time Sign Language Recognition**

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![PyTorch](https://img.shields.io/badge/PyTorch-%23EE4C2C.svg?style=for-the-badge&logo=PyTorch&logoColor=white)
![Flask](https://img.shields.io/badge/flask-%23000.svg?style=for-the-badge&logo=flask&logoColor=white)
![Docker](https://img.shields.io/badge/docker-%230db7ed.svg?style=for-the-badge&logo=docker&logoColor=white)
![AWS](https://img.shields.io/badge/AWS-%23FF9900.svg?style=for-the-badge&logo=amazon-aws&logoColor=white)

[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/nachiket0987)
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/nachiket-gadilohar-profile/)
[![Email](https://img.shields.io/badge/email-%23D14836.svg?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nachiketlohar0306@gmail.com)

</div>

---

## 📖 Project Overview

**SignLens** is a production-ready, end-to-end computer vision pipeline designed to bridge the communication gap for the deaf and hard-of-hearing community. By leveraging the power of **YOLOv5**, this system detects and translates sign language gestures in real-time. 

Built with scalability in mind, it features a robust MLOps workflow, including automated data ingestion, validation, model training, and continuous deployment (CI/CD) pipelines using Jenkins and Docker.

---

## ✨ Key Features

| Feature | Description |
| :---: | :--- |
| ⚡ **Real-time Inference** | Low-latency object detection using a fine-tuned YOLOv5s model. |
| 🔄 **End-to-End MLOps** | Fully automated pipeline from data ingestion to model deployment. |
| 📦 **Containerized** | Dockerized architecture ensures consistent environments across development and production. |
| ☁️ **Cloud Native** | Seamless deployment on AWS EC2 with continuous integration via Jenkins. |
| 🌐 **Interactive Web UI** | Easy-to-use Flask-based interface for uploading images or video streams for instant prediction. |
| 📊 **Experiment Tracking** | Integrated metrics tracking to monitor validation accuracy and loss during training. |

---

## 🏗️ Architecture & Workflow

```text
[ Data Source ] ➔ [ Data Ingestion ] ➔ [ Data Validation ] ➔ [ Feature Store ]
                                                                      │
                                                                      ▼
[ AWS EC2 / Docker ] ◄-- [ Jenkins CI/CD ] ◄-- [ Model Evaluation ] ◄-- [ Model Trainer (YOLOv5) ]
        │
        ▼
[ Flask Web UI ] ➔ [ User Inference ] ➔ [ Bounding Box & Predictions ]
```

---

## 🛠️ Tech Stack

### 🧠 Machine Learning
| Technology | Purpose |
| :--- | :--- |
| **Python 3.10** | Core programming language |
| **YOLOv5** | Object detection architecture |
| **PyTorch** | Deep learning framework |
| **Roboflow** | Data annotation and preprocessing |

### 🖥️ Frontend & Backend
| Technology | Purpose |
| :--- | :--- |
| **Flask** | Lightweight web application framework |
| **HTML/CSS/JS** | User interface and client-side logic |
| **Bootstrap** | Responsive UI components |

### ⚙️ Infrastructure & MLOps
| Technology | Purpose |
| :--- | :--- |
| **Docker & Docker Compose** | Containerization |
| **Jenkins** | CI/CD Pipeline automation |
| **AWS (EC2, S3)** | Cloud hosting and artifact storage |
| **GitHub Actions** | Automated workflow orchestration |

---

## 📂 Project Structure

```text
├── .github/workflows/       # GitHub Actions CI/CD pipelines
├── .jenkins/                # Jenkins configuration and Jenkinsfile
├── data/                    # Local dataset storage (ignored in git)
├── notebooks/               # Jupyter notebooks for exploration and testing
├── SignLens/            # Core Python package
│   ├── components/          # ML Pipeline steps (Ingestion, Validation, Training)
│   ├── configuration/       # Cloud and Database configurations
│   ├── constants/           # Global constants
│   └── entity/              # Data classes for configs and artifacts
├── templates/               # HTML templates for the Flask app
├── yolov5/                  # Cloned YOLOv5 repository for training
├── app.py                   # Flask application entry point
├── Dockerfile               # Docker image configuration
├── requirements.txt         # Python dependencies
└── setup.py                 # Package setup configuration
```

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- Git
- Docker & Docker Compose (optional for local deployment)
- AWS Account (for cloud deployment)

### 1. Local Setup

Clone the repository:
```bash
git clone https://github.com/nachiket0987/signlens.git
cd signlens
```

Create and activate a virtual environment:
```bash
conda create -n signlens python=3.10 -y
conda activate signlens
```

Install dependencies:
```bash
pip install -r requirements.txt
```

### 2. Run the Application

Start the Flask server:
```bash
python app.py
```
Navigate to `http://localhost:8080` in your browser.

---

## 🔐 Environment Variables

To run the pipeline locally or in production, set the following environment variables:

| Variable | Description | Required |
| :--- | :--- | :---: |
| `DATA_DOWNLOAD_URL` | Google Drive or S3 link to download the dataset | ✅ |
| `AWS_ACCESS_KEY_ID` | Your AWS Access Key | Optional |
| `AWS_SECRET_ACCESS_KEY` | Your AWS Secret Key | Optional |
| `AWS_REGION` | AWS Region (e.g., `us-east-1`) | Optional |

**Windows (Anaconda Prompt):**
```bash
set DATA_DOWNLOAD_URL="https://drive.google.com/uc?/export=download&id=YOUR_FILE_ID"
```

**Mac/Linux (Bash):**
```bash
export DATA_DOWNLOAD_URL="https://drive.google.com/uc?/export=download&id=YOUR_FILE_ID"
```

---

## 🔌 API Reference

### Health Check
Check if the API is running.
- **Endpoint**: `/`
- **Method**: `GET`
- **Response**: Renders `index.html`

### Predict Image
Upload an image (base64 encoded) to receive object detection predictions.
- **Endpoint**: `/predict`
- **Method**: `POST`
- **Payload**: JSON object containing base64 image data.

**Example cURL:**
```bash
curl -X POST http://localhost:8080/predict \
     -H "Content-Type: application/json" \
     -d '{"image": "base64_encoded_string_here"}'
```

### Train Model
Trigger the training pipeline manually.
- **Endpoint**: `/train`
- **Method**: `GET`
- **Response**: `Training done successfully!`

**Example cURL:**
```bash
curl -X GET http://localhost:8080/train
```

---

## 🚢 Deployment Guide

### Docker Deployment
Build and run the container locally:

```bash
docker build -t signlanguage-app .
docker run -p 8080:8080 signlanguage-app
```

### AWS EC2 + Jenkins (CI/CD)
1. Launch an Ubuntu EC2 instance.
2. Install Docker, AWS CLI, and Jenkins using the provided scripts in `scripts/`.
3. Configure AWS credentials (`aws configure`).
4. Set up a Jenkins Pipeline job linked to your GitHub repository and select the `Jenkinsfile`.
5. Push to the `main` branch to trigger an automated build and deployment!

---

## 🛠️ Troubleshooting

| Issue | Possible Cause | Solution |
| :--- | :--- | :--- |
| **Model not downloading** | Invalid `DATA_DOWNLOAD_URL` | Verify your Google Drive file ID and ensure the file is public. |
| **OutOfMemoryError** | Insufficient RAM/VRAM | Reduce batch size in `constants/training_pipeline/__init__.py` or upgrade hardware. |
| **Docker build fails** | Missing dependencies | Check `requirements.txt` or ensure `yolov5` submodule is initialized. |
| **Port 8080 in use** | Another service is running | Change the Flask port in `app.py` or kill the existing process. |

---

## 🤝 Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---



<div align="center">

**Developed with ❤️ by Nachiket Gadilohar**

[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/nachiket0987)
[![LinkedIn](https://img.shields.io/badge/linkedin-%230077B5.svg?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/nachiket-gadilohar-profile/)
[![Email](https://img.shields.io/badge/email-%23D14836.svg?style=for-the-badge&logo=gmail&logoColor=white)](mailto:nachiketlohar0306@gmail.com)

</div>
