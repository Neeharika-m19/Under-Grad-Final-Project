# ⚠️ Faulty Review Detector

> A Flask‑powered web app that classifies restaurant reviews as **truthful** or **deceptive** using a pre‑trained SVM model, and lets you explore the training dataset and data distribution graphically.

---

## 📋 Table of Contents

- [Demo](#-demo)  
- [Features](#-features)  
- [🔧 Installation](#-installation)  
- [⚙️ Configuration](#️-configuration)  
- [🚀 Running the App](#-running-the-app)  
- [📂 Project Structure](#-project-structure)  
- [🎯 How It Works](#-how-it-works)  
- [📈 Exploring Data & Models](#-exploring-data--models)  
- [💡 Future Improvements](#-future-improvements)  
- [🛠️ Tech Stack](#️-tech-stack)  

---

## 🎬 Demo

![home](./screenshots/home.png)  
*Enter a review → Predict truthfulness → View result GIF*  

---

## ✨ Features

- **Review Classification**: Predict whether a review is _truthful_ or _deceptive_.  
- **Interactive Web UI**: Clean, responsive design with animated gradients.  
- **Data Exploration**:  
  - View the original training **dataset** in tabular form.  
  - See a **bar chart** of truthful vs. deceptive counts.  
- **Model Persistence**: Uses `pickle`‑serialized SVM model & TF‑IDF vectorizer.  
- **Extensible**: Easily swap in new classifiers or datasets.

---

## 🔧 Installation

1. **Clone the repo**  
   ```bash
   git clone https://github.com/your‑username/your-project-name.git
   cd your-project-name
2. **Create a Python virtual environment**  
   ```bash
   python3 -m venv venv
   source venv\bin\activate
3. **Install dependencies**  
   ```bash
   pip install -r requirements.txt
   ```

## ⚙️ Configuration

No external API keys are required. Just ensure you have:

- `mlmodel.pickle` — your trained SVM classifier  
- `vectorizer.pickle` — your TF‑IDF vectorizer  
- `static/graph.png` — the saved bar chart image (generated via the notebook)  

---

## 🚀 Running the App

```bash
export FLASK_APP=app.py
export FLASK_ENV=development

flask run --port=5000
```
Then open your browser at:
http://localhost:5000/
```
## 📂 Project Structure

```text
faulty-review-detector/
├── app.py                      # Flask application & routes
├── mlmodel.pickle              # Trained SVM model (pickle)
├── vectorizer.pickle           # TF‑IDF vectorizer (pickle)
├── requirements.txt            # Python dependencies
├── templates/
│   ├── home.html               # Landing & input form
│   ├── result.html             # Prediction result (+ GIF)
│   ├── graph.html              # Bar‑chart view
│   └── dataset.html            # Raw dataset table
└── static/
    ├── styles.css              # All custom CSS
    ├── Fake.png                # Background image
    ├── negative-review.gif     # GIF for deceptive
    ├── positive-review.gif     # GIF for truthful
    └── graph.png               # Saved bar chart

```

## 🎯 How It Works

1. **Home** → User enters a review and clicks **Predict**.  
2. **Predict** →  
   - Text is vectorized via the loaded TF‑IDF model.  
   - SVM classifier outputs **truth** or **deceptive**.  
   - Result page shows verdict and an appropriate GIF.  
3. **Graph** → Displays the pre‑computed bar chart of label distribution.  
4. **Dataset** → Renders an HTML table of all reviews + labels.  

---

## 📈 Exploring Data & Models

This repo includes a Jupyter notebook (`fakerestarentreviewclassification.ipynb`) that:

- Loads ~3,000 hotel review files (*truthful* / *deceptive*).  
- Preprocesses text (lowercasing, stopword removal, POS tagging).  
- Vectorizes with TF‑IDF.  
- Tunes & trains a linear SVM.  
- Evaluates with cross‑validation, confusion matrix & classification report.  
- Serializes (pickle.dump) the final model & vectorizer.  
- Saves a bar chart (`graph.png`) of truthful vs. deceptive counts.  

---

## 💡 Future Improvements

- **Model Upgrades:** Try ensemble methods or deep learning.  
- **Live Graphing:** Dynamically regenerate charts on demand.  
- **Database & API:** Store reviews and predictions in a database; expose a REST API.  
- **Dockerization:** Containerize the entire stack for one‑click deployment.  
- **Tests & CI:** Add unit tests for routes & model predictions; integrate GitHub Actions.  

---

## 🛠️ Tech Stack

| Layer          | Technology                |
| -------------- | ------------------------- |
| **Framework**  | Flask                     |
| **Language**   | Python 3.x                |
| **ML**         | scikit‑learn (SVM)        |
| **Vectorizer** | scikit‑learn TF‑IDF       |
| **Templating** | Jinja2                    |
| **Styling**    | CSS (Flexbox, Animations) |
| **Visualization** | Matplotlib (bar chart) |
