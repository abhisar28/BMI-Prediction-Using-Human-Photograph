# BMI Prediction Using Human Photograph

A web application for predicting Body Mass Index (BMI) from images using deep learning. The system supports full body, face, and combined BMI predictions, and maintains a history of predictions.

---

## Technologies Used

### Backend

- **Python 3.8+**
- **Flask** — REST API framework
- **PyTorch** — For full body BMI prediction using a ResNet101 model
- **TensorFlow Lite** — For face BMI prediction using a TFLite model
- **OpenCV & facenet-pytorch (MTCNN)** — For face detection and image processing
- **Flask-SQLAlchemy** — ORM for database management
- **SQLite** — Lightweight database for storing prediction history

### Frontend

- **React** — Modern JavaScript UI library
- **Vite** — Fast development server and build tool
- **CSS (Poppins font, custom styles)** — For a modern, responsive UI

---

## Models

- **Full Body BMI Model:**  
  - Architecture: ResNet101 (PyTorch)
  - File: `best_resnet101_model.pth`
  - Input: Full body images
  - Output: Predicted BMI value

- **Face BMI Model:**  
  - Architecture: Custom model (TensorFlow Lite format)
  - File: `model.tflite`
  - Input: Cropped face images (detected using MTCNN)
  - Output: Predicted BMI value

- **Combined BMI:**  
  - Combines predictions from both models using a weighted formula for improved accuracy.

---

## Database

- **Type:** SQLite (file-based, no setup required)
- **File:** `bmi-backend/instance/predictions.db`
- **Managed by:** Flask-SQLAlchemy
- **Stores:**  
  - Timestamp of prediction  
  - Full body BMI  
  - Face BMI  
  - Combined BMI  
  - Base64-encoded face image

---

## Project Structure

```
bmi_prediction/
  bmi-backend/      # Flask backend (API, models, database)
  bmi-frontend/     # React frontend (UI)
```

---

## Getting Started

### 1. Backend Setup

**Requirements:**  
- Python 3.8+
- pip

**Install dependencies:**
```bash
cd bmi-backend
pip install -r requirements.txt
```

**Start the backend server:**
```bash
python app.py
```
- The backend runs on `http://localhost:5000`

### 2. Frontend Setup

**Requirements:**  
- Node.js (v16+ recommended)
- npm

**Install dependencies:**
```bash
cd bmi-frontend
npm install
```

**Start the frontend server:**
```bash
npm run dev
```
- The frontend runs on `http://localhost:5173` (or as shown in your terminal)

---

## Usage

1. Open the frontend in your browser.
2. Upload one or more images (full body or face).
3. Choose the prediction type: Full Body, Face, or Combined BMI.
4. View results and prediction history.

---

## API Endpoints

- `POST /extract-faces` — Extracts faces from uploaded images.
- `POST /predict-bmi` — Predicts BMI from full body images.
- `POST /predict-face-bmi` — Predicts BMI from face images.
- `POST /predict-combined-bmi` — Predicts combined BMI.
- `GET /prediction-history` — Retrieves prediction history.
- `DELETE /prediction-history/<id>` — Deletes a prediction record.

---

## Notes

- Pre-trained model files (`best_resnet101_model.pth`, `model.tflite`) are required in the backend folder.
- The backend uses a SQLite database (`predictions.db`) to store prediction history.
- For best results, use clear, well-lit images.

---

**Built by Group 21**
