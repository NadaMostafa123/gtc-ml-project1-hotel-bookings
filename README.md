# 🏨 Hotel Booking Data Cleaning & Preprocessing  

## 📌 Project Overview    
The goal is to **clean and preprocess** the raw `hotel_bookings.csv` dataset so it becomes ready for a future machine learning model that predicts **booking cancellations**.  

---

## 🔎 What I Did (Step by Step)  

### 1️⃣ Exploratory Data Analysis (EDA)  
- Checked dataset shape, column types, and statistics.  
- Identified **missing values** and visualized them.  
- Detected **outliers** in key columns (`adr`, `lead_time`) using IQR and boxplots.  
- Found **31,994 duplicate rows**.  

### 2️⃣ Data Cleaning  
- **Missing values** fixed:  
  - `company` & `agent` → replaced with 0.  
  - `country` → filled with mode.  
  - `children` → filled with median.  
- **Duplicates** removed.  
- **Outliers** handled:  
  - `adr` values > 1000 capped at 1000.  
  - `lead_time` values > 365 capped at 365.  
- Converted date columns to correct `datetime` format.  

### 3️⃣ Feature Engineering  
- Created new features:  
  - `total_guests = adults + children + babies`  
  - `total_nights = stays_in_weekend_nights + stays_in_week_nights`  
  - `is_family` → Yes/No flag depending on children/babies.  

### 4️⃣ Encoding  
- One-Hot Encoding applied to **low-cardinality categorical columns** (`meal`, `market_segment`, `deposit_type`, etc.).  
- Frequency Encoding used for **high-cardinality column** (`country`).  

### 5️⃣ Final Preparation  
- Dropped **leakage columns**: `reservation_status` & `reservation_status_date`.  
- Split dataset into **train (80%)** and **test (20%)** using `random_state=42`.  

---

## ✅ Key Findings  
- Large number of duplicates (31k+).  
- Outliers in `adr` and `lead_time`.  
- Missing values mainly in `company`, `agent`, `country`, and `children`.  
- After cleaning, the dataset is **ready for ML modeling**.  
 
