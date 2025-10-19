# 🚀 Safety Equipment Detection using YOLOv8  

## 📌 Project Overview  
This project aims to **automatically detect safety equipment** (like fire extinguishers, oxygen tanks, first aid kits, etc.) using **YOLOv8**.  
The model is trained and deployed using **Google Colab (with T4 GPU)** to ensure smooth and fast training.

---

## 🧠 Problem Statement  
In many workplaces and industrial environments, it’s crucial to ensure safety equipment is properly placed.  
Manually monitoring is time-consuming and prone to errors.  

✅ **Solution:** Automated detection of safety equipment using a trained YOLOv8 model with a simple Streamlit-based app for real-time usage.

---

## 📂 Folder Structure
├── datasets
│ ├── train
│ │ ├── images
│ │ └── labels
│ ├── val
│ │ ├── images
│ │ └── labels
│ └── yolo_params.yaml
├── app.py
├── README.md

yaml
Copy code

---

## ⚡ Google Colab Setup Guide

### 1. 📥 Mount Google Drive
```python
from google.colab import drive
drive.mount('/content/drive')
2. 📦 Install Ultralytics and Streamlit
bash
Copy code
!pip install ultralytics
!pip install streamlit localtunnel
3. 🧭 Navigate to Your Dataset
bash
Copy code
%cd /content/drive/MyDrive/datasets
Make sure your yolo_params.yaml file correctly points to your train and val folders.

🧠 Training the Model
bash
Copy code
!yolo task=detect mode=train model=yolov8s.pt data=yolo_params.yaml epochs=100 batch=16 imgsz=640 device=0
✅ This will:

Use T4 GPU

Train the model for 100 epochs

Save best weights in runs/detect/train/weights/best.pt

🧪 Validating the Model
bash
Copy code
!yolo task=detect mode=val model=/content/drive/MyDrive/datasets/runs/detect/train/weights/best.pt data=yolo_params.yaml
You will get:

Precision

Recall

mAP@0.5

mAP@0.5–0.95

📸 Running Predictions
bash
Copy code
!yolo task=detect mode=predict model=/content/drive/MyDrive/datasets/runs/detect/train/weights/best.pt source='path/to/image_or_folder'
✅ Results are saved inside:
/content/drive/MyDrive/datasets/runs/detect/predict/

🌐 Deploying Streamlit App in Colab
1. Run Streamlit + LocalTunnel
bash
Copy code
!streamlit run app.py & npx localtunnel --port 8501
2. Get the Public Link
It will show something like:

csharp
Copy code
your url is: https://xxxxx.loca.lt
Click that link to view the app.

🛠️ Tech Stack
🐍 Python

⚡ Google Colab (T4 GPU)

🧠 YOLOv8 (Ultralytics)

📊 Streamlit

🪄 LocalTunnel (for deployment in Colab)

🧭 Future Scope
Real-time camera detection

Mobile & Edge device optimization

Alert systems for missing safety equipment

Integration with dashboards

📎 References
Ultralytics YOLO Docs

Streamlit Documentation

Google Colab

✨ Developed for: GenIgnite Hackathon 2025
👨‍💻 Team: Codex — Sneha, Sneha, Trijya, Saumya

yaml
Copy code
