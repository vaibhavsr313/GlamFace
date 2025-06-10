
# ✨ GlamFace: AI-Powered Hairstyle Recommendation App  
**🧠 Your Personal AI Stylist – Because your face shape and hair texture matter!**

---

## 📱 About the Project  
**GlamFace** is a smart Android application that recommends the most flattering hairstyles based on your **face shape** and **hair texture**. Using two powerful deep learning models, GlamFace analyzes your selfie and gives you instant, personalized hairstyle suggestions that suit your look!

---

## 🧠 Core Features  
- 🔍 **Face Shape Detection** – Trained on 5000+ images using **VGG16**, detects:  
  `Heart`, `Oblong`, `Oval`, `Round`, `Square`
- 🧬 **Hair Texture Classification** – Trained using **MobileNetV2** to detect:  
  `Straight`, `Wavy`, `Curly`
- 🤳 **Selfie Input** – Capture and analyze your selfie right in the app!
- 🎨 **Aesthetic UI** – Stylish, modern Android UI with smooth transitions
- 🔐 **Firebase Auth** – User login and signup functionality
- 💾 **Firebase Realtime Database** – Store liked hairstyles
- 🎯 **Combo-based Recommendations** – Hairstyles are recommended based on the perfect pairing of face shape and hair texture

---

## 🛠️ Tech Stack  

| Area               | Technology Used                               |
|--------------------|-----------------------------------------------|
| Android App        | Java, XML, Android Studio                     |
| ML Model 1         | VGG16 for Face Shape Detection                |
| ML Model 2         | MobileNetV2 for Hair Texture                  |
| Image Processing   | OpenCV, MediaPipe, Rembg, Pillow (PIL)        |
| Authentication     | Firebase Authentication                       |
| Database           | Firebase Realtime Database                    |
| Deployment         | App uses local `.tflite` models               |

---

## 🧑‍🔬 Dataset Summary  

### 🧠 Face Shape Dataset  
- 📊 Classes: `Heart`, `Oblong`, `Oval`, `Round`, `Square`  
- 🏋️ Training: 800 images/class → **4000 total**  
- 🧪 Testing: 200 images/class → **1001 total**

### 💇 Hair Texture Dataset  
- 📊 Classes: `Curly`, `Straight`, `Wavy`  
- 🔢 Samples:  
  - Curly: 339  
  - Straight: 324  
  - Wavy: 331

---

## 🔍 Model Performance  

### 🧠 Face Shape (VGG16)  
- ✅ Accuracy: **75.66%**  
- 🔝 Top-2 Accuracy: **88.83%**

### 💇 Hair Texture (MobileNetV2)  
- ✅ Accuracy: **88.33%**  
- 🔝 Top-2 Accuracy: **98.67%**

---

## 📄 Classification Report (Hair Texture)
```
               precision    recall  f1-score   support

   Curly Hair       0.98      0.93      0.95       102  
Straight Hair       0.87      0.85      0.86        98  
    Wavy Hair       0.81      0.87      0.84       100  

    Accuracy                            0.88       300  
   Macro Avg       0.89      0.88      0.88       300  
Weighted Avg       0.89      0.88      0.88       300  
```

---

## 🧪 Preprocessing Pipeline  
**Applied consistently during both training & prediction.**

### ✅ Face Shape Preprocessing  
- 📤 **Remove background** with `rembg`  
- 👁️ **Detect & align face** using `MediaPipe Face Detection`  
- 📏 **Resize** to (224x224) and **normalize**  
- 🛠️ Libraries: `rembg`, `MediaPipe`, `OpenCV`, `Pillow`, `NumPy`

### ✅ Hair Texture Preprocessing  
- 🖼️ Use full image **after background removal**  
- 📐 Resize to **(256x256)** → then **(224x224)**  
- ⚖️ **Normalize** image  
- 🛠️ Libraries: `OpenCV`, `Pillow`, `TensorFlow Keras img_to_array`

---

## 📷 Example Code  
```python
# Predict Face Shape & Hair Texture
face_label = face_class_labels[np.argmax(face_model.predict(face_input)[0])]
hair_label = hair_class_labels[np.argmax(hair_model.predict(hair_input)[0])]
print(f"🧠 Face Shape: {face_label}")
print(f"💇 Hair Texture: {hair_label}")
```

---

## 🎨 App Screens  
Add screenshots in this section. Suggested images:

- 🖼️ Splash screen  
- 🔐 Login / Signup page  
- 🤳 Selfie capture  
- 🧠 Predicted results screen  
- 💇 Recommended hairstyles  

```
![Splash](screenshots/splash.png)  
![Login](screenshots/login.png)  
![Recommendations](screenshots/results.png)  
```

---

## 📋 Style Recommendation Example  
**For** `Oval + Curly`:  
```java
if ("Oval".equals(face) && "Curly".equals(hair)) {
    list.add(new Style(R.drawable.curly_bob_with_layers, "Curly Bob with Layers"));
    list.add(new Style(R.drawable.shoulder_length_voluminous_curls, "Shoulder-Length Voluminous Curls"));
    list.add(new Style(R.drawable.pineapple_updo, "Pineapple Updo"));
    list.add(new Style(R.drawable.half_up_curly_bun, "Half-Up Curly Bun"));
}
```

---

## 🔐 User Flow in App  
1. 👋 Splash Screen  
2. 🔐 Login / Signup (via Firebase)  
3. 📸 Add your selfie  
4. 🧠 Model predicts face shape & hair texture  
5. 💇 Get hairstyle recommendations  
6. ❤️ Like & save styles to Firebase  

---

## 🌟 Why GlamFace?  
✅ Accurate deep learning models  
📱 Seamless Android experience  
👩 Personalized recommendations  
🔁 Real-time prediction pipeline  
🔒 Secure Firebase integration  
❤️ Save your favorite styles  

---

## 🚀 Future Improvements  
- 🎯 Add hairstyle filtering (occasion, age)  
- 👨 Include male hairstyle recommendations  
- ☁️ Deploy models on cloud for scalability  
- 🪞 Add **AR view** for hairstyle try-on  

---

## 🏁 Getting Started  
1. 📥 Clone the repo  
2. 🧠 Train or load models using provided scripts  
3. 💻 Import the Android project in Android Studio  
4. 🔐 Setup Firebase config for Auth & DB  
5. 📲 Build and run the app on device/emulator  

---

## 📂 Project Structure  
```
GlamFace/
│
├── AndroidApp/
│   ├── app/src/...
│   ├── Firebase setup
│   └── tflite models
│
├── FaceShapeModel/
│   └── VGG16 training + preprocessing
│
├── HairTextureModel/
│   └── MobileNetV2 training + preprocessing
│
└── README.md
```
