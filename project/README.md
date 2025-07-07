
# Real-Time Smart Parking Dashboard

This project implements a real-time parking pricing and rerouting dashboard using **Pathway** (for stream processing) and **Panel + Bokeh** (for visualization). It dynamically adjusts parking prices and flags rerouting decisions based on occupancy, queue lengths, traffic conditions, and more.

---

## 🔧 Features

- Real-time data streaming from CSV files using **Pathway**
- Dynamic pricing based on demand and nearby competition
- Reroute flagging if occupancy exceeds a critical threshold
- Individual dashboards for 14 parking lots with time-series plots
- Interactive visualization using **Panel** and **Bokeh**

---

## 🗂️ Project Structure

```
.
├── dataset.csv                     # Raw dataset with parking info
├── parking/parking_stream.csv     # Preprocessed stream-ready file
├── stream_preprocessing.py        # Data transformation and CSV export
├── real_time_dashboard.py         # Stream logic, pricing model, dashboard UI
├── run_pathway.py                 # Runs the Pathway engine
├── README.md                      # Project documentation
```

---

## 🛠️ Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/smart-parking-dashboard.git
cd smart-parking-dashboard
```

### 2. Install Required Packages

You need Python 3.8+ and the following packages:

```bash
pip install pandas numpy pathway panel bokeh
```

### 3. Prepare the Stream Data

Run the preprocessing script to generate the streamable CSV:

```bash
python stream_preprocessing.py
```

This will create a file at: `./parking/parking_stream.csv`

---

## ▶️ Running the Dashboard

### 1. Start Pathway Engine

```bash
python run_pathway.py
```

This will process the stream in real-time using the Pathway runtime.

### 2. Launch the Dashboard

Open a new terminal and run:

```bash
panel serve real_time_dashboard.py --autoreload
```

Then visit: `http://localhost:5006/real_time_dashboard`

---

## 📈 Dashboard Preview

Each lot has its own section with:

- **Price Plot** — Final price over time
- **Occupancy vs Capacity Plot** — Real-time load status
- **Reroute Flag Plot** — Whether users should be redirected

---

## 📘 Key Logic

- **Dynamic Pricing:** Combines occupancy, queue, traffic, special days, and vehicle types with competitive logic (based on nearby lots).
- **Rerouting Trigger:** A reroute flag is activated when occupancy exceeds 95% of capacity.
- **Distance Calculation:** Uses the Haversine formula for proximity between parking lots.

---

## 📍 Lot IDs Covered

The dashboard supports 14 parking lots, including:

- BHMBCCMKT01
- BHMBCCTHL01
- BHMEURBRD01
- Broad Street
- Others-CCCPS8  
*(and more...)*

---

## 📤 Future Improvements

- Connect to real-time sensors or APIs
- Add authentication for lot managers
- Export analytics and price logs
- Use WebSocket for truly live dashboards

---

## 📄 License

This project is open-source and available under the MIT License.
