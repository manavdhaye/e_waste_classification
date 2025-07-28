📦 E-WASTE CLASSIFICATION & DISPOSAL DECISION SYSTEM
===================================================

🧠 Model Accuracy: 78%
🏷️ Supported Classes: 77 types of e-waste (see full list in train.csv)
🔗 Dataset & Model Links: Provided below

---

📝 PROJECT OVERVIEW
====================
This project is a complete deep learning-based solution for classifying different types of electronic waste (e-waste) using the MobileNetV2 architecture. After classification, it makes an informed decision whether the item should be **resold**, **recycled**, or **disposed**.

🎯 Goals:
---------
1. Classify 77 types of electronic waste (e.g., smartphones, laptops, TVs, routers, etc.)
2. Decide the appropriate action: **Reuse (Resell)**, **Recycle**, or **Dispose**
3. Provide a mobile-friendly UI to capture or select images and display predictions

---

📁 DATASET & MODEL FILES
=========================
All relevant dataset files are hosted on Google Drive:

- 📂 Train Images ZIP:
  https://drive.google.com/file/d/1unIZtTXnT26_U9fDwnMdLFZz-gRXEwn7/view?usp=drive_link

- 📂 Validation Images ZIP:
  https://drive.google.com/file/d/1KDfXjPuU-cn8uPraM3xmQBRveeSude9h/view?usp=drive_link

- 📄 Training Labels CSV:
  https://drive.google.com/file/d/1UeVxjaB2ydfFRGWAlGK-SZqQ-fyweyCc/view?usp=drive_link

- 📄 Validation Labels CSV:
  https://drive.google.com/file/d/1wDqrG_-tR1IodlIZ8J0Pl4R6DlFUx0bh/view?usp=drive_link

---

🔧 TECHNICAL STACK
===================
- TensorFlow/Keras (MobileNetV2)
- Python (cv2, numpy, pandas, matplotlib, PIL)
- Android Studio (Java + TensorFlow Lite)
- TFLite Model (Converted and integrated into Android app)
- Cosine similarity for damage assessment
- Custom DataGenerator for efficient training

---

📸 ANDROID APP FUNCTIONALITY
==============================
- Capture image from camera or pick from gallery
- Image is classified into one or more of 77 categories
- Final decision is shown: `Dispose`, `Recycle`, or `Resell`
- TensorFlow Lite model embedded for real-time prediction

---

🚀 TRAINING DETAILS
====================
- Base Model: MobileNetV2 (pretrained on ImageNet)
- Custom classifier head with:
    - GlobalAveragePooling
    - Dense(128) with ReLU
    - Dropout(0.4)
    - Output Layer: 77 units with sigmoid (multi-label)
- Optimizer: Adam
- Loss: Binary Crossentropy
- Metrics: Accuracy
- Epochs: 30 (with early stopping and learning rate scheduler)
- Accuracy Achieved: ~78%

---

📊 E-WASTE PROCESSING DECISION
===============================
After classification, another model compares the input image with a sample database of labeled e-waste images. Based on cosine similarity of extracted features (using MobileNetV2), it classifies the item into one of the three categories:

- 🔁 Reuse (Resell)
- ♻️ Recycle
- 🗑️ Dispose

Features are pre-saved using a `pickle` file (`image_db.pkl`) to avoid recomputation.

