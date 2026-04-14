# 🚇 OnTimeLondon AI

A multi-agent transport prediction system that predicts London transport delays in real-time and provides personalized route recommendations.

> **🚧 Note:** The multi-agent backend pipeline is fully complete. Dissertation research & writing and React Native mobile app are currently in progress.

<img width="264" height="250" alt="1 1 logo" src="https://github.com/user-attachments/assets/d1e3d940-0abb-41c2-a5e6-df91aa9f8476" />


🔗 [Portfolio](https://ramya-portfolio-ten.vercel.app) | [LinkedIn](https://linkedin.com/in/ramya-sri-518a85204)

---

## 🚧 Project Status

| Component | Status |
|-----------|--------|
| Multi-Agent Backend Pipeline | ✅ Complete |
| LSTM Prediction Model (~97% accuracy) | ✅ Complete |
| n8n Workflow Orchestration | ✅ Complete |
| Dissertation Research & Writing | 🔄 In Progress |
| React Native Mobile App | 🔄 In Progress |

---

## 🎯 Problem Statement

London commuters face daily uncertainty — sudden delays with no early warning and no clear alternatives. Existing apps show delays *after* they happen, but don't *predict* them or tell you what to do.

**OnTimeLondon AI solves this by:**
- Predicting delays *before* they happen
- Detecting anomalies in real-time
- Finding the fastest alternative route
- Personalizing recommendations based on your travel history
- Delivering friendly, actionable travel messages

---

## 🏗️ Architecture

The system uses a **5-agent pipeline** orchestrated through n8n workflows:

<img width="562" height="1007" alt="image" src="https://github.com/user-attachments/assets/5d5af1b3-a4cf-4766-82ea-3145a1ce9156" />

---

## 🤖 The 5 Agents

| Agent | File | Purpose | Technology |
|-------|------|---------|------------|
| **Agent 1** | `Real-Time Monitor Agent-1.json` | Z-Score Anomaly Detection | Statistical analysis on live TfL data |
| **Agent 2** | `Delay Predictor Agent-2.json` | Delay Prediction | LSTM Neural Network (~97% accuracy) |
| **Agent 3** | `Optimizer workflow Agent-3.json` | Route Optimization | Dijkstra's Algorithm (471 stations, 1,154 connections) |
| **Agent 4** | `Learning Agent-4.json` | Personalization | Epsilon-Greedy RL + Collaborative Filtering |
| **Agent 5** | `Communication Agent-5.json` | Message Generation | Llama LLM via OpenRouter |

**Full Pipeline:** `OnTimeLondon AI - Full Pipeline.json` — Complete orchestrated workflow

---

## 📊 LSTM Model Details

**Architecture:** 128 → 64 → 32 neurons (3 LSTM layers)

**Features used (6):**
- `line_encoded` — Transport line
- `hour` — Hour of day
- `day_of_week` — Day of week
- `is_weekend` — Weekend flag
- `is_rush_hour` — Rush hour flag
- `status_severity` — Current severity level

**Performance:** ~97% accuracy on TfL historical data

---

## 📁 Repository Structure

```
OnTimeLondon-AI/
│
├── README.md
│
├── agents/                                    # n8n workflow JSON files
│   ├── OnTimeLondon AI - Full Pipeline.json  # Complete 5-agent workflow
│   ├── Real-Time Monitor Agent-1.json        # Z-Score anomaly detection
│   ├── Delay Predictor Agent-2.json          # LSTM prediction calls
│   ├── Optimizer workflow Agent-3.json       # Dijkstra's routing
│   ├── Learning Agent-4.json                 # RL + Collaborative Filtering
│   └── Communication Agent-5.json            # Llama LLM responses
│
├── data-collectors/                           # Data polling workflows
│   ├── TfL Live Status Poller (2).json       # TfL API (every 60s)
│   ├── Weather Data Poller (2).json          # Weather data (every 15min)
│   ├── Events Collector (2).json             # Ticketmaster (every 12hrs)
│   └── Social Media Monitor (1).json         # Reddit sentiment (every 15min)
│
├── data/                                      # Database setup workflows
│   ├── Data Setup - Stations (1).json        # 471 TfL stations
│   └── Data Setup - Connections (1).json     # 1,154 station connections
│
├── model/                                     # LSTM model files
│   ├── OnTimeLondon_LSTM_Model.ipynb         # Training notebook
│   ├── lstm_delay_predictor.h5               # Trained model
│   ├── scaler.pkl                            # Feature scaler
│   └── line_mapping.pkl                      # Line encoding
│
└── screenshots/                               # Demo screenshots
    ├── model-accuracy.png                    # 97% accuracy result
    └── agent-response.png                    # AI travel message
```

---

## 🗃️ Database Tables (Supabase)

| Table | Records | Description |
|-------|---------|-------------|
| `stations` | 471 | All TfL stations with IDs, names, coordinates |
| `connections` | 1,154 | Station-to-station connections for routing |
| `delay_history` | - | Historical delay data for model training |
| `user_preferences` | - | User travel preferences for personalization |
| `predictions` | - | Stored prediction results |

---

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| Workflow Orchestration | n8n (Docker) |
| ML Framework | TensorFlow / Keras |
| Backend Database | Supabase (PostgreSQL) |
| API Deployment | Flask |
| LLM Integration | Llama 3.3 70B via OpenRouter |
| Data Source | TfL Unified API |
| Hosting | Local (Docker) / Oracle Cloud (planned) |

---

## 📸 Screenshots

### LSTM Model Accuracy (~97%)
<img width="762" height="782" alt="model-accuracy" src="https://github.com/user-attachments/assets/6aec99f9-3998-4afd-bed1-15b22b64876e" />

### AI Agent Response — Personalized Travel Message
<img width="1790" height="917" alt="agent-response" src="https://github.com/user-attachments/assets/091b52ac-9125-407e-984a-677a6be18832" />

---

## 🚀 How to Run

**Prerequisites:**
- Docker installed
- n8n running locally (`localhost:5678`)
- Supabase project set up
- TfL API key

**Steps:**

1. Clone the repository
```bash
git clone https://github.com/MRamya-sri/OnTimeLondon-AI.git
cd OnTimeLondon-AI
```

2. Import n8n workflows
   - Open n8n (`localhost:5678`)
   - Import `OnTimeLondon AI - Full Pipeline.json` from `agents/`
   - Import all workflows from `data-collectors/`
   - Import data setup workflows from `data/`

3. Run the Flask API for LSTM model
```bash
cd model
python flask_api.py
```

4. Activate the workflows in n8n

---

## 📈 Results & Impact

- **~97% prediction accuracy** on delay classification
- **471 TfL stations** mapped with **1,154 connections**
- **5 AI agents** working seamlessly in a pipeline
- **Real-time personalized** travel recommendations
- **Sub-second response time** for route calculations

---

## 🔮 What's Next

- 📝 **Dissertation writing** — Currently documenting research methodology and findings
- 📱 **React Native mobile app** — Building user-facing app for commuters
- ☁️ **Cloud deployment** — Deploy to Oracle Cloud Free Tier for 24/7 availability
- 🔔 **Push notifications** — Real-time alerts for predicted delays
- 🚌 **More transport modes** — Integrate buses, DLR, and National Rail

---

## 📄 License

This project was built as part of my MSc Artificial Intelligence dissertation at Northumbria University London.

---

## 📬 Contact

**Ramya Sri Muthuluri**  
📧 ramyasrimuthuluri@gmail.com  
🔗 [LinkedIn](https://linkedin.com/in/ramya-sri-518a85204)  
🌐 [Portfolio](https://ramya-portfolio.vercel.app)
