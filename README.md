# 🚦 AI Traffic Violation Detection & E-Challan System

An advanced, AI-powered traffic monitoring and automatic e-challan generation system. This project uses YOLOv8 and computer vision to detect multiple traffic violations in real-time and automatically issues citations to offenders via an integrated backend system.

---

## 🌟 Key Features

- **🪖 Helmet Detection**: Identifies two-wheeler riders without helmets.
- **🏍️ Triple Riding Detection**: Detects more than two passengers on a single two-wheeler.
- **🔴 Red Light Violation**: Monitors vehicles crossing the stop line during a red light.
- **🔢 License Plate Recognition (ANPR)**: Automatically extracts license plate numbers of violating vehicles using OCR.
- **🎫 Automatic E-Challan Generation**: Creates a digital challan (ticket) immediately upon detecting a violation.
- **📱 SMS Notifications**: Sends instant alerts to violators using Twilio integration.
- **💻 Interactive Dashboard**: A modern web application to view violations, generate reports, and manage challans.

---

## 🏗️ System Architecture

The project is divided into several robust components:

- **Central Detection Manager**: Coordinates all AI models (`central_detection_manager.py`).
- **AI Modules**: Standalone models for specific violations (`detect_helmet.py`, `detect_triple_riding.py`, `red_light_violation.py`, `license_plate_detection/`).
- **Backend (Flask/FastAPI)**: Manages the database, APIs, and E-Challan logic (`backend/`).
- **Frontend (React)**: An interactive UI for authorities to monitor traffic and review challans (`frontend/`).
- **Database (MongoDB)**: Stores vehicle data, user records, and violation history.

---

## 🚀 Getting Started

### Prerequisites
- **Python 3.8+**
- **Node.js** (for frontend)
- **MongoDB** (running locally or via Atlas)

### 1. Clone & Install Dependencies

```bash
# Install Python dependencies
pip install -r requirements.txt
```

### 2. Environment Setup

Create a `.env` file in the root directory (you can use `.env.example` as a template) and add your configurations:

```env
MONGO_URI=your_mongodb_connection_string
TWILIO_ACCOUNT_SID=your_twilio_sid
TWILIO_AUTH_TOKEN=your_twilio_token
TWILIO_PHONE_NUMBER=your_twilio_phone
```

### 3. Running the Application

You can start the backend and frontend using the provided batch scripts (Windows) or manually.

**Start the Backend (API & Detection Engine):**
```bash
# Using batch script
start_backend.bat

# Or manually
python app.py
```

**Start the Frontend (Web Dashboard):**
```bash
# Using batch script
start_frontend.bat

# Or manually
cd frontend
npm install
npm run dev
```

*(Alternatively, use `docker-compose up --build` if you prefer a containerized setup!)*

---

## 📁 Directory Structure

```text
├── backend/                  # API endpoints, DB, and notification services
├── frontend/                 # React-based web dashboard
├── license_plate_detection/  # ANPR and OCR logic
├── models/                   # Pre-trained AI models
├── tests/                    # Testing scripts for modules (YOLO, OCR, etc.)
├── training/                 # Scripts to train/fine-tune models
├── central_detection_manager.py  # Main pipeline manager
├── detect_*.py               # Individual detection modules
└── README.md                 # Project documentation
```

---

## 🧠 Model Training

If you want to train the models on your custom dataset, training scripts have been organized into the `training/` directory. 

```bash
# Example: Train the helmet detection model
python training/train_helmet_clean.py
```

## 🧪 Testing

All test scripts are located in the `tests/` directory to keep the root clean. You can run them to verify individual modules:

```bash
python tests/test_helmet_system.py
python tests/test_triple_riding.py
python tests/test_easyocr.py
```

---

## 🤝 Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License.
