# 🚦 Intelligent Speed Monitoring and Alert System for Traffic Management

## 📌 Project Overview

The **Intelligent Speed Monitoring and Alert System** is a real-time traffic monitoring solution designed to:

- Monitor vehicle speeds
- Detect and log speed violations
- Automatically recognize vehicle number plates
- Notify authorities via email with violation details

This project was developed during the **NVIDIA GRIL Training Program**, an intensive AI-focused program powered by NVIDIA. It leverages **GPU-accelerated DGX systems** and frameworks like **PyTorch** and **OpenCV** for real-time processing.

---

## 🎯 System Pipeline

```
[Camera Input] 
      ↓
[OpenCV] → Vehicle Detection → Speed Estimation
      ↓
[Violation Check] → If overspeed:
      ↓
[Frame Capture] → [PyTorch Model: Number Plate Recognition]
      ↓
[Email Notification System]
```

---

## 🛠️ Setup Instructions

### 1. Access DGX Server

- Open your browser and visit:  
  `http://<DGX_IP>:<application_port>`
- Log in with the credentials provided by your admin.

### 2. Create Environment

- **Resource Allocation:**
  - RAM: 6 GB
  - CPU: 8 Cores
  - GPU: 1 (20GB VRAM)
- Environment Name: `test`
- Select the appropriate **PyTorch container image**
- Flask default port: `5000`

### 3. Virtual Environment Setup

```bash
sudo apt update
sudo apt install python3.8-venv
python3.8 -m venv newenv
source newenv/bin/activate
```

### 4. Install Python Dependencies

```bash
pip install -r requirements.txt
```

### 5. Transfer Files to DGX Server

```bash
scp -r -P <port_number> <local_folder> user@<DGX_IP>:<remote_folder>
```

### 6. Run the System

```bash
python3 app.py
```

---

## 🖼️ Annotations & Dataset Preparation

### 🚗 Vehicle Annotation

- Use tools like [LabelImg](https://github.com/tzutalin/labelImg) or [Roboflow](https://roboflow.com)
- Draw bounding boxes around vehicles
- Label each object as `"car"` or appropriate class
- Annotate a diverse set of images for better generalization

### 🔢 Number Plate Recognition

- Train a **PyTorch-based OCR model** using annotated license plate images
- Export the trained model to inference-ready format
- Use this model to extract text from detected plates during violation events

---

## 📧 Email Notification

When a speed violation is detected:

- Capture the frame of the vehicle
- Use the OCR model to extract the license plate number
- Send an automated email using `smtplib` with:
  - 📷 Captured image as an attachment
  - 🔢 Recognized plate number in the email body

---

## ✅ Key Features

- ✅ Real-time vehicle tracking and speed estimation
- ✅ Speed violation detection
- ✅ Number plate recognition (ANPR)
- ✅ Automated alert via email
- ✅ GPU-accelerated deployment on NVIDIA DGX

---

## 🎓 Developed Under: NVIDIA GRIL

This project was developed under the **NVIDIA GRIL (GPU Research Innovation Lab)** — a hands-on, research-driven AI program focused on leveraging high-performance computing for real-world problem solving.

---

## 🙌 Acknowledgements

- NVIDIA GRIL Team – for providing infrastructure and mentorship  
- Open-source contributors – PyTorch, Flask, OpenCV  
- Community dataset providers – for public training data

---

## 🏁 Conclusion

This project demonstrates a powerful, real-time traffic management system using AI and computer vision. It minimizes manual enforcement and enhances road safety by automating violation detection and reporting. With GPU-accelerated computing, it is capable of processing high-resolution video streams efficiently and accurately.

---


