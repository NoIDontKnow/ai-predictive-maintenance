<!---Bismillahirrahmanirraheem--->
# 🚀 AI Predictive Maintenance & LLM Workflow System

A **production-ready AI-native application** for predictive maintenance, LLM-powered workflows, and dynamic scheduling—**deployed for free** using **Git + Python DevOps** (no Docker, no VMs).

---

## 📌 **About the Project**
This project demonstrates:
- **Predictive maintenance** using ML models (Scikit-learn, TensorFlow/PyTorch).
- **LLM workflows** for intelligent decision-making (OpenAI API, LangChain).
- **Dynamic scheduling** based on AI predictions.
- **End-to-end ownership** of frontend, backend, database, and DevOps—**all for free**.

**Key Difference**: Uses **Git + Python scripts** for DevOps (no Docker, no VMs, no extra software).

---

## ✨ **Key Features**


Key Features


| Feature               | Description                                      | Technologies Used                     |
|-----------------------|--------------------------------------------------|---------------------------------------|
| Predictive Maintenance| Predicts equipment failures using ML models.    | Python, Scikit-learn, TensorFlow      |
| LLM Workflows         | Automates reports and chatbot support.           | OpenAI API, LangChain, Hugging Face    |
| Dynamic Scheduling    | Schedules maintenance tasks based on AI.        | FastAPI, Celery, Redis                 |
| Full-Stack Ownership  | Owns frontend, backend, database, and DevOps.    | React.js, FastAPI, MongoDB, Python    |
| Free DevOps           | Automates testing/deployment with Git + Python. | GitHub, Python scripts, Render/Vercel |

---

## 🛠 **Tech Stack**

### **Frontend**
- **Framework**: React.js (TypeScript)
- **UI Library**: Material-UI / Tailwind CSS
- **State Management**: Redux / Zustand

### **Backend**
- **Framework**: FastAPI (Python)
- **Authentication**: JWT, OAuth2
- **Database**: MongoDB (with Beanie ODM)

### **AI/ML Stack**
- **Machine Learning**: Scikit-learn, TensorFlow, PyTorch
- **LLMs**: OpenAI API, LangChain, Hugging Face Transformers

### **DevOps Stack**
- **Version Control**: Git + GitHub
- **Automation**: Python scripts (`setup.py`, `test.py`, `deploy.py`)
- **CI/CD**: GitHub Actions (optional)
- **Hosting**:
  - Backend: [Render (Free Tier)](https://render.com/)
  - Frontend: [Vercel (Free Tier)](https://vercel.com/)
  - Database: [MongoDB Atlas (Free Tier)](https://www.mongodb.com/atlas/database)

---

## 🚀 **Why This Approach?**
- **100% Free**: Uses free tiers of Render, Vercel, MongoDB Atlas, and GitHub.
- **No Docker/VMs**: Relies on **Git + Python scripts** for automation.
- **Simple**: Easy to understand, maintain, and scale.
- **Production-Ready**: Deployed on cloud services with CI/CD (optional).

---

## 📂 **Project Structure**
```
ai-predictive-maintenance/
│
├── /frontend               # React.js application
│   ├── public/
│   ├── src/
│   └── package.json
│
├── /backend                # FastAPI server
│   ├── app/
│   ├── ml_models/
│   ├── requirements.txt
│   └── README.md
│
├── /scripts                # DevOps Python scripts
│   ├── setup.py            # Install dependencies
│   ├── test.py             # Run tests
│   └── deploy.py           # Deploy to Render/Vercel
│
├── .github/
│   └── workflows/
│       └── devops.yml      # GitHub Actions (optional)
│
├── README.md
└── LICENSE
```

---

## 🛠 **Getting Started**

### **Prerequisites**
- Python 3.10+
- Node.js 16+
- Git
- Free accounts on [GitHub](https://github.com/), [Render](https://render.com/), [Vercel](https://vercel.com/), and [MongoDB Atlas](https://www.mongodb.com/atlas/database)

---

### **1. Local Setup**
#### **Clone the Repo**
```bash
git clone https://github.com/yourusername/ai-predictive-maintenance.git
cd ai-predictive-maintenance
```

#### **Install Dependencies**
Run the Python script to install all dependencies:
```bash
python scripts/setup.py
```

#### **Run Locally**
- **Backend**:
  ```bash
  cd backend
  uvicorn app.main:fastapi_app --reload
  ```
- **Frontend**:
  ```bash
  cd frontend
  npm start
  ```

---

### **2. Configure MongoDB Atlas**
1. Sign up for [MongoDB Atlas](https://www.mongodb.com/atlas/database).
2. Create a **free cluster** and whitelist your IP.
3. Create a database user and get the connection string.
4. Add the connection string to your backend `.env`:
   ```env
   MONGO_DETAILS=mongodb+srv://<username>:<password>@cluster0.example.mongodb.net/ai_maintenance?retryWrites=true&w=majority
   ```

---

### **3. Deploy to Cloud (Free)**
#### **Backend: Render**
1. Sign up for [Render](https://render.com/).
2. Connect your GitHub repo.
3. Create a **Web Service**:
   - **Name**: `ai-maintenance-backend`
   - **Root Directory**: `backend`
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: `gunicorn -k uvicorn.workers.UvicornWorker -w 4 -b 0.0.0.0:$PORT app.main:fastapi_app`
4. Render will auto-deploy when you push to `main`.

#### **Frontend: Vercel**
1. Sign up for [Vercel](https://vercel.com/).
2. Import your GitHub repo.
3. Vercel will auto-detect React and deploy it.
4. Auto-deploys on push to `main`.

#### **Database: MongoDB Atlas**
- Already configured in Step 2.

---
### **4. Automate with Python Scripts**
Use the provided Python scripts to **install, test, and deploy** your app:

- **Install dependencies**:
  ```bash
  python scripts/setup.py
  ```
- **Run tests**:
  ```bash
  python scripts/test.py
  ```
- **Deploy** (manual trigger):
  ```bash
  python scripts/deploy.py
  ```

---
### **5. (Optional) Automate with GitHub Actions**
To **fully automate** testing and deployment, set up GitHub Actions:

1. Create `.github/workflows/devops.yml` (see example below).
2. Add your **Vercel and Render API keys** as GitHub secrets (`VERCEL_TOKEN`, `RENDER_API_KEY`).

**Example Workflow**:
```yaml
name: DevOps Pipeline
on: [push]

jobs:
  setup:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.10'
      - name: Install dependencies
        run: python scripts/setup.py

  test:
    needs: setup
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Run tests
        run: python scripts/test.py

  deploy:
    needs: test
    runs-on: ubuntu-latest
    if: github.ref == 'refs/heads/main'
    steps:
      - uses: actions/checkout@v4
      - name: Deploy
        run: python scripts/deploy.py
```

---
---
## 📊 **Example Workflows**

### **1. Predictive Maintenance**
1. Sensor data → **MongoDB Atlas**.
2. FastAPI calls **predictive model** (TensorFlow).
3. If failure risk > threshold → **alert via WebSocket/Email**.
4. React dashboard displays **real-time predictions**.

### **2. LLM-Powered Reports**
1. User query: *"Generate a report for Equipment X."*
2. LangChain retrieves **sensor logs/past issues** from MongoDB.
3. OpenAI GPT-4 generates a **natural language report**.
4. Report saved to **MongoDB** and displayed in React.

---
---
## 🎯 **Future Improvements**
- Add **JWT authentication** for secure API access.
- Implement **WebSockets** for real-time alerts.
- Optimize models for **edge deployment** (e.g., ONNX, TensorRT).
- Add **more LLM use cases** (e.g., voice assistants, automated work orders).

---
---
## 🤝 **Contributing**
1. Fork the repo.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a **Pull Request**.

---
---
## 📜 **License**
This project is licensed under the **MIT License** – see the [LICENSE](LICENSE) file for details.

---
---
## 📞 **Contact**
- **Email**: [abdaferfav@tuta.io](mailto:abdaferfav@tuta.io)
- **GitHub**: [@NoIDontKnow](https://github.com/NoIDontKnow)
- **LinkedIn**: [Favour Abayomi-Dada](https://linkedin.com/in/favourabayomi-dada)
```

---
