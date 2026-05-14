# ✈️ Flight Fare Prediction — Machine Learning (GRU Neural Network)

An end-to-end machine learning project that predicts flight ticket prices using the full data science lifecycle — from data cleaning and feature engineering to a GRU neural network with cross-validation.

---

## 📁 Folder Structure

```
flight-fare-prediction/
│
├── notebooks/
│   └── Flight-Fare-Prediction.ipynb     # Full notebook: EDA, preprocessing, modeling
│
├── dataset/
│   └── Data_Train.xlsx                  # Training dataset (flight records)
│
├── models/
│   └── flight_fare_model.h5             # Saved trained GRU model
│
├── requirements.txt                     # Python dependencies
└── README.md
```

---

## 📌 Project Overview

This project follows the complete data science lifecycle to predict flight fares:

1. **Data Collection** — Excel dataset with flight booking records
2. **Data Cleaning** — Handle missing values, fix data types
3. **Data Preprocessing** — Extract datetime features from `Date_of_Journey`, `Dep_Time`, `Arrival_Time`
4. **EDA** — Visualize departure time patterns, stop distributions, airline pricing
5. **Feature Engineering** — Extract journey day/month, departure hour/minute, duration hours/mins, encode stops
6. **Model Building** — GRU (Gated Recurrent Unit) Neural Network
7. **Hypertuning** — 5-Fold Cross-Validation with Early Stopping
8. **Model Export** — Saved as `.h5` for deployment

---

## 🛠️ Tech Stack

| Library | Purpose |
|---------|---------|
| Python 3.x | Core language |
| Pandas & NumPy | Data manipulation |
| Matplotlib & Seaborn | Visualization |
| Scikit-learn | Preprocessing, pipelines, KFold CV |
| TensorFlow / Keras | GRU Neural Network |
| OpenPyXL | Reading Excel dataset |

---

## 📊 Dataset Features

| Feature | Description |
|---------|-------------|
| Airline | Name of the airline |
| Date_of_Journey | Travel date |
| Source | Departure city |
| Destination | Arrival city |
| Route | Flight path |
| Dep_Time | Departure time |
| Arrival_Time | Arrival time |
| Duration | Total flight duration |
| Total_Stops | Number of stops (non-stop to 4 stops) |
| Additional_Info | Extra flight info |
| **Price** | **Target variable — ticket fare** |

---

## 🤖 Model Architecture — GRU Neural Network

```
Input → GRU(64, return_sequences=True) → Dropout(0.3)
      → GRU(32, return_sequences=False) → Dropout(0.3)
      → Dense(64, relu, L2) → Dense(32, relu, L2) → Dense(1)

Optimizer: Adam (lr=0.001)
Loss: Mean Squared Error
Validation: 5-Fold Cross-Validation + EarlyStopping (patience=10)
```

---

## ⚙️ Feature Engineering Highlights

- Extracted `Journey_day`, `Journey_month` from `Date_of_Journey`
- Extracted `Dep_Time_hour`, `Dep_Time_minute` from departure time
- Extracted `Duration_hours`, `Duration_mins` from duration string
- Encoded `Total_Stops`: non-stop → 0, 1 stop → 1, ..., 4 stops → 4
- One-Hot Encoded: `Airline`, `Source`, `Destination`, `Route`, `Additional_Info`
- Scaled features using `StandardScaler`

---

## 🚀 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/flight-fare-prediction.git
   cd flight-fare-prediction
   ```

2. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

3. Open the notebook:
   ```bash
   jupyter notebook notebooks/Flight-Fare-Prediction.ipynb
   ```

4. Place `Data_Train.xlsx` inside the `dataset/` folder and update the file path in the notebook.

---

## 📦 requirements.txt

```
pandas
numpy
matplotlib
seaborn
scikit-learn
tensorflow
openpyxl
jupyter
```

---

## 📄 License

This project is for educational and portfolio purposes.
