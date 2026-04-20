<p align="center">
  <img src="https://img.shields.io/badge/Python-3.8+-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit">
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white" alt="scikit-learn">
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white" alt="Pandas">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge" alt="License">
</p>

<h1 align="center">🌬️ AirAware System</h1>

<p align="center">
  <b>An end-to-end Air Quality Index (AQI) prediction and monitoring system powered by Machine Learning</b>
</p>

<p align="center">
  Predict · Analyze · Alert · Visualize
</p>

<p align="center">
  <a href="https://airaware-system-aqcpndcqiq3bcxl5mtfzum.streamlit.app/">
    <img src="https://static.streamlit.io/badges/streamlit_badge_black_white.svg" alt="Open in Streamlit">
  </a>
</p>

> 🔗 **Live Demo:** [https://airaware-system-aqcpndcqiq3bcxl5mtfzum.streamlit.app/](https://airaware-system-aqcpndcqiq3bcxl5mtfzum.streamlit.app/)

---

## 📖 About

**AirAware** is a comprehensive air quality monitoring and forecasting system that leverages a **Random Forest Regressor** to predict the Air Quality Index (AQI) for cities across India. The project follows a milestone-based architecture — from raw data preprocessing to an interactive Streamlit dashboard — making it easy to understand, extend, and deploy.

### ✨ Key Highlights

- 🔮 **ML-Powered Forecasting** — Predict AQI values using a trained Random Forest model
- 📊 **Interactive Dashboard** — City-wise AQI monitoring with Streamlit
- ⚠️ **Smart Health Alerts** — Automated alerts based on AQI severity levels
- 📈 **Trend Analysis** — Monthly AQI trend visualization with Seaborn & Matplotlib
- 🏗️ **Modular Architecture** — Clean, milestone-based project structure

---

## 🗂️ Project Structure

```
AirAware-System/
│
├── data/
│   └── air_quality.csv              # Raw air quality dataset (14 pollutant features)
│
├── milestone1_data_preprocessing/
│   ├── data_cleaning.py             # Data loading, cleaning & missing value handling
│   └── feature_engineering.py       # Temporal feature extraction (Year, Month, Day, DayOfWeek)
│
├── milestone2_forecasting_model/
│   ├── train_model.py               # Random Forest model training & evaluation
│   └── aqi_model.pkl                # Serialized trained model (auto-downloaded if missing)
│
├── milestone3_aqi_analysis/
│   ├── aqi_category.py              # AQI → Category classification (Good → Hazardous)
│   ├── alert_system.py              # Health alert generation based on AQI levels
│   ├── predict_aqi.py               # AQI prediction pipeline using the trained model
│   └── trend_analysis.py            # Monthly AQI trend plotting
│
├── milestone4_dashboard/
│   └── app.py                       # Streamlit dashboard application
│
├── reports/
│   └── eda_report.html              # Exploratory Data Analysis report
│
├── requirements.txt                 # Python dependencies
├── .gitignore
└── README.md
```

---

## 📊 Dataset

The dataset (`data/air_quality.csv`) contains daily air quality measurements from multiple Indian cities starting from **2015**.

| Feature | Description |
|---------|-------------|
| `City` | Name of the city |
| `Date` | Date of measurement |
| `PM2.5` | Fine particulate matter (μg/m³) |
| `PM10` | Coarse particulate matter (μg/m³) |
| `NO` | Nitric oxide (μg/m³) |
| `NO2` | Nitrogen dioxide (μg/m³) |
| `NOx` | Nitrogen oxides (ppb) |
| `NH3` | Ammonia (μg/m³) |
| `CO` | Carbon monoxide (mg/m³) |
| `SO2` | Sulphur dioxide (μg/m³) |
| `O3` | Ozone (μg/m³) |
| `Benzene` | Benzene (μg/m³) |
| `Toluene` | Toluene (μg/m³) |
| `Xylene` | Xylene (μg/m³) |
| `AQI` | Air Quality Index (target variable) |
| `AQI_Bucket` | AQI category label |

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8 or higher
- pip (Python package manager)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/satyajitsonkar96/AirAware-System.git
   cd AirAware-System
   ```

2. **Create and activate a virtual environment**

   ```bash
   python -m venv venv

   # Windows
   venv\Scripts\activate

   # macOS / Linux
   source venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

---

## ⚙️ Usage

### 1️⃣ Data Preprocessing

Clean the raw data and generate temporal features:

```bash
cd milestone1_data_preprocessing
python data_cleaning.py
```

### 2️⃣ Train the Forecasting Model

Train the Random Forest Regressor on the cleaned data:

```bash
python milestone2_forecasting_model/train_model.py
```

> **Note:** The trained model (`aqi_model.pkl`) is ~157 MB and excluded from Git via `.gitignore`. It will be **automatically downloaded** from Google Drive when you launch the dashboard for the first time.

### 3️⃣ Predict AQI & View Alerts

Run the prediction pipeline with health alerts:

```bash
cd milestone3_aqi_analysis
python predict_aqi.py
```

**Sample Output:**
```
Predicted AQI: 185
AQI Category: Unhealthy
Health Alert: ⚠ Unhealthy! Wear a mask outside.
```

### 4️⃣ Launch the Dashboard

Start the interactive Streamlit dashboard:

```bash
streamlit run milestone4_dashboard/app.py
```

The dashboard will open at `http://localhost:8501` and provides:

- 🏙️ **City Selection** — Choose from available cities via the sidebar
- 📊 **Today's Overview** — Current AQI, category, and daily change
- ⚠️ **Health Alerts** — Contextual warnings & recommendations
- 📅 **7-Day Forecast** — Pollutant-level forecast table

---

## 🧠 Model Details

| Parameter | Value |
|-----------|-------|
| **Algorithm** | Random Forest Regressor |
| **Estimators** | 100 trees |
| **Test Split** | 80/20 train-test split |
| **Random State** | 42 |
| **Input Features** | All numeric pollutant columns (PM2.5, PM10, NO, NO2, NOx, NH3, CO, SO2, O3, Benzene, Toluene, Xylene) |
| **Target** | AQI |
| **Serialization** | Joblib (`.pkl`) |

### AQI Classification Scale

| AQI Range | Category | Alert |
|-----------|----------|-------|
| 0 – 50 | 🟢 Good | Air quality is safe |
| 51 – 100 | 🟡 Moderate | Sensitive groups be careful |
| 101 – 200 | 🟠 Unhealthy | Wear a mask outside |
| 201 – 300 | 🔴 Very Unhealthy | Avoid outdoor activities |
| 300+ | ☠️ Hazardous | Stay indoors |

---

## 🛠️ Tech Stack

| Category | Technologies |
|----------|-------------|
| **Language** | Python 3.8+ |
| **ML Framework** | scikit-learn |
| **Data Processing** | Pandas, NumPy |
| **Visualization** | Matplotlib, Seaborn |
| **Dashboard** | Streamlit |
| **Model Persistence** | Joblib |

---

## 🏗️ Milestone Roadmap

- [x] **Milestone 1** — Data Preprocessing & Feature Engineering
- [x] **Milestone 2** — AQI Forecasting Model (Random Forest)
- [x] **Milestone 3** — AQI Analysis, Categorization & Alert System
- [x] **Milestone 4** — Interactive Streamlit Dashboard

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

---

## 📜 License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

---

## 👨‍💻 Developer

**Satyajit Sonkar**

<p>
  <a href="https://github.com/satyajitsonkar96"><img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"></a>
</p>

---

<p align="center">
  Made with ❤️ for cleaner air
</p>
